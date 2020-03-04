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

<img width="534" alt="Screen Shot 2020-03-04 at 22 13 59" src="https://user-images.githubusercontent.com/31357623/75919137-ac153400-5e65-11ea-8d75-e4f04276c8a0.png">


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

<img width="534" alt="Screen Shot 2020-03-04 at 22 14 14" src="https://user-images.githubusercontent.com/31357623/75919200-c2bb8b00-5e65-11ea-9dc1-6faa025fe374.png">


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



<img width="534" alt="Screen Shot 2020-03-04 at 22 14 25" src="https://user-images.githubusercontent.com/31357623/75919287-ef6fa280-5e65-11ea-8426-68174b958f81.png">

Instead of computeing eigen vectors without actually needing them, we can make use of the symmetry of matrix M.

Since M is symmetric, we have

<img width="534" alt="Screen Shot 2020-03-04 at 22 14 32" src="https://user-images.githubusercontent.com/31357623/75919317-fd252800-5e65-11ea-9370-a4e2bfda3687.png">

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
 <img width="534" alt="Screen Shot 2020-03-04 at 22 14 54" src="https://user-images.githubusercontent.com/31357623/75919398-25ad2200-5e66-11ea-8805-e344b5a5b36b.png">

2. Eigenvalues need to be bigger than one
<img width="534" alt="Screen Shot 2020-03-04 at 22 14 47" src="https://user-images.githubusercontent.com/31357623/75919394-23e35e80-5e66-11ea-94f2-adfa046e5200.png">
3. Use trace and det of matrix M ( trace = sum of diagonals )
 <img width="534" alt="Screen Shot 2020-03-04 at 22 14 43" src="https://user-images.githubusercontent.com/31357623/75919387-21810480-5e66-11ea-9b7a-5346194cd36f.png">
    
If R value is positive => there is a corner,
otherwise => egde or flate

---

## Harris corner response is invariant to rotation

Ellipse rotates but its shape (eigenvalues) remains the same

## Harris corner response is invariant to intensity changes

Partial invariance to affine intensity change
- Only derivatives are used => invariance to intensity
shift I → I + b
- Intensity scale: I → a I

## The Harris corner detector is not invariant to scale




TBD : Multi scale detector
