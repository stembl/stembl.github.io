---
layout: post
published: true
title: Vibration Analysis For Electronic Equipment
category: notes
tags: [book,notes,vibration]
---


`Steinberg, Dave. Vibration Analysis for Electronic Equipment, 2nd ed., 1988`

 Steinberg's Vibration Analysis for Electric Equipment was recommended to me as a good text for improving my understanding of random vibration testing.  This book turned out to be full of great information from the design of electronic chassis to fatigue analysis. Steinberg covers a large range of topics and starts with a simple model to explain each.  Often, he will extend this analysis into a slightly more complex model, but with assumptions that simplify the model. I appreciate the detail with which the simple models were derived and would have liked to have seen similar detail in the second order systems.

I've taken notes on the areas related to my vibration work posted them to [GitHub](https://github.com/stembl/stembl.github.io/blob/master/public/ipy/Steinberg_1988/Steinberg_1988.ipynb).  Below is an excerpt of some of the interesting results.

### 2.9, Forced Vibrations with Viscous Damping

* Solving the response of a MSD system given a harmonic force acting on the mass.
    * Can I find a similar solution to this as a function of a harmonic deflection at the base of the spring and damper?
    * This derivation is not detailed, Eqn 2.43



```python
# Plotting Figure 2.17 using Eqn. 2.48.

import numpy as np
import matplotlib.pyplot as plt
from math import sqrt
from sympy import zeros

R_c = np.arange(0,1,.1)        # R_c = c/c_c. This is the ratio of the damping to the critical damping
R_Omega = np.arange(0,10,.01)   # R_Omega = Omega / Omega_n.  This is the ratio of the input frequency to the natural frequency.

# Initialize the transmissibility Q 
Q = zeros(len(R_c), len(R_Omega))

# Equation 2.48
def Q_Rc_RO(R_Omega, R_c):
    Q = sqrt((1 + (2 * R_Omega * R_c)**2)/((1 - R_Omega**2)**2 + (2 * R_Omega * R_c)**2))
    return(Q)

for i in range(len(R_c)):
    for j in range(len(R_Omega)):
        Q[i,j] = Q_Rc_RO(R_Omega[j], R_c[i])
        
# Plot Results
plt.semilogy(R_Omega,Q.T)
plt.xlabel('$R_\Omega = \\frac{Forcing Frequency}{Natural Frequency} = \\frac{f}{f_n}$')
plt.ylabel('$Q = \\frac{{Maximum Output Force}}{Maximum Input Force}$')
plt.axis([0,10,0.1,10])
plt.plot([0,10],[1,1],'k')
plt.show()
        
```

    C:\Anaconda3\lib\site-packages\ipykernel\__main__.py:16: RuntimeWarning: divide by zero encountered in double_scalars
    


![png](/public/ipy/Steinberg_1988/output_2_1.png)


Damping occurs to the right of the amplification peak at \[ \R_{Omega} = \sqrt(2) \].

## Chapter 8, Understanding Random Vibration

* "If two major structural resonances occur close to one another, they may produce severe dynamic coupling effects that can produce rapid fatigue failures."
* For a cyclically alternating electric current, RMS is equal to the value of the direct current that would produce the same average power dissipation in a resistive load.
* Failure conditions
    1. High acceleration levels
    2. High stress levels
    3. Large displacement amplitudes
    4. Electrical signals out of tolerance - N.A.
* sigma is often the limit used because it captures 99.7% of the accelerations and most labs have a 3*sigma limit on their equipment.
* In the math library, natural log is called with (`log`) and log base 10 with (`log10`)
* Multiple degree of freedom systems (8.29). \[ G_{out} = \sqrt(\sum(P_i \Delta f_i Q_i^2)) \]
* From: Crandall, Random Vibration, 1958.  \[ P_{out} = Q^2 P \].  Book available [online](https://babel.hathitrust.org/cgi/pt?id=mdp.39015060919126;view=1up;seq=17).





```python
## Calculating the Grms of a shaped random vibration input curve.
# Sec. 8.8, Eqns. 8.4 - 8.6.

def grms (freq, PSD):
    """Returns the Grms value for a shaped random vibration input curve.
    Input the frequency and PSD values as a list in the form grms(freq, PSD).
    The frequency and PSD list must have the same number of elements."""
    
    from math import log10, log
    
    A = 0
    
    if len(freq)!=len(PSD):
        print("Error: The number of elements in the Frequency and PSD lists do not match.")
    
    else:
        for i in range(1,len(freq)):
            
            # Calculate the slope
            dB = 10 * log10(PSD[i]/PSD[i-1])           # dB
            OCT = log10(freq[i]/freq[i-1])/log10(2)    # Octave
            S = dB/OCT                                 # Slope
            
            # Calculate the area in units of [G^2]
            if S == 0:
                A = A + PSD[i] * (freq[i] - freq[i-1])
            elif S == -3:
                A = A + -freq[i] * PSD[i] * log(freq[i-1] / freq[i])
            else:
                A = A + (3 * PSD[i]/(3 + S)) * (freq[i] - (freq[i-1]/freq[i])**(S/3) * freq[i-1])
            
            # Calculate the Grms [G]
            grms = A**(0.5)

    return(grms)

```


```python
# Find the GRMS of the ASTM common carrier profile.  

Common_Carrier = [[1, 4, 100, 200], [.0001, .01, .01, .001]]

grms(Common_Carrier[0], Common_Carrier[1])
```




    1.1469379669303117




```python
## Response to a random vibration, from Section 8.
# Valid for a single resonance with a Q > 10.


def resp_psd_Q (P_in, Q, f_n, g=9800):
    """At a natural frequency, calculates the Grms and Zrms (relative motion) of the point given the transmissibility,
    and PSD.""" 
    from math import pi
    
    Grms = ((pi/2)*P_in*f_n*Q)**0.5    # RMS acceleration, Eqn. 8.61
    
    #g = 9.8*1000                       # Gravity, [mm/s^2]
    
    Zrms = Y_G_fn(Grms, f_n, g)      # Relative motion, Eqn. 8.62.  Ref. Eqn. 2.30
    
    return(Grms, Zrms)
```


```python
resp_psd_Q (0.00072, 3.146, 30.4)
```




    (0.3288836909042307, 0.08834083693899289)



## Chapter 9, Designing for Shock Environments
* Eqn. 9.40 - Damping ratio ~ R_c = C/C_c = 1/(2 Q)
    * Q = 1/(2 R_c)
* Figure 9.17 illustrates the difficulty in designing for both shock and vibration.  Shock isolation occurs to the left of the amplification peak while vibration isolation occurs on the right. Equation for calculating amplification missing for graphs in Chp. 9. 
* Velocity shocks, used when modeling drop tests.
    * Assuming single DOF M-S-D, the dork done on the spring is equal to the kinetic energy of the mass. (1/2) K Y^2 = (1/2) M V^2
    * Max acceleration: G_max = (a/g) = (V/g) sqrt(K/M) = (V/g) Omega, or G = (Delta V Omega)/g.
* Can not recreate Fig. 9.21 without a relationship between the amplification and the frequency ratio.
    * Impact damping only occurs at R = frequency_response/frequency_source <= 0.5
    * Danger area from 0.5 <= R <= 2
    * This assumes an damping ratio of R_c = 0.1 and Q = 5
    * These equations do not relate to velocity shocks in which the forcing frequency is determined by the natural frequency.  
* For velocity shocks max expected G can be calculated or if the response is known, the natural frequency should fall out as function of the response G and the height.


```python
# Calculate the velocity before impact during drop tests
def vf_H (H, g=9800):
    '''Solves for the velocity before impact of an object dropped from a height H.
    Assumes a standard gravity of 9800 mm/s. Input the gravity in the same unit system as the height.'''
    
    v = (2*g*H)**0.5
    
    return v

# For a 2" drop
vf = vf_H(2*2.54)
print(vf)
```

    315.54397474837003
    


```python
# Find G_max due to a drop test

def gmax_drop (H, fn, g=9800):
    '''Find the maximum acceleration due to a velocity shock given the drop height (H), 
    natural frequency (fn), and gravity (g). The gravity should be input in the same
    unit system as the velocity.  Defaults to mm/s^2
    
    Returns max acceleration in Gs (unitless)'''
    
    from math import pi
    
    v = (2*g*H)**0.5
    g_max = v*(2*pi*fn)/g
    
    return(g_max)

def fn_drop (H, g_max, g=9800):
    '''Find the natural frequency of a system based on a  shock
    from a given the height (H), maximum acceleration response (g_max), 
    and gravity (g). The gravity should be input in the same
    unit system as the velocity.  Defaults to mm/s^2
    
    Returns natural freuqncy f_n [Hz]'''
    
    from math import pi
    
    v = (2*g*H)**0.5
    fn = g_max*g/(v*2*pi)
    
    return(fn)

H = 2       #[in]
H = H*25.4  #[mm]

g_max = gmax_drop(H, 14)
fn = fn_drop(H, 10)

print('Max G: ', g_max)
print('Natural Frequency: ', fn)
```

    Max G:  8.95656991107948
    Natural Frequency:  15.630983891145293
    
