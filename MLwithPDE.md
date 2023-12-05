## Terminologies
* __"Mesh-invariant neural networks"__ would be a concept aiming to develop neural networks that can effectively operate on data represented by different meshes or discretizations. This would be particularly useful in applications where the choice of mesh might vary or where a model needs to generalize across different discretizations of the same underlying problem.
* __"Mesh-Dependent Nature"__ suggests that the accuracy and performance of these numerical methods are closely tied to the specific way the mesh is constructed or discretized.
Different meshes or discretizations may lead to different numerical results, and the accuracy of the numerical solution can be influenced by the choice of mesh.

## Motivation 
Solving PDE is one of the most common and intricate problems in science and engineering. A data-driven approach has been proven to be more efficient and accurate than traditional discretizational solvers. Here, we introduce the __Fourier neural operator__, a novel deep learning architecture, which consists mostly of two previous works. 
* Recent works of __neural Operators__ (citation), enable to transfer solutions between meshes. Moreover, the neural operator needs to be trained only once, which means it has only passed one time through the neural network. Lastly, the neural operator requires no knowledge of the underlying PDE, only data. 
*  __The Fourier transform__ is frequently used in spectral methods for solving differential equations, since differentiation is equivalent to multiplication in the Fourier domain. Fourier transforms have also played an important role in the development of deep learning. Empirically, they have been used to speed up convolutional neural networks. Recently, some spectral methods for PDEs have been extended to neural networks. This paper builds on these works by proposing a neural operator architecture defined directly in Fourier space with quasi-linear time complexity and state-of-the-art approximation capabilities.
 
## Performance highlights
* The Fourier neural operator is the first work that learns the resolution-invariant solution operator
for the family of Navier-Stokes equation in the turbulent regime, where previous graph-based
neural operators do not converge.
* By construction, the method shares the same learned network parameters irrespective of the discretization used on the input and output spaces. It can do zero-shot super-resolution: trained on a lower resolution and directly evaluated on a higher resolution.
* The proposed method consistently outperforms all existing deep learning methods.
* On a 256 × 256 grid, the Fourier neural operator has an inference time of only 0.005s compared to the 2.2s of the pseudo-spectral method used to solve Navier-Stokes. Despite its tremendous speed advantage, the method does not suffer from accuracy degradation when used in downstream applications such as solving the Bayesian inverse problem.

## The Learning Operators
Suppose G is the mapping between two infinite dimensional spaces from a finite collection of observed input-output pairs. We use a parameterized mapping $G_\theta$ to approximate G and then seek a minimizer for calculating the cost. Showing the existence of minimizers, in the infinite-dimensional setting, remains a challenging open problem. We will approach this problem in the test-train setting by using a data-driven empirical approximation to the cost used to determine θ and to test the accuracy of the approximation.

## The architecture of Fourier neural operator
(here need to insert the architecture figure)
* P and Q are local transformation P which is usually parameterized by a shallow fully-connected neural network.
* Fourier Transformation layers are defined below:



