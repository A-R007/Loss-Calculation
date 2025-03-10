# Loss-Calculation

# Weight Update Using Backpropagation

This README explains how to update the weights of a single neuron after one step of backpropagation.

## Given Data
- **Inputs**: \( x = [1,2] \)
- **Initial Weights**: \( W = [0.4, -0.2] \)
- **Bias**: \( b = 0.1 \)
- **Predicted Output**: \( y' = 0.6 \)
- **True Output**: \( y = 0.8 \)
- **Learning Rate**: \( \eta = 0.1 \)
- **Loss Function**: Mean Squared Error (MSE)
- **Derivative of Activation Function**: \( y'(1 - y') = 0.24 \)

---

## Step-by-Step Calculation

### 1. Error Calculation
The error is computed as:
\[
\text{Error} = y - y' = 0.8 - 0.6 = 0.2
\]

### 2. Gradient of Loss with Respect to Output
Using the Mean Squared Error (MSE) loss function:
\[
L = \frac{1}{2} (y - y')^2
\]
The derivative of the loss function with respect to the output \( y' \) is:
\[
\frac{\partial L}{\partial y'} = (y' - y) = 0.6 - 0.8 = -0.2
\]

### 3. Gradient of Loss with Respect to Weights
Using the chain rule:
\[
\frac{\partial L}{\partial W_i} = \frac{\partial L}{\partial y'} \times \frac{\partial y'}{\partial W_i}
\]
Since:
\[
\frac{\partial y'}{\partial W_i} = x_i \times y'(1 - y')
\]

Now, calculating for each weight:

- **For \( W_1 \) (corresponding to \( x_1 = 1 \))**:
\[
\frac{\partial L}{\partial W_1} = (-0.2) \times (0.24) \times (1) = -0.048
\]

- **For \( W_2 \) (corresponding to \( x_2 = 2 \))**:
\[
\frac{\partial L}{\partial W_2} = (-0.2) \times (0.24) \times (2) = -0.096
\]

### 4. Weight Updates
Using the learning rate \( \eta = 0.1 \):
\[
W_i = W_i - \eta \times \frac{\partial L}{\partial W_i}
\]

Updating each weight:

- **Updated \( W_1 \)**:
\[
W_1 = 0.4 - 0.1 \times (-0.048) = 0.4 + 0.0048 = 0.4048
\]

- **Updated \( W_2 \)**:
\[
W_2 = -0.2 - 0.1 \times (-0.096) = -0.2 + 0.0096 = -0.1904
\]

### 5. Final Answer - Updated Weights
\[
W = [0.4048, -0.1904]
\]

These are the updated weights after one backpropagation step.

---

## Notes
- The bias was not updated in this step, but a similar process can be applied.
- The learning rate (\( \eta \)) controls how much the weights change in each step.
- This process is repeated for multiple iterations to train the neuron effectively.

If you have any questions, feel free to ask! 🚀

