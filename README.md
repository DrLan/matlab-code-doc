#3D Resistor Network Code Documentation 

## 1. Modeling Approach
### 1.1 	Fundamental Conduction Mechanism
Electrical conductivity in carbon fiber reinforced composites (CFRP) is highly anisotropic with out-of-plane resistance several orders higher compared to the in-plane properties.  Carbon fibers provide the continuous current flow pathways in fiber directions (x-direction) while the high resistivity of the matrix lowers the effective conductivity of the CFRP in transverse direction (y- and z-direction) (Figure 2.1).  This research addresses the lower tow or single prepreg layer conductivity in transverse direction.
Nevertheless, in a real composite structure individual conducting fibers and tows will be in contact providing current flow paths across the interface improving the electrical out-of-plane conductivity. Along the fiber direction, the conductivity of the composite depends upon the carbon fiber conductivity and the fiber volume fraction. In the transverse to the fiber direction, the electrical conductivity of the unidirectional (UD) preform depends upon the random fiber-to-fiber contact. Current can cross at contact points and build a conducting path. So the distance between contact points is critical to overall through thickness conductivity.
The idea of contact points between fibers is well adopted by other researchers in the study of composites. Gutowski applied this approach to develop models to study the load transfer in composite materials. Using similar assumptions, our model implementation is looking at the electrical properties of composites. It considers not only contact to contact distance, but also contact resistance between two neighboring fibers. In most cases, contact resistance can be insignificant for unsized fibers, while large for sized fibers. So the resistivity of composite depends on single fiber resistivity and the microstructure of the composite
Figure. 2.2 illustrates the conduction path associated with through-thickness conduction behavior. Conduction path transverse to the fiber direction (out-of-plane and in-plane transverse) is due to fiber waviness creating fiber to fiber contact points of neighboring fibers. The current path is along individual fibers before crossing to the next parallel fiber and repeats until the opposite surface is reached. Since the resistivity of matrix is much higher (1015~1020 times higher) than of the carbon fibers, it can be regarded as insulators. The conduction mechanism of unidirectional CFRP panels is then very similar to that of unidirectional dry carbon fiber tows (assuming no resin rich layers at the layer interface). 
### 1.2 Resistor Network Model v.s. Finite Element Model



## 2. Overview of Model Implementation
### 2.1 2D Structure
### 2.1 Lamina Model

### 2.2 Laminate Model

### 

## 3. Classes Defined
### 3.1 Objected Oriented Design
### 3.2 Main Classes Defined
#### 3.2.1 Fiber
#### 3.2.2 Lamina
#### 3.2.3 Laminate
#### 3.2.4 Simulation
#### 3.3

## 4. Graphical User Interface (GUI)
### 4.1 Quick Start

### 4.2 Behind the Frames



### 4.3

###


work flow:
1. generate 2D cross section area
2. generate SPICE netlist for 3D structure
3. compute using LTSPICE
4. return results


