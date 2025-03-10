# CH-1 QN1

# Backpropagation Weight Update for a Single Neuron

## Given Data:
- **Inputs**: \( x = [1,2] \)
- **Weights**: \( W = [0.4, -0.2] \)
- **Bias**: \( b = 0.1 \)
- **Predicted Output**: \( y' = 0.6 \)
- **True Output**: \( y = 0.8 \)
- **Learning Rate**: \( \eta = 0.1 \)
- **Activation Function Derivative**: \( y' (1 - y') = 0.24 \)
- **Loss Function**: Mean Squared Error (MSE)

## 1. Error Calculation
The error is the difference between the true output \( y \) and the predicted output \( y' \):

\[
\text{Error} = y - y' = 0.8 - 0.6 = 0.2
\]

## 2. Gradient of Loss with Respect to Output
The MSE loss function is:

\[
L = \frac{1}{2} (y - y')^2
\]

The derivative of the loss function with respect to the output \( y' \) is:

\[
\frac{\partial L}{\partial y'} = (y' - y) = 0.6 - 0.8 = -0.2
\]

## 3. Gradient of Loss with Respect to Weights
Using the chain rule:

\[
\frac{\partial L}{\partial W_i} = \frac{\partial L}{\partial y'} \times \frac{\partial y'}{\partial W_i}
\]

Since:

\[
\frac{\partial y'}{\partial W_i} = x_i \times y' (1 - y')
\]

Now, calculating for each weight:

### For \( W_1 \) (corresponding to \( x_1 = 1 \)):

\[
\frac{\partial L}{\partial W_1} = (-0.2) \times (0.24) \times (1) = -0.048
\]

### For \( W_2 \) (corresponding to \( x_2 = 2 \)):

\[
\frac{\partial L}{\partial W_2} = (-0.2) \times (0.24) \times (2) = -0.096
\]

## 4. Weight Updates
Using the weight update formula:

\[
W_i = W_i - \eta \times \frac{\partial L}{\partial W_i}
\]

### Updated Weights:
- **For \( W_1 \)**:

\[
W_1 = 0.4 - 0.1 \times (-0.048) = 0.4 + 0.0048 = 0.4048
\]

- **For \( W_2 \)**:

\[
W_2 = -0.2 - 0.1 \times (-0.096) = -0.2 + 0.0096 = -0.1904
\]

## 5. Final Answer - Updated Weights:
\[
W = [0.4048, -0.1904]
\]

##QN3

## Compute the Final Probability using Sigmoid Activation Function

Given data:
- Input temperature (\(x\)) = 2°C
- Learned weight (\(w\)) = 0.5 (influence of temperature on decision)
- Bias (\(b\)) = 1 (accounts for external factors like time of day or user preferences)

### Step-by-Step Calculation

**1. Compute \( z \):**



\[ z = wx + b \]



Substitute the values:



\[ z = (0.5 \times 2) + 1 \]




\[ z = 1 + 1 = 2 \]



**2. Apply the Sigmoid Function:**

The formula for the sigmoid function is:



\[ \sigma(z) = \frac{1}{1 + e^{-z}} \]



Substitute \( z = 2 \):



\[ \sigma(2) = \frac{1}{1 + e^{-2}} \]



**3. Calculate the Final Probability:**



\[ \sigma(2) \approx \frac{1}{1 + 0.1353} \]




\[ \sigma(2) \approx \frac{1}{1.1353} \]




\[ \sigma(2) \approx 0.8808 \]



### Final Result

The final probability of the thermostat turning on is approximately **0.8808** (or 88.08%).

**Justification:** The sigmoid activation function converts the linear combination of the input temperature, weight, and bias into a probability value between 0 and 1. In this case, given the input temperature of 2°C, the learned weight of 0.5, and the bias of 1, the model predicts a high probability (approximately 88.08%) of the thermostat turning on.
