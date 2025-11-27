# Projective Transformation via SVD

This project shows how to compute a 3×3 projective transformation matrix (homography) using Singular Value Decomposition (SVD) from point correspondences in homogeneous coordinates.

Given pairs of points  
x → x'  
we build a linear system:

    A * p = 0

where `p` is the 9-element vector containing the entries of the transformation matrix `P`.  
Each point correspondence contributes two independent equations, so four pairs produce an 8×9 matrix `A`.

To solve for `P`, we compute the SVD:

    A = U * D * V^T

and take the **last row of V^T** (the singular vector corresponding to the smallest singular value).  
Reshaping this vector into a 3×3 matrix gives the homography, up to scale.

---

## Example

Input point correspondences:

```python
pts = [
    [1, 2, -3],
    [1, 0, -1],
    [1, 2, 0],
    [3, -2, 1]
]

pts_prime = [
    [-6, -7, 17],
    [-4, 1, 5],
    [9, 11, 26],
    [0, 23, 9]
]

```
Computed projective transformation matrix:
```css
[ 1  4  5 ]
[ 7  2  6 ]
[ 8  9  3 ]
```
