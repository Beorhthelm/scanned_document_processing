# Scanned document processing

### Rank decomposition

For an arbitrary matrix $A$ of the rank $r$ with $m$ rows and $n$ columns there exist two matrices $B$ (with $m$ rows and $r$ columns) and $C$ (with $r$ rows and $n$ columns) such that $A=BC$.

**Example**

$A$ is a matrix of rank one.

$$
\begin{pmatrix}
4 & 8 & 12 & 16\\
3 & 6 & 9 & 12\\
2 & 4 & 6 & 8\\
1 & 2 & 3 & 4
\end{pmatrix} =
\begin{pmatrix}
4\\
3\\
2\\
1
\end{pmatrix}
\begin{pmatrix}
1 & 2 & 3 & 4
\end{pmatrix}.
$$

### How to find the Rank decomposition?

We could apply the Gaussian elimination process the matrix $A$ and obtain a reduced row echelon form $\tilde C$. Then we could take matrix $C$ as $\tilde C$ without zero rows. The matrix $C$ will have exactly $r$ rows, where $r=rank(A)$. As matrix $B$ we could take the columns from the matrix $A$, corresponding to the leading coefficients in $\tilde C$. It will have exactly $r$ columns.<br>
We select the basis of the span of the columns for the matrix $B$ and the $C$ is a matrix of the coefficients that would take to reconstruct $A$.

**Example**

$$A =
\begin{pmatrix}
2 & 1 & 1 & 3\\
1 & 0 & 1 & -1\\
1 & 1 & 0 & 4
\end{pmatrix}
\sim
\begin{pmatrix}
1 & 0 & 1 & -1\\
0 & 1 & -1 & 5\\
0 & 0 & 0 & 0
\end{pmatrix}$$

Let us take

$$
B =
\begin{pmatrix}
2 & 1\\
1 & 0\\
1 & 1
\end{pmatrix}
\text{ and }
C =
\begin{pmatrix}
1 & 0 & 1 & -1\\
0 & 1 & -1 & 5
\end{pmatrix}
\text{, then}
$$

$$
BC = 
\begin{pmatrix}
2 & 1 & 1 & 3\\
1 & 0 & 1 & -1\\
1 & 1 & 0 & 4
\end{pmatrix}
= A.
$$

### Compression of a scanned document using rank decomposition

<p align="center">
<img src="https://github.com/Beorhthelm/scanned_document_processing/blob/70ca8b54670de865495e435606fe076945cb5d7b/pic/Alexander_Pushkin_Eugene_Onegin1.png?raw=true" alt="Sample" width="40%">
</p>

As an example of a scanned document, we consider such rectangular black and white matrix. Here we have a piece of the Eugene Onegin novel written by Alexander Pushkin. Each entry of the matrix has one of two values, for example, zero or one. Zero represents black pixel, while one - white pixel. So, we could apply the rank decomposition to compress this image, namely to obtain two matrices that will have smaller size. Note that it works because the matrix has many totally white rows or totally white columns, so this compression can indeed reduce the size. One should note that it's not the best way to compress an image or even a scanned document. The algebra has some more efficient tools.