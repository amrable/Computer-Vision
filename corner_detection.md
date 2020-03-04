# Detecting corners

_Basic reading: Szeliski textbook, Sections 4.1._

## **Helps in**

- Image alignment (homography, fundamental matrix)
- 3D reconstruction
- Motion tracking
- Object recognition
- Indexing and database retrieval
- Robot navigation

--- 
## **Recall :** Visualizing Quadratics

-  Equation of a ‘bowl’ (paraboloid) 
   -  f(x,y) = x<sup>2</sup> + y<sup>2</sup>
   -  If you slice the bowl at you get a circle of radius = 1.
   -  It can be represented by matrix multiplication => [ x y ] * A * [ x y ]T
$$
\left(\begin{array}{cc} 
x & y
\end{array}\right)
\left(\begin{array}{cc} 
1 & 0\\ 
0 & 1
\end{array}\right)
\left(\begin{array}{cc} 
x\\ 
y
\end{array}\right)
$$ 

- Singular Value Decomposition (SVD) for Matrix A
  - A = eig_vectors * eig_values * (eig_vectors)T
---
##  Harris Corners Detector

**Intiuition :** Consider shifting window W by (u,v)

- Informally, while shifting the window W
  - if there is not variance, there are no edges/corners (flat area)
  - if there is variance in one axis, it is an edge
  - if the are variance in many axis, it is a corner
  
These intuitions can be formalized by looking at the simplest possible matching criterion
for comparing two image patches, i.e., their summed square difference => E(u,v)

The surface E(u,v) is locally approximated by a quadratic form: [ u v ] * A * [ u v ]T
- Define an	summed square difference “error”	E(u,v):	
  - Ix - Gradient in x axis
  - Iy - Gradient in y axis
  - M - covariance matrix

 $$
 E(u,v) = 
\left(\begin{array}{cc} 
u & v
\end{array}\right)
\left(\begin{array}{cc} 
M
\end{array}\right)
\left(\begin{array}{cc} 
u\\ 
v
\end{array}\right)
$$ 

$$
M = \Sigma
\left(\begin{array}{cc} 
Ix^{2} & IxIy\\ 
IxIy & Iy^{2}

\end{array}\right)
$$ 
---
## Program to detect corners

1. Compute image gradients over small region
2. Subtract mean from each image gradient
3. Compute the covariance matrix
4. Compute eigenvectors and eigenvalues
5. Use threshold on eigenvalues to detect corners

### 1. Compute image gradients over small region
    - Compute image gradients over a small region
    - Plot each pixel intensity ( Ix Iy axis)
    - distribution reveals edge orientation and magnitude

### 2. Subtract the mean from each image gradient
    Data is centered in the plot of image gradients (‘DC’ offset is removed)

### 3. Compute the covariance matrix
    Compute M - Covariance matrix -

### 4. Compute eigenvalues and eigenvectors

**Eigenvector problem**



$$ Me = \lambda e $$ 

Instead of computeing eigen vectors without actually needing them, we can make use of the symmetry of matrix M.

Since M is symmetric, we have
$$
M =  R^{-1}
\left(\begin{array}{cc} 
\lambda 1 & 0\\ 
0 & \lambda 2

\end{array}\right)
R
$$ 
We can visualize M as an ellipse with axis lengths determined by the
eigenvalues and orientation determined by R

**Eigenvalues possibilities**
| eig_val_1| eig_val_1| State |
|-----|-----|---|
|low|low|flat|
|low|high|edge|
|low|high|edge|
|high|high|corner|

### 5. Use threshold on eigenvalues to detect corners

Many ways to apply threshold

1. Use the smallest eigenvalue as the response function
   $$ R = min( \lambda 1 , \lambda 2) $$
2. Eigenvalues need to be bigger than one
   $$ R =  \lambda 1 \lambda 2 - k (\lambda 1 + \lambda 2)^{2}  $$
3. Use trace and det of matrix M ( trace = sum of diagonals )
   $$ R =  det(M) - k trace^{2}(M)  $$
    
If R value is positive => there is a corner,
otherwise => egde or flate
