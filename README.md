# README

## Introduction

This README file presents the results of investigating various hyperparameters of a neural network model. The parameters studied include the number of convolutional and pooling layers, pool sizes, filter sizes, the number of filters, hidden layer sizes, the number of hidden layers, and dropout rates. 

The default values used for the study are:
1. 2 convolutional and 2 pooling layers
2. 2x2 pool size
3. 3x3 filter size
4. 32 filters
5. 128 size of hidden layer
6. 1 hidden layer
7. 0.5 dropout value

## Results

### 1. Number of Convolutional and Pooling Layers

| Configuration                       | Accuracy | Loss   |
|-------------------------------------|----------|--------|
| 1 convolutional and 1 pooling layer | 0.0581   | 3.4950 |
| 2 convolutional and 2 pooling layers| 0.9351   | 0.1140 | (default)
| 3 convolutional and 3 pooling layers| 0.9617   | 0.1531 |

**Observations:**
- Increasing the number of convolutional and pooling layers improves accuracy and reduces loss up to a point.
- The model with 3 convolutional and 3 pooling layers achieves the highest accuracy but slightly higher loss compared to the default.
- Adding more layers allows the network to learn more complex features. However, after a certain point, it can lead to overfitting, which can explain the slight increase in loss.

### 2. Pool Size of Pooling Layer

| Pool Size | Accuracy | Loss   |
|-----------|----------|--------|
| 2x2       | 0.9351   | 0.1140 | (default)
| 3x3       | 0.9200   | 0.2777 |
| 4x4       | 0.1326   | 3.1009 |

**Observations:**
- The default 2x2 pool size provides the best accuracy and lowest loss.
- Larger pool sizes degrade model performance, due to excessive downsampling, leading to loss of spatial information.

### 3. Filter Size of Convolutional Layer

| Filter Size | Accuracy | Loss   |
|-------------|----------|--------|
| 2x2         | 0.0549   | 3.5023 |
| 3x3         | 0.9351   | 0.1140 | (default)
| 4x4         | 0.9762   | 0.1051 |

**Observations:**
- Larger filter sizes improve accuracy and reduce loss, with 4x4 providing the best performance.
- Smaller filter sizes fail to capture sufficient spatial features, resulting in poor accuracy and high loss.

### 4. Number of Filters in Convolutional Layer

| Number of Filters | Accuracy | Loss   |
|-------------------|----------|--------|
| 15                | 0.9655   | 0.1254 |
| 32 (default)      | 0.9351   | 0.1140 |
| 50                | 0.9763   | 0.0963 |

**Observations:**
- Increasing the number of filters generally improves performance.
- The best results are obtained with 50 filters, offering the highest accuracy and lowest loss.
- More filters allow the network to learn a greater number of features. However, increasing the number of filters also increases the computational cost and risk of overfitting.

### 5. Size of Hidden Layers

| Hidden Layer Size | Accuracy | Loss   |
|-------------------|----------|--------|
| 50                | 0.0521   | 3.5099 |
| 128 (default)     | 0.9351   | 0.1140 |
| 300               | 0.9415   | 0.2250 |

**Observations:**
- The default size of 128 provides a balance of good accuracy and low loss.
- Smaller sizes underperform, while larger sizes do not significantly improve accuracy and increases loss due to overfitting.

### 6. Number of Hidden Layers

| Number of Hidden Layers | Accuracy | Loss   |
|-------------------------|----------|--------|
| 0                       | 0.8730   | 0.4685 |
| 1 (default)             | 0.9351   | 0.1140 |
| 3                       | 0.9512   | 0.2148 |

**Observations:**
- Adding hidden layers improves performance.
- The model with 3 hidden layers achieves the highest accuracy, but with a slight increase in loss, due to overfitting.

### 7. Dropout Rate

| Dropout Rate | Accuracy | Loss   |
|--------------|----------|--------|
| 0.2          | 0.9736   | 0.1089 |
| 0.5 (default)| 0.9351   | 0.1140 |
| 0.8          | 0.0541   | 3.4984 |

**Observations:**
- A lower dropout rate (0.2) improves accuracy and reduces loss, due to better generalization.
- A higher dropout rate (0.8) severely degrades performance, due to excessive regularization and loss of information during training.

## Conclusion

This investigation demonstrates the impact of various hyperparameters on the performance of a neural network model. The results highlight the importance of selecting appropriate values for each parameter to optimize model accuracy and minimize loss. 
