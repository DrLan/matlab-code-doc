#3D Resistor Network Code Documentation 

## 1. Modeling Approach
### 1.1 	Fundamental Conduction Mechanism
Electrical conductivity in carbon fiber reinforced composites (CFRP) is highly anisotropic with out-of-plane resistance several orders higher compared to the in-plane properties.  Carbon fibers provide the continuous current flow pathways in fiber directions (x-direction) while the high resistivity of the matrix lowers the effective conductivity of the CFRP in transverse direction (y- and z-direction) (Figure 2.1).  This research addresses the lower tow or single prepreg layer conductivity in transverse direction.
Nevertheless, in a real composite structure individual conducting fibers and tows will be in contact providing current flow paths across the interface improving the electrical out-of-plane conductivity. Along the fiber direction, the conductivity of the composite depends upon the carbon fiber conductivity and the fiber volume fraction. In the transverse to the fiber direction, the electrical conductivity of the unidirectional (UD) preform depends upon the random fiber-to-fiber contact. Current can cross at contact points and build a conducting path. So the distance between contact points is critical to overall through thickness conductivity.
The idea of contact points between fibers is well adopted by other researchers in the study of composites. Gutowski applied this approach to develop models to study the load transfer in composite materials. Using similar assumptions, our model implementation is looking at the electrical properties of composites. It considers not only contact to contact distance, but also contact resistance between two neighboring fibers. In most cases, contact resistance can be insignificant for unsized fibers, while large for sized fibers. So the resistivity of composite depends on single fiber resistivity and the microstructure of the composite
Figure. 2.2 illustrates the conduction path associated with through-thickness conduction behavior. Conduction path transverse to the fiber direction (out-of-plane and in-plane transverse) is due to fiber waviness creating fiber to fiber contact points of neighboring fibers. The current path is along individual fibers before crossing to the next parallel fiber and repeats until the opposite surface is reached. Since the resistivity of matrix is much higher (1015~1020 times higher) than of the carbon fibers, it can be regarded as insulators. The conduction mechanism of unidirectional CFRP panels is then very similar to that of unidirectional dry carbon fiber tows (assuming no resin rich layers at the layer interface). 
### 1.2 Resistor Network Model v.s. Finite Element Model



## 2. Overview of Model Implementation
The CFRP composite is modeled as a DC circuit with an array of electrical resistors reflecting the individual parallel fibers of the unidirectional carbon layer. Contact points of neighboring fibers are distributed along the longitudinal direction of composites while the dielectric properties of the resin effectively insulate the remaining part of the parallel fibers. This assumption makes it possible to represent a CFRP structure as a large resistor network.
A bottom-up modeling method is adopted: 2D structure is firsted constructed, then the 2D structure is extended in fiber length direction to give a 3D microstructure representation of single ply lamina. The model is scaled up to consider laminate by stacking laminas. 
### 2.1 2D Structure
#### 2.1.1	Generate Microstructure from Micrograph
Micrographs of composite structure such as those taken from confocal and SEM can be used as composite microstructure input. An image processing algorithm will first turn the micrograph into binary image and then extract the locations and radius of the circles (in our case the fibers) and store them in a matrix. FiberMatrix is a N by 3 matrix with 3 columns representing x coordinate of fiber center, y coordinate of fiber center, and fiber radius respectively. N is the total number of fibers. Figure .2 (a) provide an example of an SEM image of IM7 fiber system. Figure 6.2(b) represents the extracted fibers from the micrograph. 

~~~matlab
function FiberMatrix = Micrograph(imgname,fiberRadius,xmin_ratio,xmax_ratio,ymin_ratio,ymax_ratio)
%% Input imgname is the file name of micrograph. 
% The micrograph can be in format of jgp, png or bmp. 
% Input fiberRadius is fiber radius. Users can also choose to read part of the image using xmin_ratio,xmax_ratio,ymin_ratio and ymax_ratio parameters. 
%To read full image, set these parameters to 0,1,0,1. 
% Output FiberMatrix is a 3 column matrix, with 3 columns be x,y and radius.
~~~
#### 2.1.2	Generate microstructure from random packing
A random distribution of fibers is used to generate the microstructure. Based on fiber radius, fiber volume fraction and how many fibers are evaluated, a mathematical fiber structure can be defined using Random Sequential Addition (RSA) algorithm. Figure 6.3 shows a randomly generated fiber network.
~~~matlab
function FiberMatrix = Random_Packing(xlen,ylen,vf,fiberRadius)
%% Input xlen,ylen give the dimension of sample; 
% vf is fiber volume fraction, 
% fiberRadius is fiber radius. 
~~~
#### 2.1.3	Generate Microstructure From hexagonal packing
The composite microstructure is often modeled using a hexagonal packing. The structure is defined by the number of row and columns, fiber radius, fiber volume fraction. Fiber distance can be calculated based on given fiber volume fraction and microstructure is then built. Figure 6.4 shows a graphical representation of a perfect square packing of fibers. Here the radius of every fiber is the same while we can also assign a distribution of fiber radius.
~~~matlab
function FiberMatrix=Hex_Packing(nrow,ncolumn,vf,fiberRadius)
%% Input nrow,ncolumn give the number of rows and columns respectively; 
% vf is fiber volume fraction, fiberRadius is fiber radius. 
% Output FiberMatrix is a 3 column matrix, with 3 columns be x,y and radius.
~~~

#### 2.1.4	 Generate Microstructure from square packing
Similar to hexagonal packing, a square packing order can be used generate composite microstructure. Figure 6.5 shows a graphical representation of a perfect square packing of fibers. 
~~~matlab
function FiberMatrix=Square_Packing(nrow,ncolumn,vf,fiberRadius)
%% Input nrow,ncolumn give the number of rows and columns respectively;
% vf is fiber volume fraction, fiberRadius is fiber radius.
% Output FiberMatrix is a 3 column matrix, with 3 columns be x,y and radius.
~~~


### 2.1 Lamina Model


### 2.2 Laminate Model

### 

## 3. Classes Defined
## 3 Object Oriented Model Implementation
At the initial stage of this project, the resistor network model was implemented  as a group of simple functions as presented in section 2. However, as the magnitude and complexity of modeling tasks increase, functions become more complex and difficult to manage. This is where object oriented design come handy. 
As functions become too large, one way to handle them is to break them into smaller functions and pass data from one to function to another. However, as the number of functions becomes large, designing, and managing the data passed to functions becomes difficult and error prone. Model implementations are rewritten using object oriented design. The following session describes major classed defined in the model implementation. 
Each class contains properties and methods.Properties store data while methods provides operations on data. 
### 3.1 Main Classes Defined
#### 3.2.1 Fiber
~~~matlab
properties
    propertyStruct ={};

methods
    function obj = Fiber1(val)
    function showOnGui(obj,tableHandle)
~~~

#### 3.2.2 Lamina
~~~matlab
properties
    propertyStruct ={}

methods
    function obj = Lamina1(val)
    function showOnGui(obj,tableHandle)
    function  resistivityTensor = getResistivityTensor(obj)
    function  resistivityTensor = getResistivityTensor(obj)
    function yResistivity = getYResistivity(obj)
    function yResistivity = getYResistivity(obj)
~~~

#### 3.2.3 Laminate
~~~matlab
properties
    propertyCell = {};
    parameterCell = {};
    propertyStruct = struct;
    parameterStruct = struct;
    propertyTable = table
methods
    function obj = Laminate1(val)
    function showOnGui(obj,tableHandle)
    function  resistivityTensor = getResistivityTensor(obj)
    function  resistivityTensor = getResistivityTensor(obj)
    function yResistivity = getYResistivity(obj)
    function yResistivity = getYResistivity(obj)
         ~~~

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


