---
tags:
  - ba5
  - improc
  - numpy
  - cheatsheet
class: improc
url: https://moodle.unige.ch/course/view.php?id=2291
description: idiomatic and useful numpy / data science stuff
---

# Numpy Quick Notes & tips

## Slicing - 1 liner to modify whole image / tensor (n x m x 3)


```python
import numpy as np
test = np.zeros((5, 5, 3))
test[:,:] = [0,0,100];

```


1. test = np.zeros((5, 5, 3)): Here, a NumPy array test is created using the np.zeros function. The array has dimensions 5x5x3, meaning it's a 3D array with a shape of 5 rows, 5 columns, and 3 color channels (for an RGB image).

2. test[:,:] = [0,0,100]: This line assigns the RGB color [0, 0, 100] to all elements in the 5x5x3 array. The [:,:] is a slice notation that selects all rows and columns in the array.

So, after this code, the test array will contain the RGB color [0, 0, 100] in all its elements. If you were to visualize this as an image, it would be a solid blue color.

i.e. [:,:] selectionne toutes les colonnes => toute la matrice
e.g.

test[:,:,2] => selectionne toutes les 3e colonnes
i.e. on une image => une liste de liste de vecteur 1x3. chaque element est du type `[0, 0, 0]`

```python
array([[[  0.,   0., 100.],
        [  0.,   0., 100.],
        [  0.,   0., 100.],
        [  0.,   0., 100.], ...

        [[  0.,   0., 100.],
        [  0.,   0., 100.],
        [  0.,   0., 100.],
        [  0.,   0., 100.],
        [  0.,   0., 100.]]])
```

Ici `test[:,:,2]` return la composante bleu de tous les pixels (r,g,b) i.e. la colonne 2 (3e) de chaque colonne.
(une colonne ou une ligne est juste une liste/vecteur de pixel => une liste d'array 1x3 )

i.e. 

```python
array([[100., 100., 100., 100., 100.],
       [100., 100., 100., 100., 100.],
       [100., 100., 100., 100., 100.],
       [100., 100., 100., 100., 100.],
       [100., 100., 100., 100., 100.]])
```

```python
test[:,:, 2] *= 2

test
> array([[[  0.,   0., 200.],
        [  0.,   0., 200.],
        [  0.,   0., 200.],
        [  0.,   0., 200.],
        [  0.,   0., 200.]],

test[:, :, 2]

> array([[200., 200., 200., 200., 200.],
       [200., 200., 200., 200., 200.],
       [200., 200., 200., 200., 200.],
       [200., 200., 200., 200., 200.],
       [200., 200., 200., 200., 200.]])
```

## Mean - Sort


1.  **Cols**
    ```python
    a = np.random.randint(4, size=(3, 2))
    print(a)
    a.mean(0) # mean for cols because there 2 mean component (1 for each col)
    ```


    ```Python
    [[3 0]
     [3 3]
     [3 2]]
     
    array([3.        , 1.66666667])
    ```

2. **Rows**
    ```python
    a.mean(1) # mean for rows because there 3 mean component (1 for each row)
    ```


    ```Python
    [[3 0]
     [3 3]
     [3 2]]

     array([0. , 1.5, 1.5])
    ```


3.  **3D**
    ```python
    a = np.random.randint(4, size=(3, 2, 3))
    print(a)
    a.mean(1) # mean for rows because there 3 mean component (1 for each row, 3 rows)
    ```


    ```Python
    [[[3 1 2]
      [2 3 0]]

     [[2 2 3]
      [1 2 1]]

     [[0 0 2]
      [2 3 2]]]
     

    array(
      [[2.5, 2. , 1. ],
       [1.5, 2. , 2. ],
       [1. , 1.5, 2. ]])

    ```


4. 
    ```python
    a.mean(0) # mean for cols because there 2 mean component (1 for each col, 2 cols)
    ```

    ```Python
    [[[3 1 2]
      [2 3 0]]

     [[2 2 3]
      [1 2 1]]

     [[0 0 2]
      [2 3 2]]]


    array([[2.33333333, 1.        , 1.        ],
           [2.33333333, 2.        , 2.33333333]])
    ```


5. 
    ```python
    print(a.shape)
    a.mean(2) # mean for lignes internes because there 3 mean component (1 for each elem, 3 times 2 pixel/vector)
    ```

> [!HINT]
> Mean of each element. If each element is a pixel i.e. 3 vector => mean of that vector / pixel for each entry in "2d matrix" of pixel.
> i.e. 3D matrix => 2D matrix where each pixel is replaced by the mean of its rgb component.



```python
(3, 2, 3)
[[[2 2 2]
  [0 2 0]]

 [[2 1 0]
  [0 1 2]]

 [[0 2 0]
  [1 1 0]]]

array(
  [[2.        , 0.66666667],
   [1.        , 1.        ],
   [0.66666667, 0.66666667]])
```

# Np.stack

# TODO!

arrays = [np.random.randint(0, 3, (3, 4)) for _ in range(2)]
assert np.array([res[0,0], res[1,0]]).all() == res[:,0].all()
print(arrays)
print("------")
res = np.stack(arrays, 2)
print(res.shape)
print(res, "\n\n")
print(res[:,0])

[array([[1, 0, 1, 2],
       [2, 1, 2, 2],
       [2, 2, 0, 2]]), array([[0, 0, 1, 1],
       [1, 1, 0, 1],
       [0, 0, 0, 2]])]
------
(3, 4, 2)
[[[1 0]
  [0 0]
  [1 1]
  [2 1]]

 [[2 1]
  [1 1]
  [2 0]
  [2 1]]

 [[2 0]
  [2 0]
  [0 0]
  [2 2]]] 


[[1 0]
 [2 1]
 [2 0]]


----

stack 1


[array([[1, 1, 1, 2],
       [1, 1, 1, 2],
       [1, 2, 2, 0]]), array([[0, 1, 0, 0],
       [1, 1, 0, 1],
       [2, 0, 1, 2]])]
------
(3, 2, 4)
[[[1 1 1 2]
  [0 1 0 0]]

 [[1 1 1 2]
  [1 1 0 1]]

 [[1 2 2 0]
  [2 0 1 2]]] 


[[1 1 1 2]
 [1 1 1 2]
 [1 2 2 0]]


 ----


 stack 0 


 array([[1, 1, 1, 0],
       [0, 2, 2, 0],
       [2, 2, 1, 2]]), array([[1, 0, 1, 0],
       [2, 0, 0, 2],
       [2, 1, 0, 2]])]
------
(2, 3, 4)
[[[1 1 1 0]
  [0 2 2 0]
  [2 2 1 2]]

 [[1 0 1 0]
  [2 0 0 2]
  [2 1 0 2]]] 


[[1 1 1 0]
 [1 0 1 0]]


# comment ^^ and format / rewrite this

list of matrix => each row of matrix became an element of the bigger tensor containing the 2 mat. I.e. "concatenate according to row"
row 1 = mat1
Row 2 = mat2
col

***

For axis = 1 =>  
(3,4)=> (3,2,4)
3 rows 4 cols => 3 rows 2 cols 4 depth
Cols of 3d is array of rows of inner 2d.

Splits the 2d 3x4 matrix into 3 lines of 2x4 matrix.  
=> take =>  
=> [1st row of mat 1, 1st row of mat 2]  
=> [2nd row of mat 1, 2nd row of mat 2]  
=> [3rd row of mat 1, 3rd row of mat 2]

**Always takes first $k$ value of each matrix in array. Where $k$ is the value of the n-th dimension when calling `np.stack(axis=n)`. It _will_ split the original matrices**



