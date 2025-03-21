---
layout: default
title: "Portfolio"
permalink: portfolio/
permalink: portfolio
permalink: portfolio.html
---

# Portfolio
Updated: 06/29/2023

---

## Index

---
1. [Introduction](portfolio#introduction)
1. [Design](portfolio#design)
1. [Modeling and Automation](portfolio#modeling-and-automation)
1. [3D Printed](portfolio#3d-printed)
1. [Patents List](portfolio#patents-list)
1. [Publications and Reports](portfolio#publications-and-reports)
1. [Other Interesting Projects](portfolio#other-interesting-projects)

---

## Introduction

---

Innovative and passionate Design Engineer with over 10 years of experience in mechanical design, analysis, and modeling. Proven ability to drive cost-effective, cutting-edge solutions in high-performance industries, including energy storage, data centers, and precision engineering. Skilled at leading cross-functional teams to develop industry-leading hardware solutions.

---

## Design

---

These design related projects are listed in chronological order are some mechanical designs which I've led or contributed to significantly.

### Tesla 4680 In-House Mechanical Design
As the energy density of battery cells increases, so do the mechanical forces that the structure must withstand over time. I was tasked with leading a team to address and mitigate mechanical deformation in next-generation 4680 cells, specifically under higher energy densities. The challenge was to maintain structural integrity while optimizing for cost, weight, and performance.

I led a cross-functional team to develop a novel approach for the 4680 cells, resulting in an 80% reduction in cost and a 70% reduction in weight compared to previous solutions. These improvements have the potential to save $100M annually, making a significant impact on both the economics of production and the scalability of manufacturing.

On a technical level, I developed advanced tools that allowed for fundamental evaluations of the system, enabling parametric sweeps to optimize both material properties and geometric designs. Additionally, I invented several novel concepts for installing mechanical structures within the cell, all of which led to substantial improvements over existing solutions. This work contributed not only to the performance and durability of the 4680 cell but also to its overall manufacturability and cost efficiency.

![Tesla 4680](public/img/tesla_4680.jpg)

### Novel Power Electronics Meachnical and Thermal Design
I was the lead for thermal design and simulation of components on a new Tesla product. This included initial validation of heat transfer through the heatsink, simulation and refinement of novel magnetics components, and ensuring an adequate thermal buffer was maintained throughout the design process. 

I owned the mechanical and thermal design of a large planar magnetic. This component requried months of iteration to optimize the shape, efficiency, thermal performance, and manufacturability. I was responsible for working with the supplier to improve their manufacturing process and tolerances.


![Planar Tolerances](public/img/tols_feature.png)

![Planar Yield](public/img/tol_yield.png)

### RF Secure Rack
I led the mechanical design of the Dell RF shielded rack designed to allow our customers to deploy thousands of IOT devices in a small footprint for application development. Developed with  a smaller footprint and better performance when compared with existing solutions we delivered the only product that met or exceeded all of our customer's requirements.

Links:
* [Dell Blog, Dell EMC Provides Radio Frequency Shielding Technology for Mobile App Development & Testing](https://www.delltechnologies.com/en-us/blog/dell-emc-radio-frequency-shielding-mobile-app-development/)
* [YouTube, Dell EMC RF Secure Rack Enclosure](https://www.youtube.com/watch?v=Cs7S3C93k-E)

On this project we were asked to build an IT enclosure with an EMR attenuation of 90 dB while maintaining a light weight, low cost, and the ability to ship loaded to a customer.  The conflicting design requirements included minimizing structure, maximizing transportable weighted capacity, minimizing airflow impedance, minimizing EMI, and maintaining standard serviceability.  This problem gave me the opportunity to develop parametric EMI models for vented surfaces, FEA models to simulate harmonics and random vibration, a tolerance analysis, required jigging, and production test and inspection plans.  The final solution that addressed all these issues required novel developments that resulted in a few patent applications.

This project lasted a year and a half from customer request through first purchase.  During that time I greatly expanded my knowledge of EMI concerns, products, testing, sealing techniques, and modeling. I also advanced my research into structural vibration and impact modeling.

![RF Secure Rack](public/img/federer2.PNG)

![RF Secure Rack](public/img/federer.PNG)


### Transportation Tote
I was the shock and vibration SME on the Transportation Tote, a solution for large quantity delivers with a minimal ecological footprint. The Transportation Tote needed to meet all of the damping requirements of existing packaging, last for years without degradation, and not break the bank to manufacture.

Links:
* [Dell Blog, New Pilot Program Eliminates Packaging for Large Scale Server Orders](https://www.delltechnologies.com/en-us/blog/new-pilot-program-eliminates-packaging-large-scale-server-orders/)
* [YouTube, Transportation Tote: Good for the Environment, But Not the Fort](https://www.youtube.com/watch?v=avTVxay0PHg)

![Transportation Tote](public/img/tote.JPG)

![Transportation Tote FEA](public/img/tote2.PNG)

### Dell DSS 9000
The DSS 9000 is a scalable rack infrastructure aimed at the largest cloud companies.  In deployments of this rack level solution I provided analysis for shock and vibration, tolerances, manufacturability, transportation, and integration.  The solution required maintaining +/- 1.6 mm spacing across the internal width  from the bottom to top of the rack.  This was especially challenging given the bolted together, multi-piece, sheet metal structure.  The power bus bar also proved an interesting challenge in ensuring it would maintain the proper contact force after transportation when fully loaded.

![DSS 9000](public/img/dss9000-2.JPG)

![Surface Roughness](public/img/busbar2.PNG)


### Dell DSS 7000

The DSS7000 is a very dense storage solution with 100 hard drives in 5U of space.  On this product I participated in the architectural concepts, shock an vibration analysis, and integration and serviceability.

![DSS 7000](public/img/dss7000.PNG)

### Rack Hardware

Our group at Dell specialized in shipping fully loaded configurations to the largest cloud companies.  This has led to the requirement of many custom brackets and other hardware.  Some of the more interesting solutions included a tip bracket designed to install in 30 seconds, fit within 50 mm, and withstand a 4000 lb. rack tipping 10 degrees.  Another was the development of a bracket to eliminate the need for a crate during transportation of our DSS 9000 racks.

![Tip Bracket](public/img/tip.PNG)

![U Bracket](public/img/ubracket.PNG)

![U Bracket Detail](public/img/ubracket2.PNG)

### EIA Flange Jigs

As mentioned above, IT racks need to maintain a very tight tolerance across the internal width.  This ensures the IT equipment may both be installed and not collapse.  Some IT equipment rely on rails with ledges only a few millimeters long.  To ensure our racks and our partners racks met this requirement I designed a jig that could be easily built, light weight, robust, and ensure the racks were within tolerance.

![EIA Flange Jig](public/img/jig.PNG)

### Modular Ramp

One of the options we offered was white glove delivery in which we would unload the rack, roll it into the DC and install it.  Unloading fully integrated racks at the customer site is a tricky task as some solutions weighed north of 4500 lbs.  Safely removing the racks from the shock pallet required a ramp that could be installed consistently, adjust for an uneven floor, survive a harsh environment, and be simple enough for a single person to set up.

My design goals for this rack was a modular system with each piece weighing less then 50 lbs, easy to assemble, and capable of withstanding a rolling rack weighing 6000 lbs.  The biggest problems for this solution occur when shipping racks with six casters instead of four.  This leads to a moment of instability and an impact when the rack rotates into place on the ramp.  Following the impact, the next biggest challenge was securing the side panels as the ramp passes through maximum deflection.

![Ramp Test](public/img/ramptest.PNG)

### Cast AL Brackets

In designing a low cost shipping solution I was afforded the opportunity to develop a cast AL bracket that could maintain a rack in position on a shock pallet during the roughest transportation scenarios.  This effort included 3D printed test fits, FEA analysis, and production samples.

![AL Brackets](public/img/longhorn3.PNG)


### Light Weight Sonar

I designed a US submarine sonar system 75% lighter and 90% cheaper than existing solutions.  This is an old solution, but it was a really interesting problem.  I challenged decades of sonar design history and developed a story convincing enough to lead to this systems deployment. This system needed to be easy to install and repair, withstand wave slap and pressure at depth, and be easy to manufacture.

![Sonar](public/img/sub.JPG)

---

## Modeling and Automation

---

### Automated Profilometer Analysis

*** Details after product release ***

### Optimized Thermally Sensitive Component Pitch

For an array of components that are close to their thermal limit I wrote a program to determine the smallest pitch while maintaining adequate cooling. This required determining the heat transfer coefficient of the heat sink as a function of length and the component thermal resistance into the heat sink. 

![Component Location on Heat Sink](public/img/comp_hs_temp.png)

![Component Power vs Heat Sink Pitch](public/img/hs_comp_pwr.png)

### 2-phase Concept Development

I really enjoyed building system models of next generation servers that use two-phase fluid for component cooling. The models required solving for the boiling and condensation performance of a variety of power levels, components, fluids, condenser features, and facility water temperatures. These models were validated against published results and are now being compared with test systems.  These models have been used to validate future concepts and explore the potential design space.  Below is a set of images illustrating a solution as the fluid and component surface coating varies.  After that is an image illustrating the wall temperature of select components as the power increases.

![2-Phase Solutions](public/img/2phase.PNG)

![2-Phase with Varying Comps](public/img/2phase-comps.PNG)

### Rack Level LC Design Space

Dell is ramping up the addition of liquid cooling to its PowerEdge portfolio.  In doing so, we need a method for quickly determining the required liquid components given a desired server, power per rack, and the number of racks in the deployment.  To solve this problem I built a tool in python to solve the thermal-fluid problem.  I then iterated this solution over all of the component variables to identify solutions that would address the immediate customer needs.  This would allow us to prioritize our development resources.  Below is an image of the process followed by a map of solution cost per node as the power per rack and number of racks vary.

![LC Rack Process](public/img/lcrack-process.PNG)

![LC Rack Cost Map](public/img/lcrack.PNG)

### Transportation Analysis
I developed a custom application to efficiently analyze weeks worth of shock and vibration data reducing analysis time 92%. This data is collected to validate Dell shock and vibration testing or to analyze new transportation methods. This system is a key differentiator for Dell when compared to our competition. Below is an image illustrating the process followed by some example results.

![Transportation Process](public/img/trans-process.PNG)

![Transportation Results](public/img/trans-results.PNG)

---

## 3D Printed

---
### Guardian Robot
After printing the Maker Figure my son and I sat down to design our own robot. During our concept generation session it quickly became apparent that my son, who is four, was asking me to design a robot that looked very similar to one from a video game he had seen. With that drawing as a template we built a few prototypes of the body and legs before settling on the parts that have been uploaded. According to my son, "It's perfect, exactly what I wanted."

This design led to a collaboration with Noe from Adafruit leading to a motorized and two material version.

[Thingiverse, Guardian Robot](https://www.thingiverse.com/thing:2359634)

[Thingiverse, Hackable Guardian Robot](https://www.thingiverse.com/thing:2391826)

![Robot](public/img/robot.PNG)

![Robot, Hackable](public/img/robot-hack.PNG)


### NASA Space Fabric

JPL submitted an [article](https://www.jpl.nasa.gov/news/news.php?feature=6816) on a "4-D" printed fabric that could be used to protect objects in space.  I used the images and attempted to create a model as close to the original as possible.  I modified the model so that the reflective surface would be printed last (on top).  This allows the surface to be smoother and more similar to the model.

My segments are not as small as those in the image from NASA.  This is due to the diameter of the linking arms.  In the image, the linking arms are probably close to 1 mm.  At that diameter, my printer can not print the linking arms accurately.

The model is 2 X the size of the NASA segments with a linking arm diameter of 2 mm and top size of 16 x 16 mm.  The pitch between the segments is 10 mm.  This model scales easily if you have a printer with a better resolution.

[Thingiverse, Nasa Space Fabric](https://www.thingiverse.com/thing:2422015)

![Nasa Space Fabric](public/img/nasa.PNG)


### Auxetic Materials

I find auxetic materials fascinating and I am always considering where they may find an interesting application.  One thought was for a flat packable bicycle helment.  The model below was used to explore this concept.

![Auxetic Concept](public/img/auxetic.PNG)

### Growler Tap

Based of the Growler Tap design, I decided to try something similar.  The growler tap pressurized the growler allowing easy dispensing of the beer.  I also added a pressure release valve which allows any air trapped to be removed preserving the beer.

With this print I wanted to build something not possible with traditional techniques.  I built in threads and attempted to make every wall a constant thickness.  This lets you visualize the internal structure from the exterior.

Another goal was to make the parts easily washable, a common complaint with the production units.  To achieve this, I added an o-ring that seals the tube which is inserted into the beer.

![Growler Tap](public/img/tap.PNG)

### Sous Vide Controller

I had all of the parts to create a 20 dollar sous vide controller and I was looking at 10 dollars for an off-the-shelf box.  I used this as an opportunity to try and build a custom enclosure for my device.  My goal with the enclosure was to create a part using a single run that was as dense as possible and looked seam-less.

![Sous Vide Controller](public/img/sousvide.PNG)

### Life Counter

I made this for a friend using [ambrosial's](https://www.thingiverse.com/thing:2094793) divining top as inspiration.

[Thingiverse, Sensei's Divining Top with Scroll Work](https://www.thingiverse.com/thing:2377665)

![Sensei's Divining Top with Scroll Work](public/img/top.PNG)

### Transforming Motorcycle

The model below was built using one of UT's early SLS 3D printers.  The device needed to illustrate a transforming motorcycle using RC car actuators.

![Transforming Motorcycle](public/img/motorcycle.JPG)

---

## Patents List

---

[20 Granted](https://scholar.google.com/citations?user=FnGkK-1_v4MC&hl=en&oi=sra) and 43 Applications. Recent areas include ML, Reliability, Edge, and Liquid Cooling.

### Granted

* Liquid cooling of rack information handling system with a plurality of liquid flow paths that enable continued cooling of liquid cooled nodes when one flow path is disrupted
* Modular information technology (IT) rack and air flow system
* Rack delivery system
* Systems and methods for accelerated temperature acclimation of equipment
* Transportation pallet and method for depalletizing load
* Rack information handling system having modular liquid distribution (MLD) conduits
* Rack anti-tip system
* Generic rack transportation top cap
* Compute device casing that doubles as packaging and shipping container for the compute device
* Shock pallet with adjustable anti-tip mechanism
* Structure and method for securing and transporting equipment racks
* Modular information technology (IT) rack and air flow system
* Rack level air flow baffle providing hot aisle separation from rack-inserted it components
* Factory configurable shock pallet for various integrated rack weights
* High frequency injection for improved false acceptance reduction
* Structure and method for securing and transporting equipment racks
* Tuned mass-spring damper for electronics enclosure
* Systems and methods for reliability control of information handling system
* Thermal ducting for improved cooling in rack domains
* Shock pallet with adjustable anti-tip mechanism
* Rack information handling system having modular liquid distribution (mld) conduits

### Applications

|Quantity|Area of Application|
|:---:|:---|
|1|Liquid Cooling|
|3|2-Phase Cooling|
|1|ML, Reliability|
|12|Corrosion|
|3|Graphite, Thermal|
|1|Heatsink|
|4|RF Secure Rack|
|12|EMI, Servers|
|6|Transportation|

---

## Publications and Reports

---
* [Methodology for the design of hydrophone acoustic baffles and supporting materials](https://docs.google.com/a/embletonblog.com/viewer?a=v&pid=sites&srcid=ZW1ibGV0b25ibG9nLmNvbXxzdGV2ZXxneDo1YzhlYmQ5ZmM4MmE2MTk2)
* [Experimental study of piezoelectret foams as underwater sensors](https://asa.scitation.org/doi/abs/10.1121/1.2934735)
* [Acoustics in Poro-elastic Sediment: History, Review and Current Research](https://docs.google.com/viewer?a=v&pid=sites&srcid=ZW1ibGV0b25ibG9nLmNvbXxzdGV2ZXxneDoyNDdiYTNiMmQzYjBmNjZi)
* [Flexibility-Based Approach to Collaborative Design: Trial Application](https://docs.google.com/viewer?a=v&pid=sites&srcid=ZW1ibGV0b25ibG9nLmNvbXxzdGV2ZXxneDo2YjBiNDYyNDJhNmZhYTMw)
* [Design of Sound Absorption Treatments for a Music Venue](https://docs.google.com/viewer?a=v&pid=sites&srcid=ZW1ibGV0b25ibG9nLmNvbXxzdGV2ZXxneDo0M2M0MGFmODQzZTBiYTcx)

---

## Other Interesting Projects

---

### Twist Light Re-Design
During the Spring 2010 semester I took an Engineering Design Theory and Mathematical Techniques course.  In this course I reverse engineered a Brookstone's twist light and developed multiple parametric and adaptive redesign concepts.  Documentation of this course and the results may be found [here](https://sites.google.com/site/flashlightredesign/).

![Yankee Drive Concept](public/img/yankee.PNG)

### CoolCore Business Concept
CoolCore Technologies was a business concept my group developed in a Lab to Market class.  This concept was built around a non-invasive medical device invented by a professor at UT.  With this business plan, we won second place in the Idea to Product competition at UT.

![Cool Core](public/img/coolcore.JPG)

### Sea Turtle UUV

Before my full time appointment at ARL, I was the mechanical design lead of a UUV designed as a cost effective platform for testing sonar design from our Lake Travis Testing Station.  This project spanned a few years and was the combined effort of mechanical, electrical and computer science engineers.

![Sea Turtle UUV](public/img/seaturtle.JPG)

### UTeach Helmet Impact Measuremnt

While working with UTeach, I developed a test stand to allow high school students to measure the force imparted on a head for a variety of helmets.  Challenges in the project stem from the cost limitations and simple construction techniques and user interface required.  The stand pictured here is the first proof of concept.  The final stand was half the cost, with a head cast from a polymer with a similar density to a human head.

![Head Test](public/img/headtest.JPG)
