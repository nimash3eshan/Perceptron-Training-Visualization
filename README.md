# SLP Learning Example: The Perceptron Learning Rule (Online)

Let's walk through an online learning iteration for an SLP.

**Dataset Example:** (Assume 3 features x1, x2, x3, and binary output y is 0 or 1)

| **x1** | **x2** | **x3** | **y (target)** |
| --- | --- | --- | --- |
| 1 | 0 | 1 | 0 |
| 0 | 0 | 1 | 1 |
| 1 | 1 | 0 | 0 |
| 0 | 1 | 1 | 1 |
| 1 | 0 | 0 | 0 |
| 0 | 1 | 0 | 1 |

**Network Setup:**

- 3 input neurons + 1 bias neuron.
- 1 output neuron.
- Activation: Heaviside function (φ).
- Learning rate (η - eta): 0.01.

**Initialization:**

- Initialize weights: w1=0.1, w2=0.2, w3=0.1, bias=0.1.

**Training - Iteration 1 (First data point: [1, 0, 1], target y=0)**

1. **Apply Input:** x = [1, 0, 1]. Current weights: w1=0.1, w2=0.2, w3=0.1, bias=0.1.
2. **Calculate Weighted Sum (u):**
    
    ```
    
    u = (x1*w1) + (x2*w2) + (x3*w3) + bias
    u = (1*0.1) + (0*0.2) + (1*0.1) + 0.1
    u = 0.1 + 0 + 0.1 + 0.1 = 0.3
    ```
    
3. **Calculate Output (ŷ):**
    
    ```
    ŷ = φ(u) = Heaviside(0.3)
    Since 0.3 ≥ 0, ŷ = 1
    ```
    
4. **Calculate Error (e):**
    
    ```
    e = y_target - ŷ
    e = 0 - 1 = -1
    ```
    
5. **Update Weights:**
The Perceptron learning rule for a weight w_j connected to input x_j:

For the bias:
    

    w_j_new = w_j_old + η * e * x_j

    bias_new = bias_old + η * e * 1

    
  - w1_new = 0.1 + (0.01 * -1 * 1) = 0.1 - 0.01 = 0.09
  - w2_new = 0.2 + (0.01 * -1 * 0) = 0.2 - 0 = 0.2
  - w3_new = 0.1 + (0.01 * -1 * 1) = 0.1 - 0.01 = 0.09
  - bias_new = 0.1 + (0.01 * -1 * 1) = 0.1 - 0.01 = 0.09

**Updated Weights for Next Iteration:** w1=0.09, w2=0.2, w3=0.09, bias=0.09.

**Training - Iteration 2 (Second data point: [0, 0, 1], target y=1)**

1. **Apply Input:** x = [0, 0, 1]. Weights: w1=0.09, w2=0.2, w3=0.09, bias=0.09.
2. **Calculate u:**
    
    ```
    u = (0*0.09) + (0*0.2) + (1*0.09) + 0.09
    u = 0 + 0 + 0.09 + 0.09 = 0.18
    ```
    
3. **Calculate ŷ:**
    
    ```
    ŷ = Heaviside(0.18) = 1 (since 0.18 ≥ 0)
    ```
    
4. **Calculate Error e:**
    
    ```
    e = y_target - ŷ = 1 - 1 = 0
    ```
    
5. **Update Weights:** Since e = 0, there will be **no change** to the weights.

The network correctly classified this sample, so no learning adjustment is needed for this step.
    
    
    w_new = w_old + η * 0 * x = w_old
    
    

...This process continues for all training samples, for multiple epochs until the perceptron converges or reaches maximum iterations.
