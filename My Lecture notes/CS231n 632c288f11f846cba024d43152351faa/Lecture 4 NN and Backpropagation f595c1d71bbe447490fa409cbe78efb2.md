# Lecture 4 | NN and Backpropagation

- Computational graphs

    ![Lecture%204%20NN%20and%20Backpropagation%20f595c1d71bbe447490fa409cbe78efb2/Untitled.png](Lecture%204%20NN%20and%20Backpropagation%20f595c1d71bbe447490fa409cbe78efb2/Untitled.png)

    - We use the chain rule.
    - each node is only aware of its surroundings.
    - The node knows the inputs and the output and the local gradient of the output with respect to the input, and the local gradient.

    ![Lecture%204%20NN%20and%20Backpropagation%20f595c1d71bbe447490fa409cbe78efb2/Untitled%201.png](Lecture%204%20NN%20and%20Backpropagation%20f595c1d71bbe447490fa409cbe78efb2/Untitled%201.png)

    - **Patterns in backward Flow:**

    ![Lecture%204%20NN%20and%20Backpropagation%20f595c1d71bbe447490fa409cbe78efb2/Untitled%202.png](Lecture%204%20NN%20and%20Backpropagation%20f595c1d71bbe447490fa409cbe78efb2/Untitled%202.png)

    but now x, y, and z are vectors. this makes us to use the **Jacobian matrix** (deravative of each element of z w.r.t each element of x)

    ![Lecture%204%20NN%20and%20Backpropagation%20f595c1d71bbe447490fa409cbe78efb2/Untitled%203.png](Lecture%204%20NN%20and%20Backpropagation%20f595c1d71bbe447490fa409cbe78efb2/Untitled%203.png)

    And this is the vectorized gradient of this equation bounded

    $$\nabla_{W} f=2 q \cdot x^{T}$$