
Use in https://latexeditor.lagrida.com to generate expressions in Latex Format

**Given Data:**
X_1 = [1, 2, 3]\\
X_2 = [2, 3, 7]\\
Y_{\text{true}} = [3, 5, 10]\\

**Neural Network Architecture: Simple perceptron with only one neuron
- Input Layer: Two nodes (corresponding to \(X_1\) and \(X_2\))
- Output Layer: One node (corresponding to \(Y\))


**Initialization:**

Learning\ rate\ \alpha = 0.10\\
Activation function : Sigmoid\ \sigma(Z)=1/(1+e^{-Z})\\
Weights\ and\ Bias
W_1 = 0.5\\
W_2 = -0.5\\
b = 0.2\\

**Forward Pass:**

1. **Calculate \(Z\) and \(Y_{\text{pred}}\) for each data point:**
   For\ X_1 = 1, X_2 = 2\ and \ Y_{\text{true}_1} =3:\\
Z_1 = W_1 \times X_1 + W_2 \times X_2 + b\\
Z_1 = W_1 \times 1 + W_2 \times 2 + b = 0.5 \times 1 + (-0.5) \times 2 + 0.2 = -0.3 \\
Y_{\text{pred}_1} = \sigma(Z_1) = \sigma(-0.3) = 0.425 \\ 
\\

For\ X_1 = 2, X_2 = 3\ and \ Y_{\text{true}_2} =7:\\
Z_2 = W_1 \times X_1 + W_2 \times X_2 + b\\
Z_2 = W_1 \times 2 + W_2 \times 3 + b = 0.5 \times 2 + (-0.5) \times 3 + 0.2 = -0.3 \\
Y_{\text{pred}_2} = \sigma(Z_2) = \sigma(-0.3) = 0.425 \\
\\
For\ X_1 = 3, X_2 = 7\ and \ Y_{\text{true}_3} =10:\\
Z_3 = W_1 \times X_1 + W_2 \times X_2 + b\\
Z_3 = W_1 \times 3 + W_2 \times 7 + b = 0.5 \times 3 + (-0.5) \times 7 + 0.2 = -1.8 \\
Y_{\text{pred}_3} = \sigma(Z_3) = \sigma(-1.8) = 0.142

**Calculate MSE Loss:**
MSE = (1/2\ n) \sum_{1}^{n}(Y_{\text{pred}}-Y_{\text{true}})^{2} :\\

MSE =(1/ (2 \times 3))\times[((Y_{\text{pred}_1}-Y_{\text{true}_1})^{2})+((Y_{\text{pred}_2}-Y_{\text{true}_2})^{2})+((Y_{\text{pred}_3}-Y_{\text{true}_3})^{2})]\\
1/6 \times [(0.425-3)^{2}+(0.425-5)^{2}+(0.142-10)^{2})]=20.79



**Backpropagation - Calculate Gradients:**

Recall : 
Z= W_1 \times X_1 + W_2 \times X_2 + b\\
Y_{\text{pred}} = \sigma(Z) =1/(1+e^{-Z})\\
MSE = (1/2\ n) \sum_{1}^{n}(Y_{\text{pred}}-Y_{\text{true}})^{2} :\\

For\ the\ parameter\ p = W_1, W_2\ or\ b : \\

∂MSE/∂p = (∂MSE/∂Y_{\text{pred}}) \times (∂Y_{\text{pred}}/∂Z) \times (∂Z/∂p) \\

\\ General expressions 
1.\\(∂MSE/∂Y_{\text{pred}}) = ∂[(1/2n) \sum_{1}^{n}(Y_{\text{pred}}-Y_{\text{true}})^{2}]/∂Y_{\text{pred}} = (1/n) \times \sum_{1}^{n}(Y_{\text{pred}}-Y_{\text{true}})\\
2.\\
(∂Y_{\text{pred}}/∂Z)=∂\sigma(Z)/∂Z=∂((1/(1+e^{-Z})))/∂Z\\
=e^{-Z} \times (1+e^{-Z})^{-2}=(1/(1+e^{-Z})) \times (1-(1/(1+e^{-Z})))\\
=\sigma(Z) \times (1-\sigma(Z))=Y_{\text{pred}}(1-Y_{\text{pred}})\\
3.\\
(∂Z/W_{1})=∂(W_1 \times X_1 + W_2 \times X_2 + b)/∂W1=X_{1}\\
(∂Z/W_{2})=∂(W_1 \times X_1 + W_2 \times X_2 + b)/∂W2=X_{2}\\
(∂Z/b)=∂(W_1 \times X_1 + W_2 \times X_2 + b)/∂b=1\\


∂MSE/∂W_{1} =(1/n)\sum_{1}^{n}  (Y_{pred}-Y_{true}) \times Y_{pred} \times (1-Y_{pred}) \times X_1 \\
∂MSE/∂W_{2}=(1/n)\sum_{1}^{n} \ (Y_{pred}-Y_{true}) \times Y_{pred} \times (1-Y_{pred}) \times X_2 \\
∂MSE/∂b =(1/n)\sum_{1}^{n} \ (Y_{pred}-Y_{true}) \times Y_{pred} \times (1-Y_{pred}) \times 1 \\ \\ 

Calculation
For\ W1 :\\
∂MSE/∂W_{1} =(1/n)\sum_{1}^{n}  (Y_{pred}-Y_{true}) \times Y_{pred} \times (1-Y_{pred}) \times X_1 \\


(Y_{pred}-Y_{true}) \times Y_{pred} \times (1-Y_{pred}) \times X_1\\


For\ X_1 = 1, X_2 = 2\ and \ Y_{\text{true}_1} =3: (0.425-3) \times 0.425 \times (1-0.425) \times 1=-0.629\\


For\ X_1 = 2, X_2 = 3\ and \ Y_{\text{true}_1} =5:(0.425-5) \times 0.425 \times (1-0.425) \times 2=-2.236  \\


For\ X_1 = 3, X_2 = 7\ and \ Y_{\text{true}_1} =10:(0.142-10) \times 0.142 \times (1-0.142) \times 3 = -3.603 \\
∂MSE/∂W_{1}=(1/3) \times (-0.629-2.236-3.603)=-2.156\\
\\

2.\\
For\ W2 :\\
∂MSE/∂W_{2} =(1/n)\sum_{1}^{n}  (Y_{pred}-Y_{true}) \times Y_{pred} \times (1-Y_{pred}) \times X_2 \\

(Y_{pred}-Y_{true}) \times Y_{pred} \times (1-Y_{pred}) \times X_2\\


For\ X_1 = 1, X_2 = 2\ and \ Y_{\text{true}_1} =3: (0.425-3) \times 0.425 \times (1-0.425) \times 2=-1.258\\


For\ X_1 = 2, X_2 = 3\ and \ Y_{\text{true}_1} =5:(0.425-5) \times 0.425 \times (1-0.425) \times 3=-3.354  \\


For\ X_1 = 3, X_2 = 7\ and \ Y_{\text{true}_1} =10:(0.142-10) \times 0.142 \times (1-0.142) \times 7 = -8.407 \\
∂MSE/∂W_{2}=(1/3)\times(-1.258-3.354-8.407)=-4.339\\
\\
3.\\
For\ b :\\
∂MSE/∂b =(1/n)\sum_{1}^{n}  (Y_{pred}-Y_{true}) \times Y_{pred} \times (1-Y_{pred}) \times 1 \\

(Y_{pred}-Y_{true}) \times Y_{pred} \times (1-Y_{pred}) \times 1\\


For\ X_1 = 1, X_2 = 2\ and \ Y_{\text{true}_1} =3: (0.425-3) \times 0.425 \times (1-0.425) \times 1=-0.629\\


For\ X_1 = 2, X_2 = 3\ and \ Y_{\text{true}_1} =5:(0.425-5) \times 0.425 \times (1-0.425) \times 1=-1.118  \\


For\ X_1 = 3, X_2 = 7\ and \ Y_{\text{true}_1} =10:(0.142-10) \times 0.142 \times (1-0.142) \times 1 = -1.201 \\
∂MSE/∂b=(1/3)\times(-0.629-1.118-1.201)=-0.982\\
\\



**Update Parameters Using Gradient Descent:**

W_{1}= W_{1}−α \times ∂MSE/∂W_{1} = 0.5-0.1 \times (-2.156)=0.7156\\
W_{2}= W_{2}−α \times ∂MSE/∂W_{2}= -0.5-0.1 \times (-4.339)=-0.066\\
b= b-α \times ∂MSE/∂b = 0.2-0.1 \times (-0.982)=0.2982\\ \\
