# Lecture 6 | Training Neural Networks I

- Activation function
    - Sigmoid

        $$\sigma(x)=1 /\left(1+e^{-x}\right)$$

        - Problems:
            1. Kills the gradient and no gradient flow coming back
            2. Sigmoid outputs are not zero-centered. The thing is that the gradients of w after passing throught the sigmoid fuction is either all positive or all negative.

            ![Lecture%206%20Training%20Neural%20Networks%20I%207b407dafb7914932886524366afe46bc/Untitled.png](Lecture%206%20Training%20Neural%20Networks%20I%207b407dafb7914932886524366afe46bc/Untitled.png)

            3.  exp() is a bit compute expensive

    - Tanh
        - Zero centered (nice thing)
        - It has the same problem as the Sigmoid funtion, it kills the gradient.
    - ReLU

        $$f(x)=\max (0, x)$$

        - Advantages
            - Does not saturate (in +region)
            - Very computationally efficient
            - Converges much faster than the sigmoid/tanh in practice (e.g. 6x)
            - more bilogically plausible than sigmoid
        - disadvantages
            - Not zero-centered output

    - Leaky ReLU

        $$f(x)=\max (\alpha x, x)$$

    - Exponential Linear Units (ELU)

        ![Lecture%206%20Training%20Neural%20Networks%20I%207b407dafb7914932886524366afe46bc/Untitled%201.png](Lecture%206%20Training%20Neural%20Networks%20I%207b407dafb7914932886524366afe46bc/Untitled%201.png)

    - Maxout "Neuron"
- Data Preprocessing
    - Zero-centering the data then normalize them
- Weight Initialization
    - If W is set to 0, then all of them will do the same exact thing because most of them do the same operation and connected in the same exact way.
    - W is set to small random numbers at deeper networks, late layers become 0, and this causes vanishing gradients
    - Xavier Initialization
        - First thing to take into consideartion is that it considers linear activation so ReLU breaks the purpose. ReLU will break half of the weights.
    - He Initialization

        It fixes the ReLU thing in the Xavier Initialization by adding (/2).

- Batch Normalization

    $$\widehat{x}^{(k)}=\frac{x^{(k)}-\mathrm{E}\left[x^{(k)}\right]}{\sqrt{\operatorname{Var}\left[x^{(k)}\right]}}$$

    ![Lecture%206%20Training%20Neural%20Networks%20I%207b407dafb7914932886524366afe46bc/Untitled%202.png](Lecture%206%20Training%20Neural%20Networks%20I%207b407dafb7914932886524366afe46bc/Untitled%202.png)

    - **It is usually inserted after Fully Connected layers or Convolutional layers and before nonlinearity**

    ![Lecture%206%20Training%20Neural%20Networks%20I%207b407dafb7914932886524366afe46bc/Untitled%203.png](Lecture%206%20Training%20Neural%20Networks%20I%207b407dafb7914932886524366afe46bc/Untitled%203.png)

    - $\gamma$ and $\beta$ helps you recover the data as if before batch normalization. Those parameters can be learned by the network in case it needed the data in its origional form not only in the gaussian form.

    $$y^{(k)}=\gamma^{(k)} \widehat{x}^{(k)}+\beta^{(k)}$$

    - You can think of Batch normalization as a funny form of regularization as it mean and variance are not diterministic (change with each batch)

- Learning rate
    - rough estimate is 1e-4 to 1e-3
    - To detect if there is something worng if the cost is 3x origional cost then it is exploding