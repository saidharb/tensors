+++
title = "Tensor algebra"
+++

# Tensor algebra
In the previous [chapter](/Theory/TensorIntro) we vaguely introduced the concept of higher (than first) order tensors. The key new concept was the open product, $\otimes$. This operations allows us to create a higher order tensor, by taking the open product between two vectors to create a second order tensor $\ts{a}$ as
\begin{align}
\ts{a} = \tv{u}\otimes\tv{v} = u_i v_j \twobase{i}{j} = a_{ij} \twobase{i}{j}
\end{align}

If we work with indicial expressions, we just need to respect the rules of the [index juggling](/Theory/IndexNotation/#index_juggling). However, it is often more convenient and easier to express without introducing indices. Therefore, we often write the expressions using actual tensors. First, we discuss the open product a bit more in detail. Thereafter, more operations and their definitions in index notation are described. By expanding the definitions, more examples and explanations are available. 

## Open product, "$\otimes$"
\collaps{The open product, also called "outer product" or "dyadic product", is a representation of multiple bases. Taking the open product between two tensors, $A$ and $B$, of arbitrary order, becomes
\begin{align}
A\otimes B &= \left(A_{i_1\,i_2,\cdots,i_n} \twobase{i_1}{i_2}\cdots\onebase{i_n}\right) \otimes \left(B_{j_1\,j_2,\cdots,j_m} \twobase{j_1}{j_2}\cdots\onebase{j_m}\right)\\
&= A_{i_1\,i_2,\cdots,i_n} B_{j_1\,j_2,\cdots,j_m} \twobase{i_1}{i_2}\cdots\onebase{i_n} \otimes \twobase{j_1}{j_2}\cdots\onebase{j_m}
\end{align}
Hence, this product doesn't actually "do" anything. It just represents multiple bases.
In pure index notation, if we have e.g. $\tf{C}=\ts{a}\otimes\ts{b}$, then $\tfind{C}{ijkl}=a_{ij} b_{kl}$.
}{
Another way to think is that $\baseij$ are 9 2nd order base tensors for a 2nd order tensor. I.e., $\baseij$ represents 9 orthogonal directions for a 2nd order tensor. Considering a particular base, e.g. $\twobase{1}{2}$, it can be represented in matrix form in the $\basei$ coordinate system, as
\begin{align*}
\left[ \twobase{1}{2} \right] = \begin{bmatrix} 0 & 1 & 0 \\ 0 & 0 & 0 \\ 0 & 0 & 0\end{bmatrix}
\end{align*}
$\twobase{1}{2}$ is similar to a basis vector, $\basei$, except that we now have a 2nd order base tensor

In pure index notation, the open product correspond to multiplying two index objects, say $b_i$ and $c_j$, with different free indices, i.e. $a_{ij} = b_i c_j$

If we would like to express this as matrix operations, it corresponds to the following vector-vector multiplication
\begin{align*}
\tv{u} = \begin{bmatrix} u_1 \\ u_2 \\ u_3 \end{bmatrix}, \quad
\tv{v} = \begin{bmatrix} v_1 \\ v_2 \\ v_3 \end{bmatrix}, \quad
\tv{u}\tv{v}\Trans = \begin{bmatrix} 
u_1 v_1 & u_1 v_2 & u_1 v_3 \\
u_2 v_1 & u_2 v_2 & u_2 v_3 \\
u_3 v_1 & u_3 v_2 & u_3 v_3 \end{bmatrix}
\end{align*}
where we see that we increased the order from vectors (1st order) to a matrix (2nd order). 
}


## Single contraction "$\cdot$"
\collaps{The single contraction is defined as the dot product between the closest basis vectors. For two 2nd order tensors this becomes\\
\begin{align}
\ts{a}\cdot\ts{b} &= a_{ij}\baseij \cdot b_{kl} \twobase{k}{l} = a_{ij} b_{kl} \baseij \cdot \twobase{k}{l} \\
& = a_{ij} b_{kl} \delta_{jk} \twobase{i}{l} = a_{ij} b_{jl} \twobase{i}{l}
\end{align}
Often, we skip the dot, "$\cdot$", except between two vectors, for convenience: e.g. $\ts{a}\cdot\ts{b}=\ts{a}\ts{b}$.
}{ *Additional examples*

* Two 1st order tensors, $\tv{u}\cdot\tv{v}$\\ $c = \tv{u}\cdot\tv{v} = u_i v_i$
* Two 2nd order tensors, $\ts{a}\ts{b}$\\ $\ts{c}=c_{ij}\twobase{i}{j}=\ts{a}\ts{b} = a_{ij} b_{jk} \twobase{i}{k}$ \\ *In pure index notation:* $c_{ij} = a_{ik} b_{kj}$
* 2nd and 1st order tensors, $\ts{a}\tv{u}$\\  $\ts{v}=v_{i}\onebase{i}=\ts{a}\tv{u} = a_{ij} u_{j} \onebase{i}$ \\ *In pure index notation:* $v_i=a_{ij} u_j$

Did you notice anything strange about the expression for two 2nd order tensors? The indices on the left and right hand side basis don't match ($c_{ij}\twobase{i}{j}$ versus $a_{ij}b_{jk}\twobase{i}{k}$). This is perfectly valid! The indices are [dummy indices](/Theory/IndexNotation/#index_juggling). However, when not writing out the basis vectors, we assume that we have the same indices and index order of the basis vectors in each term in an expression. If we have that, such as in the equivalent expression $c_{ik}\twobase{i}{k}=a_{ij} b_{jk} \twobase{i}{k}$, we can express it as $c_{ik} = a_{ij} b_{jk}$ and drop the basis vectors. This way of expressing it works if: (1) we have an orthonormal basis system and (2) that the basis vector indices and order are the same on both sides. 

The single contraction is the "standard" matrix-vector product used when doing matrix multiplication. It is sometimes called the *inner product*. 
}


## Double contraction, "$:$"
\collaps{The double contraction between tensors $A$ and $B$ (arbitrary order $\geq 2$) is defined as the dot product between $A$'s second last basis vector and $B$'s first basis vector and, at the same time, the dot product between $A$'s last basis vector $B$'s second basis vector. For two 4th order tensors this becomes\\
\begin{align}
\tf{A}:\tf{B} &= \tfind{A}{ijkl}\baseijkl : \tfind{B}{mnop} \fourbase{m}{n}{o}{p} \\
& = \tfind{A}{ijkl} \tfind{B}{mnop} (\onebase{k} \cdot \onebase{m}) (\onebase{l} \cdot \onebase{n})\fourbase{i}{j}{o}{p}\\
& = \tfind{A}{ijkl} \tfind{B}{mnop} \delta_{km} \delta_{ln} \fourbase{i}{j}{o}{p}\\
& = \tfind{A}{ijkl} \tfind{B}{klop} \fourbase{i}{j}{o}{p}
\end{align}
If we have $\tf{C}=\tf{A}:\tf{B}$, then, in pure index notation, $\tfind{C}{ijop}=\tfind{A}{ijkl}\tfind{B}{klop}$. 
}{ *Additional examples*

* Two 2nd order tensors, $\ts{a}:\ts{b}$ \\ $c = \ts{a}:\ts{b} = a_{ij} b_{ij}$
* 4th and 2nd order tensors, $\tf{A}:\ts{b}$ \\ $\ts{c} = c_{ij}\twobase{i}{j} = \tf{A}:\ts{b} = \tfind{A}{ijkl} b_{kl} \twobase{i}{j}$ \\ *In pure index notation:* $c_{ij} = \tfind{A}{ijkl} b_{kl}$

The double contraction can loosely be thought of, for 2nd and 4th order tensors, as the equivalent to the dot product for 1st and 2nd order tensors (*cf. vectors and matrices*). For example, as we will see later, the norm of a second order tensor, $\ts{a}$ is $\sqrt{\ts{a}:\ts{a}}$ and an "angle", $\theta$, between two tensors, $\ts{a}$ and $\ts{b}$ can be defined via $\sqrt{\ts{a}:\ts{a}}\sqrt{\ts{b}:\ts{b}}\cos(\theta)=\ts{a}:\ts{b}$.
}

\label{specialopenproducts}
## Special open products, "$\opu$" and "$\opl$"
\collaps{We may introduce special open products, that permutate the order of the basis vectors. Two common definitions for 2nd order tensors are
\begin{align}
\ts{a}\opu\ts{b} &= \left(a_{ik}\twobase{i}{k} \right) \opu \left(b_{jl} \twobase{j}{l}\right) \\
                 &= a_{ik} b_{jl} \left[\twobase{i}{k}\right] \opu \left[\twobase{j}{l}\right] \\
                 &= a_{ik} b_{jl} \baseijkl
\end{align}
If we have $\tf{C}=\ts{a}\opu\ts{b}$, then, in pure index notation, $\tfind{C}{ijkl}=a_{ik} b_{jl}$
\begin{align}
\ts{a}\opl\ts{b} &= \left(a_{il}\twobase{i}{l} \right) \opl \left(b_{jk} \twobase{j}{k}\right) \\
                 &= a_{il} b_{jk} \left[\twobase{i}{l}\right] \opl \left[\twobase{j}{k}\right] \\
                 &= a_{il} b_{jk} \baseijkl
\end{align}
If we have $\tf{C}=\ts{a}\opl\ts{b}$, then, in pure index notation, $\tfind{C}{ijkl}=a_{il} b_{jk}$
}{
  While it might seem arbitrary to introduce these special open products, they are useful in many cases. For example, the 4th order identity tensor is $\tf{I}=\ts{I}\opu\ts{I}$ where $\ts{I}$ is the 2nd order [identity tensor](/Theory/SpecialTensors). 
}


# Derived rules
By using our rules for index notation, we can investigate how the above multiplication operations behave. The first example here, is the order of operations for the dot product between two vectors, that is, 
\begin{align}
\tv{u}\cdot\tv{v} = u_i v_i = v_i u_i = \tv{v}\cdot\tv{u}
\end{align}
so clearly the order of the vectors do not matter. Similarly, for the double contraction between two 2nd order tensors, 
\begin{align}
\ts{a}:\ts{b} = a_{ij} b_{ij} = b_{ij} a_{ij} = \ts{b}:\ts{a}
\end{align}
we also have no difference if we flip the order. However, if we take the dot product between a 2nd and 1st order tensor, 
\begin{align}
\ts{a}\cdot\tv{u} = a_{ij} u_j = u_j a_{ij} \neq \tv{u}\cdot\ts{a}\; \forall\; \ts{a}
\end{align}
The reason that the last relation is not equal for all $\ts{a}$, is that we contract the the last index of $\ts{a}$ with $\tv{u}$'s index. (Note that if $\ts{a}$ is [symmetric](/Theory/TensorOperations#transposition), then this would be an equality.)

If we instead would look at a sum, we can consider $\tf{A}:\left[\ts{b} + \ts{c}\right]$,
\begin{align}
\tfind{A}{ijkl}\left[b_{kl} + c_{kl}\right] = \tfind{A}{ijkl} b_{kl} + \tfind{A}{ijkl} c_{kl}
\end{align}
Which holds as we are only considering summation and multiplication when working with the indices, i.e. $\tf{A}:\left[\ts{b} + \ts{c}\right]=\tf{A}:\ts{b} + \tf{A}:\ts{c}$

# Cross product with vector
For completeness, the cross product between a 2nd order tensor and a vector is given as 
\begin{align}
\ts{a}\times\tv{v} = a_{ij} v_k \baseij \times \onebase{k} = a_{ij} v_k \onebase{i} \otimes [\varepsilon_{jkm} \onebase{m}] = \varepsilon_{jkm} a_{ij} v_k \twobase{i}{m}
\end{align}