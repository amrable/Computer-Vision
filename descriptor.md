# Feature detectors and descriptors

_Basic reading: Szeliski textbook, Sections 4.1.2, 14.1.2._

### Why do we need feature descriptors?
- Matching features 
- Object instance recognition
- Mosaicing

## Designing Feature descriptors 

1. Similar content must have similar descriptors
2. It should be invariant to photometric transformation
    - not affected by the illuminations
3. It should be invariant to geometric transformation
    - ex : rotations and prespectives

## Types of descriptors

## 1. Image patch 

- The simplest way to describe an image is to get its numeric representation(vector of intensity values)
- for large images we can decrease it to be a tiny images ( Downsample )

Advantages:
- Perfectly fine if geometry and appearance is unchanged (a.k.a. template matching)
- Simple, fast, robust to small affine transforms.

Disadvantages:
- Sensitive to absolute intensity values

## 2. Image gradients

- Use vecctor of X derivatives
- Adv : Feature is invariant to absolute intensity values
- Dis adv: sensitive to deformations

## 3. Color Histograms

- Invariant to changes in scale and rotation
- Not unique
- sensitive to spatial layout

## 4. Spatial Histograms
- Compute histograms over spatial ‘cells’
- Retains rough spatial layout
- Some invariance to deformations

Dis adv.
- How can you be completely invariant to rotation?

## 5. Orientation normalization
- Use the dominant image gradient direction to normalize the orientation of the patch save the orientation angle.


TBD:

_ GIST
_ HOG
_ SIFT
