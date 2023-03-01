# Composing Transformations

#### **Overview**

In these notes, we review the concept of *composing functions* in the context of linear (geometric) transformations and matrices. Here, we will look at the *isomorphism* between linear transformations and matrices, and how this relationship is used for composing linear transformations by simply multiplying together the matrices of the transformations.

####**Isomorphism between linear transformations and matrices**

<blockquote style="border: 2px solid #666; padding: 10px; background-color: #EAEDED;"> <b>Isomorphism</b>. Linear transformations can be expressed in matrix form. Also, matrices are representations of linear transformations. This type of equivalence between algebraic structures is called <i>Isomorphism</i>. 
</blockquote>

Let $F$ be a linear transformation that maps a vector ${\bf x}$ to a vector $F({\bf x})$. Because of the isomorphism between linear transformations and matrices, we know that the matrix of the transformed vector is given by the product between the matrix of the transformation $F$ and the matrix of the original vector ${\bf x}$. This equivalence can be written as:    
$$
\begin{align}
	\left[F({\bf x})\right] &= \left[F\right] \cdot \left[{\bf x}\right]   
	\label{isomorphism}
\end{align}
$$

Here, $\left[{\bf x}\right]$ denotes the matrix of ${\bf x}$. Consider for example a rotation transformation $F$ that rotates the vector ${\bf x} = \left(1,0\right)^\mathsf{T}$ by an angle  $\theta = \frac{\pi}{4}$. The transformation operation can be written in matrix form as:
$$
\begin{align}
	\left[F({\bf x})\right] &= \left[F\right] \cdot \left[{\bf x}\right] \notag \\ 
	&=
	\begin{bmatrix}
		\cos\frac{\pi}{4} & -\sin\frac{\pi}{4} \\
		\sin\frac{\pi}{4} &  \cos\frac{\pi}{4}
	\end{bmatrix}
	\begin{bmatrix}
		1  \\
		0 
	\end{bmatrix}.
\end{align}
$$

Here, 
$$
\begin{align}
	\left[F\right] &= 
	\begin{bmatrix}
		\cos\frac{\pi}{4} & -\sin\frac{\pi}{4} \\
		\sin\frac{\pi}{4} &  \cos\frac{\pi}{4}
	\end{bmatrix}
\end{align}
$$

is called the *matrix of the rotation transformation*. 

#### **Composing transformations by multiplying transformation matrices**

In many applications, it is common for transformations to be combined with other transformations to form a composition of transformations. Given two linear transformation $F$ and $G$, the composition of $F$ and $G$ is defined by:
$$
\begin{align}
	\left(FG\right)\left({\bf x}\right) 
	= F\left(G\left({\bf x}\right)\right). \notag
\end{align}
$$
Following from the isomorphism in Equation $\ref{isomorphism}$, we have:
$$
\begin{align}
	\left[\left(FG\right)\left({\bf x}\right)\right] 
	&= \left[F\left(G\left({\bf x}\right)\right)\right] \notag \\
	&= \left[F\right]\cdot\left[G\left({\bf x}\right)\right] \notag \\
	&= \left[F\right]\cdot\left(\left[G\right]\cdot\left[{\bf x}\right]\right) \notag \\
	&= \left(\left[F\right]\cdot\left[G\right]\right)\cdot\left[{\bf x}\right].
  \label{compositionMatrix}
\end{align}
$$

Equation $\ref{compositionMatrix}$ tells us that we can compose linear transformations by simply multiplying together the matrices of the transformations. Here, the matrix of the composition transformation is given by:

$$
\begin{align}
	\left[FG\right] 
	&= \left[F\right] \left[G\right]. 
\end{align}
$$
For example, to compose the rotation $R$ and scaling $S$, and apply it to vector ${\bf x}$,  we do:
$$
\begin{align}
	\left[\left(RS\right)\left({\bf x}\right)\right] 
	&= \left(\left[R\right] \left[S\right]\right) \left[{\bf x}\right] \notag \\ 
	&=\left(
	\begin{bmatrix}
		\cos\frac{\pi}{4} & -\sin\frac{\pi}{4} \\
		\sin\frac{\pi}{4} &  \cos\frac{\pi}{4}
	\end{bmatrix}
	\begin{bmatrix}
		2 & 0 \\
		0 &  3
	\end{bmatrix}\right)
	\begin{bmatrix}
		1  \\
		0 
	\end{bmatrix} \\
	&=
  \begin{bmatrix}    
  	2\cos\frac{\pi}{4}  \\    
  	2\sin\frac{\pi}{4}   
  \end{bmatrix}. 	
  \label{exampleComposing}
\end{align}
$$

The order of multiplications is important. From matrix algebra, we know that the multiplication of matrices is not commutative, i.e., $AB \neq BA$ (for most cases). The same restriction applies to geometric transformations such as the ones in Equation $\ref{exampleComposing}$. Indeed, if we switched the order of multiplication in the example in $(\ref{exampleComposing})$, we would have:
$$
\begin{align}
	\left[\left(SR\right)\left({\bf x}\right)\right] 
	&= \left(\left[S\right] \left[R\right]\right) \left[{\bf x}\right] \notag \\ 
	&=\left(
	\begin{bmatrix}
		\cos\frac{\pi}{4} & -\sin\frac{\pi}{4} \\
		\sin\frac{\pi}{4} &  \cos\frac{\pi}{4}
	\end{bmatrix}
	\begin{bmatrix}
		2 & 0 \\
		0 &  3
	\end{bmatrix}\right)
  \begin{bmatrix}    
  1  \\    
  0   
  \end{bmatrix}  	
	\\
	&=
  \begin{bmatrix}    
  	2\cos\frac{\pi}{4}  \\    
  	3\sin\frac{\pi}{4}   
  \end{bmatrix}.
  \label{exampleComposingSwitched}
\end{align}
$$

As expected, $RS \neq SR$, and the resulting transformed vectors are different. 

The following figures show the result of the transformation on a unit square (blue). The red shape is the transformed shape. The transformations are $RS$ and $SR$, respectively.

<img src="rs_plot.png" alt="rs_plot" style="zoom:50%;" />

<img src="sr_plot.png" alt="rs_plot" style="zoom: 50%;" />

Again, the resulting shapes are different if we change the order of transformations, i.e., $RS \neq SR$. 