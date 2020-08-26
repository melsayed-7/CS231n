# Lecture 7 | Training Neural Networks II

**[Slides](http://cs231n.stanford.edu/slides/2017/cs231n_2017_lecture7.pdf)**

---

- Intuition about how normalization helps

    ![Lecture%207%20Training%20Neural%20Networks%20II%2006f34a50d997420c922551a7ca355668/Untitled.png](Lecture%207%20Training%20Neural%20Networks%20II%2006f34a50d997420c922551a7ca355668/Untitled.png)

    - (Befroe normalization) if the lines moves a little bit (small change in the weights), the loss will be very sensetive to this change, unlike the after initialization.

- Optimization
    - Problems with SGD

        ![Lecture%207%20Training%20Neural%20Networks%20II%2006f34a50d997420c922551a7ca355668/Untitled%201.png](Lecture%207%20Training%20Neural%20Networks%20II%2006f34a50d997420c922551a7ca355668/Untitled%201.png)

        - Local minima in higher dimensions are not something that can be encountered easily.
        - Saddle points, which are very frequent in higher dimensions.
        - Minibatches updates are noisy (because they are samples)
    - A great simple solution to the above problems is **Momentum**
        - It is simply taking into consideration the speed and then instead of moving towards the gradient we move towards the speed.
        - observe that we have the hyperparameter rho, which is simply to a decay constant so that if the curve is flat, it will eventually stop.

        ![Lecture%207%20Training%20Neural%20Networks%20II%2006f34a50d997420c922551a7ca355668/Untitled%202.png](Lecture%207%20Training%20Neural%20Networks%20II%2006f34a50d997420c922551a7ca355668/Untitled%202.png)

        - There is that **Nesterov Momentum** and what it does is that it goes in the direction of the velocity
    - **AdaGrad**

        ![Lecture%207%20Training%20Neural%20Networks%20II%2006f34a50d997420c922551a7ca355668/Untitled%203.png](Lecture%207%20Training%20Neural%20Networks%20II%2006f34a50d997420c922551a7ca355668/Untitled%203.png)

        - AdaGrad adds makes the change in the variance direction slower (because now we are dividing by a large number) and in the slow change direction we are moving faster, because we are dividing by a smaller number.
        - The problem with AdaGrad is that it makes you stuck at saddle points
        - it is good in convex cases but in non-convex cases it can be a problem.
    - **RMSProb**
        - RMSProb addresses the problem of AdaGrad by decaying the effect of grad_squared
        - It is very similar to the momentum concept but instead of using the actual gradient, it is using the squared gradient

        ![Lecture%207%20Training%20Neural%20Networks%20II%2006f34a50d997420c922551a7ca355668/Untitled%204.png](Lecture%207%20Training%20Neural%20Networks%20II%2006f34a50d997420c922551a7ca355668/Untitled%204.png)

        - In the above figure, we see that Momentum tends to overshoot, and RMSProb does not overshoot because it reduces (slows down) high change.
    - **Adam**
        - It is simply using both the momentum and RMSProb
        - The problem that needs to be solved is that at the beginning we divide by the second momentum (which is initialized by 0), and this can be overcome in the full form using the unbiases which will make it the second_moment around 1 at the beginning and by time it will be as if they weren't there

        ![Lecture%207%20Training%20Neural%20Networks%20II%2006f34a50d997420c922551a7ca355668/Untitled%205.png](Lecture%207%20Training%20Neural%20Networks%20II%2006f34a50d997420c922551a7ca355668/Untitled%205.png)

    - what any of the previous algorithms can't fix is that if the oval-like loss space is not aligned with the axis, you can't just cancel or slow down that much.
    - learning_rate decay is not something common when using Adam
    - L-BFGS
        - Works very well in full batch, deterministic mode.

- Model Ensembles
    - Train multiple independent models
    - At test time average their results
    - Around 2% extra performance
- Regularization
    - Dropout
        - In Deep learning, Dropout is common
        - At test time, all neurons are active always, and we simply multiply by probability of dropout while testing

        ![Lecture%207%20Training%20Neural%20Networks%20II%2006f34a50d997420c922551a7ca355668/Untitled%206.png](Lecture%207%20Training%20Neural%20Networks%20II%2006f34a50d997420c922551a7ca355668/Untitled%206.png)

        - And there is that cocept of inverted dropout which is more common

        ![Lecture%207%20Training%20Neural%20Networks%20II%2006f34a50d997420c922551a7ca355668/Untitled%207.png](Lecture%207%20Training%20Neural%20Networks%20II%2006f34a50d997420c922551a7ca355668/Untitled%207.png)

        - Training takes longer because gradient only goes through the non-dropout but generalizes better.
    - Data augmentation
        - flipping - contrast - brightness - random crops

        ![Lecture%207%20Training%20Neural%20Networks%20II%2006f34a50d997420c922551a7ca355668/Untitled%208.png](Lecture%207%20Training%20Neural%20Networks%20II%2006f34a50d997420c922551a7ca355668/Untitled%208.png)

    - normally batchnormalization works well, but if it overfits you use more and more methods.
- Transfer learning

    ![Lecture%207%20Training%20Neural%20Networks%20II%2006f34a50d997420c922551a7ca355668/Untitled%209.png](Lecture%207%20Training%20Neural%20Networks%20II%2006f34a50d997420c922551a7ca355668/Untitled%209.png)

    ![Lecture%207%20Training%20Neural%20Networks%20II%2006f34a50d997420c922551a7ca355668/Untitled%2010.png](Lecture%207%20Training%20Neural%20Networks%20II%2006f34a50d997420c922551a7ca355668/Untitled%2010.png)