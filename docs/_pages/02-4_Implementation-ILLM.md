---

layout: page
title: Iterative Least Likely Method

---

Both of the previous methods are untargeted attacks, so they only try to change the prediction to another class, most likely one similar to that of the original class leading to uninteresting results. For example, adversarially perturbation may only confuse the classifier from labelling a Husky as an Alaskan Malamute, two similar looking breeds of dog. With some small modifications to the Basic Iterative Method, it is possible to turn it into a targetted adversarial attack. 

By changing the BIM algorthm to alter the image towards a specific target class instead of away from the correct class, it creates . A problem arises in studying the effectiveness of the algorithm because it would be dependent of the target class. In targetting the least likely class by choosing the lowest confidence class in each image gives the Iterative Least Likely Class Method (ILLM) [Adversarial Examples in the Physical World]((http://arxiv.org/abs/1607.02533)). By choosing the least likely class for each example, it gives an idea of the worst case scenario for the algorithm.

Similar to BIM a clean image $$X$$ is used for initialization in iteration $$N=0$$:

\begin{equation}
\tag{3.1}
\widetilde{X}_{0} = X 
\end{equation}

The next step is similar to BIM. The most noteable changes are the change in the + to a - to represent the modification of the image towards class $$Y_{LL}$$, the least likely class, as opposed to modifying it away from the correct label.

\begin{equation}
\tag{3.2}
X^{\prime}\_{1} = \widetilde{X}\_{0} - \alpha sign(\nabla\_{X} J(\widetilde{X}\_{0}, Y\_{LL}))
\end{equation}

As in equation 2.3 the adversary is generated by finally clipping the pixel values:

\begin{equation}
\tag{3.3}
\widetilde{X}\_{1} = min \( 255, X + \epsilon, max \( 0, X-\epsilon, X^{\prime}\_{1} \)\)
\end{equation}

These steps are repeated $$N$$ times. For the hyperparameters $$\alpha$$ and $$N$$ the authors use the same values as for BIM.

