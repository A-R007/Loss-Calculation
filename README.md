# CH-1 QN1

## Backpropagation Weight Update for a Single Neuron

### Given Data:
- **Inputs**: \( x = [1,2] \)
- **Weights**: \( W = [0.4, -0.2] \)
- **Bias**: \( b = 0.1 \)
- **Predicted Output**: \( y' = 0.6 \)
- **True Output**: \( y = 0.8 \)
- **Learning Rate**: \( \eta = 0.1 \)
- **Activation Function Derivative**: \( y'(1 - y') = 0.24 \)
- **Loss Function**: Mean Squared Error (MSE)

### 1. Error Calculation
The error is the difference between the true output \( y \) and the predicted output \( y' \):

$$
\text{Error} = y - y' = 0.8 - 0.6 = 0.2
$$

### 2. Gradient of Loss with Respect to Output
The MSE loss function is:

$$
L = \frac{1}{2} (y - y')^2
$$

The derivative of the loss function with respect to the output \( y' \) is:

$$
\frac{\partial L}{\partial y'} = (y' - y) = 0.6 - 0.8 = -0.2
$$

### 3. Gradient of Loss with Respect to Weights
Using the chain rule:

$$
\frac{\partial L}{\partial W_i} = \frac{\partial L}{\partial y'} \times \frac{\partial y'}{\partial W_i}
$$

Since:

$$
\frac{\partial y'}{\partial W_i} = x_i \times y'(1 - y')
$$

Now, calculating for each weight:

#### For \( W_1 \) (corresponding to \( x_1 = 1 \)):

$$
\frac{\partial L}{\partial W_1} = (-0.2) \times (0.24) \times (1) = -0.048
$$

#### For \( W_2 \) (corresponding to \( x_2 = 2 \)):

$$
\frac{\partial L}{\partial W_2} = (-0.2) \times (0.24) \times (2) = -0.096
$$

### 4. Weight Updates
Using the weight update formula:

$$
W_i = W_i - \eta \times \frac{\partial L}{\partial W_i}
$$

#### Updated Weights:
- **For \( W_1 \)**:

$$
W_1 = 0.4 - 0.1 \times (-0.048) = 0.4 + 0.0048 = 0.4048
$$

- **For \( W_2 \)**:

$$
W_2 = -0.2 - 0.1 \times (-0.096) = -0.2 + 0.0096 = -0.1904
$$

### 5. Final Answer - Updated Weights:

$$
W = [0.4048, -0.1904]
$$

---

# CH-1 QN3

## Compute the Final Probability using Sigmoid Activation Function

### Given Data:
- **Input Temperature** \( x = 2^\circ C \)
- **Learned Weight** \( w = 0.5 \) (influence of temperature on decision)
- **Bias** \( b = 1 \) (accounts for external factors like time of day or user preferences)

### Step-by-Step Calculation

#### 1. Compute \( z \):

$$
z = wx + b
$$

Substituting the values:

$$
z = (0.5 \times 2) + 1
$$

$$
z = 1 + 1 = 2
$$

#### 2. Apply the Sigmoid Function:

The formula for the sigmoid function is:

$$
\sigma(z) = \frac{1}{1 + e^{-z}}
$$

Substituting \( z = 2 \):

$$
\sigma(2) = \frac{1}{1 + e^{-2}}
$$

#### 3. Calculate the Final Probability:

Approximating \( e^{-2} \approx 0.1353 \):

$$
\sigma(2) = \frac{1}{1 + 0.1353}
$$

$$
\sigma(2) = \frac{1}{1.1353}
$$

$$
\sigma(2) \approx 0.8808
$$

### Final Result

The final probability of the thermostat turning on is **0.8808** (or **88.08%**).

**Justification:** The sigmoid activation function converts the linear combination of the input temperature, weight, and bias into a probability value between 0 and 1. In this case, given the input temperature of 2°C, the learned weight of 0.5, and the bias of 1, the model predicts a high probability (**88.08%**) of the thermostat turning on.

# CH-1 QN5

## Backpropagation Calculation for Hidden and Output Layers

### Given Data:
- **Inputs:**
  - \( x_1 = 0.10 \), \( x_2 = 0.35 \)
- **Weights:**
  - Input to Hidden Layer:
    - \( w_1 = 0.15 \), \( w_2 = 0.25 \) (for \( H1 \))
    - \( w_3 = 0.30 \), \( w_4 = 0.35 \) (for \( H2 \))
  - Hidden to Output Layer:
    - \( w_5 = 0.40 \), \( w_6 = 0.45 \) (for \( y_1 \))
    - \( w_7 = 0.50 \), \( w_8 = 0.55 \) (for \( y_2 \))
- **Bias Values:**
  - Hidden Layer: \( b_1 = 0.60 \), \( b_2 = 0.60 \)
- **Target Values:**
  - \( T_1 = 0.01 \), \( T_2 = 0.99 \)

### 1. Compute Hidden Layer Activations

For each hidden unit:

#### Hidden Neuron \( H1 \):

$$ z_{H1} = (x_1 \times w_1) + (x_2 \times w_2) + b_1 $$

$$ z_{H1} = (0.10 \times 0.15) + (0.35 \times 0.25) + 0.60 $$

$$ z_{H1} = 0.015 + 0.0875 + 0.60 = 0.7025 $$

Applying the sigmoid activation function:

$$ H1 = \sigma(0.7025) = \frac{1}{1 + e^{-0.7025}} \approx 0.6687 $$

#### Hidden Neuron \( H2 \):

$$ z_{H2} = (x_1 \times w_3) + (x_2 \times w_4) + b_2 $$

$$ z_{H2} = (0.10 \times 0.30) + (0.35 \times 0.35) + 0.60 $$

$$ z_{H2} = 0.03 + 0.1225 + 0.60 = 0.7525 $$

Applying the sigmoid activation function:

$$ H2 = \sigma(0.7525) = \frac{1}{1 + e^{-0.7525}} \approx 0.6797 $$

### 2. Compute Output Layer Activations

For each output neuron:

#### Output Neuron \( y_1 \):

$$ z_{y1} = (H1 \times w_5) + (H2 \times w_6) $$

$$ z_{y1} = (0.6687 \times 0.40) + (0.6797 \times 0.45) $$

$$ z_{y1} = 0.2675 + 0.3059 = 0.5734 $$

Applying the sigmoid activation function:

$$ y_1 = \sigma(0.5734) = \frac{1}{1 + e^{-0.5734}} \approx 0.6395 $$

#### Output Neuron \( y_2 \):

$$ z_{y2} = (H1 \times w_7) + (H2 \times w_8) $$

$$ z_{y2} = (0.6687 \times 0.50) + (0.6797 \times 0.55) $$

$$ z_{y2} = 0.3343 + 0.3738 = 0.7081 $$

Applying the sigmoid activation function:

$$ y_2 = \sigma(0.7081) = \frac{1}{1 + e^{-0.7081}} \approx 0.6699 $$

### 3. Final Values
- **Hidden Layer Outputs:**
  - \( H1 \approx 0.6687 \)
  - \( H2 \approx 0.6797 \)
- **Output Layer Predictions:**
  - \( y_1 \approx 0.6395 \)
  - \( y_2 \approx 0.6699 \)

These values can now be used for error calculation and backpropagation adjustments.


