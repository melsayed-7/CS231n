# Lecture 2 | Image Classification

## General notes

- Things like K and the distance metric are called hyper-parameters
- Test data is the last thing you test on mostly there is a validation set to test on while training.
- Cross-validation is only used for smaller datasets

---

## K-Nearest neighbour

- Definition

    In this algorithm you find the nearst k neighbours and do voting, and the resulting label will be the most voted label

- Why it is bad?

    Because the training is just memorizing the dataset, and whenever you want to classify a new object you just find the k nearest neighbours by looping over each sample in the training dataset.

- How does it look?

    ![Lecture%202%20Image%20Classification%209b5aacfdedd54d26ba5e4bcb2fc9efa6/Untitled.png](Lecture%202%20Image%20Classification%209b5aacfdedd54d26ba5e4bcb2fc9efa6/Untitled.png)

- Distance Metrics

    **L1 (Manhattan) distance**

    $$d_{1}\left(I_{1}, I_{2}\right)=\sum_{p}\left|I_{1}^{p}-I_{2}^{p}\right|$$

    **L2 (Eucledian) distance   (Mostly this is more generic)**

    $$d_{2}\left(I_{1}, I_{2}\right)=\sqrt{\sum_{p}\left(I_{1}^{p}-I_{2}^{p}\right)^{2}}$$

---

## Linear Classifier

$$f(x, W)=W x + b$$

If the image x is 32x32x3 and will be converted to 3072x1. So W will be 10x3072 and b will be 10x1

- Hard cases for the linear classifier

    ![Lecture%202%20Image%20Classification%209b5aacfdedd54d26ba5e4bcb2fc9efa6/Untitled%201.png](Lecture%202%20Image%20Classification%209b5aacfdedd54d26ba5e4bcb2fc9efa6/Untitled%201.png)