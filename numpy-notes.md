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

