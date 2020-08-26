# Lecture 3 | Loss Functions and Optimization

## General notes

The data set is represented as the pair:

$$\left\{\left(x_{i}, y_{i}\right)\right\}_{i=1}^{N}             $$

and the **loss over the dataset** is a sum of loss over examples: 

$$L=\frac{1}{N} \sum_{i} L_{i}\left(f\left(x_{i}, W\right), y_{i}\right)$$

---

- **Multi-class SVM loss**

    **Definition**:

    This says that I want my detected class score to be higher than the rest of the other scores and not only higher, but higher with a given margin and the margin in the below example is 1.

    given (x_i, y_i) where x is the data and y is the label:

    $$s=f\left(x_{i}, W\right)$$

    **SVM loss** has the form:

    $$\begin{aligned}L_{i} &=\sum_{j \neq y_{i}}\left\{\begin{array}{ll}0 & \text { if } s_{y_{i}} \geq s_{j}+1 \\s_{j}-s_{y_{i}}+1 & \text { otherwise }\end{array}\right.\\&=\sum_{j \neq y_{i}} \max \left(0, s_{j}-s_{y_{i}}+1\right)\end{aligned}$$

     **A concrete example** of this that demostrates s_j and s_y_i perfectly in this image:

    ![Lecture%203%20Loss%20Functions%20and%20Optimization%204953d75c114945bca554c8de70c09fa1/Untitled.png](Lecture%203%20Loss%20Functions%20and%20Optimization%204953d75c114945bca554c8de70c09fa1/Untitled.png)

    **Initialization of the weights:**

    A good way of doing it is is to initialize the weights to be too small. At the beginning you will see that the loss is equal to #num_of classes -1 if the margin is 1.
    This is because the correct score can't differ by 1 at the initialization so by using the formula you loop C-1 times.

    - what if we used the **squared loss** (just squaring the loss) instead of this linear loss?

        This depends on how much do you hate being wrong. If you really really hate being wrong then you will use a squared loss.

    - Implemenation

        ![Lecture%203%20Loss%20Functions%20and%20Optimization%204953d75c114945bca554c8de70c09fa1/Untitled%201.png](Lecture%203%20Loss%20Functions%20and%20Optimization%204953d75c114945bca554c8de70c09fa1/Untitled%201.png)

    - There can be multiple W that achieve 0 loss, like 2W, nW (This can lead to overfitting), so to solve this problem we will add the regularization term, which will take the simpler version of W that gives this loss.

    $$L(W)=\frac{1}{N} \sum_{i=1}^{N} L_{i}\left(f\left(x_{i}, W\right), y_{i}\right)+\lambda R(W)$$

    - The regularization term simply gives penalty with respect to the W
    - The most used regularization term is L2 regularization

    $$\text { L2 regularization } \quad R(W)=\sum_{k} \sum_{l} W_{k, l}^{2}$$

    $$\text{L1 regularization  } R(W)=\sum_{k} \sum_{l}\left|W_{k, l}\right|$$

---

- **Softmax Classifier (Multinomial Logistic Regression)**
    - Definition: scores = unnormalized log probabilities of the classes.
    - We take the score and exponentiate it and normalize it with the sum of all exponents

    $$P\left(Y=k | X=x_{i}\right)=\frac{e^{s_k}}{\sum_{j} e^{s_j}} \quad \text { where } \quad s=f\left(x_{i} ; W\right)

    $$

    - We want to maximize the log likelihood, and in this case becasue all of the values are normalized (less or equal to 1), then we want to minimize the negative log likelihood of the correct class:

    $$L_{i}=-\log P\left(Y=y_{i} | X=x_{i}\right)$$

    - **A good debugging tip:**
    Weights are intialized with really small values, so the probabilites are so small. This means that the loss will be around -log(1/c) = log(c), where c is the the number of classes.
    - The main differecnce between the negative log likelihood of minimization

---

- **Recap**

    ![Lecture%203%20Loss%20Functions%20and%20Optimization%204953d75c114945bca554c8de70c09fa1/Untitled%202.png](Lecture%203%20Loss%20Functions%20and%20Optimization%204953d75c114945bca554c8de70c09fa1/Untitled%202.png)

---

- **Optimization**
    - The first thing you can imagine using is to follow the slope numerically like this:

    $$\frac{d f(x)}{d x}=\lim _{h \rightarrow 0} \frac{f(x+h)-f(x)}{h}$$

    - An example is:

    ![Lecture%203%20Loss%20Functions%20and%20Optimization%204953d75c114945bca554c8de70c09fa1/Untitled%203.png](Lecture%203%20Loss%20Functions%20and%20Optimization%204953d75c114945bca554c8de70c09fa1/Untitled%203.png)

    - The above solution is not practical at all because W can be millions or billions of parameters and we just can't do this operation one by one.
    - Instead of using numerical gradients we compute the analytic gradient, as it is exact, fast, and error-prone. We can use numeric gradients to check the implementation of the analytic gradient if it is the same or not.
    - In stead of full-batch gradient descent, we use SGD or mini-batch gradient descent.

    $$\nabla_{W} L(W)=\frac{1}{N} \sum_{i=1}^{N} \nabla_{W} L_{i}\left(x_{i}, y_{i}, W\right)+\lambda \nabla_{W} R(W)$$