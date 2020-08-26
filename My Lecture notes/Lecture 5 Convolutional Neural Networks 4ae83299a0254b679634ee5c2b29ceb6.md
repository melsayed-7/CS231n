# Lecture 5 | Convolutional Neural Networks

- CNN layer

    ![Lecture%205%20Convolutional%20Neural%20Networks%204ae83299a0254b679634ee5c2b29ceb6/Untitled.png](Lecture%205%20Convolutional%20Neural%20Networks%204ae83299a0254b679634ee5c2b29ceb6/Untitled.png)

    - It is not exactly dot product, but we can interpret it in this way by stretching the filter into a vector.
    - we use multiple filters so we get in this case 28x28x6 where 6 is the number of filters used.

    ![Lecture%205%20Convolutional%20Neural%20Networks%204ae83299a0254b679634ee5c2b29ceb6/Untitled%201.png](Lecture%205%20Convolutional%20Neural%20Networks%204ae83299a0254b679634ee5c2b29ceb6/Untitled%201.png)

    - The image above showhs at each level what maximizes each neuron at this level. At the low-level, we can see that  edges maximizes the neuron values, and at higher levels, more complex shapes maximize those values.
    - The output size of such convoluation is this:

    $$\frac{N - F}{Stride} + 1 \text{      where N is the image size, and F is the filter size}$$

    - To over come the probelm of looking at the edges too little, we pad the input image.
    - **Summary:**

    ![Lecture%205%20Convolutional%20Neural%20Networks%204ae83299a0254b679634ee5c2b29ceb6/Untitled%202.png](Lecture%205%20Convolutional%20Neural%20Networks%204ae83299a0254b679634ee5c2b29ceb6/Untitled%202.png)

    - Caffe implementation:

    ![Lecture%205%20Convolutional%20Neural%20Networks%204ae83299a0254b679634ee5c2b29ceb6/Untitled%203.png](Lecture%205%20Convolutional%20Neural%20Networks%204ae83299a0254b679634ee5c2b29ceb6/Untitled%203.png)

- Pooling Layer
    - It just makes the representations smaller and more manageable
    - operates over each activation map independently.
    - There is max pooling and average pooling, but max pooling works better.
    - Some use strides as a way of pooling, and -not sure- you can get better results than just normal pooling.
- Fully Connected Layer (FC layer)

    just putting all the output in a one big vector.

- Summary and typical architectures look

    ![Lecture%205%20Convolutional%20Neural%20Networks%204ae83299a0254b679634ee5c2b29ceb6/Untitled%204.png](Lecture%205%20Convolutional%20Neural%20Networks%204ae83299a0254b679634ee5c2b29ceb6/Untitled%204.png)