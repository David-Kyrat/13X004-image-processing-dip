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

## Mean


1. 
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

<br>

2. 
    ```python
    a.mean(1) # mean for rows because there 3 mean component (1 for each row)
    ```


    ```Python
    [[3 0]
     [3 3]
     [3 2]]

     array([0. , 1.5, 1.5])
    ```


<br>

3. 
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

<br>

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

<br>

5. 
    ```python
    print(a.shape)
    a.mean(2) # mean for lignes internes because there 3 mean component (1 for each elem, 3 times 2 pixel/vector)
    ```

Mean of each element. If each element is a pixel i.e. 3 vector => mean of that vector / pixel for each coordinate

    ```Python
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
