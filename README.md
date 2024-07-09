# Neural Network Traffic Project
In this project, I am going to create an AI that identifies which traffic sign appears in a photograph. Then, I will be using the results to investigate various hyperparamters of the neural network model I created. Throughout the investigation, I will note down any observations and possible reasons on why certain values in the specific hyperparamter will perform better than the other. 

# Background
As research continues in the development of self-driving cars, one of the key challenges is computer vision, allowing these cars to develop an understanding of their environment from digital images. In particular, this involves the ability to recognize and distinguish road signs – stop signs, speed limit signs, yield signs, and more.

In this project, I'll be using the [German Traffic Sign Recognition Benchmark (GTSRB) dataset](http://benchmark.ini.rub.de/?section=gtsrb&subsection=news), which contains thousands of images of 43 different kinds of road signs.

# Example Output
```
$ python traffic.py gtsrb
Epoch 1/10
500/500 [==============================] - 5s 9ms/step - loss: 3.7139 - accuracy: 0.1545
Epoch 2/10
500/500 [==============================] - 6s 11ms/step - loss: 2.0086 - accuracy: 0.4082
Epoch 3/10
500/500 [==============================] - 6s 12ms/step - loss: 1.3055 - accuracy: 0.5917
Epoch 4/10
500/500 [==============================] - 5s 11ms/step - loss: 0.9181 - accuracy: 0.7171
Epoch 5/10
500/500 [==============================] - 7s 13ms/step - loss: 0.6560 - accuracy: 0.7974
Epoch 6/10
500/500 [==============================] - 9s 18ms/step - loss: 0.5078 - accuracy: 0.8470
Epoch 7/10
500/500 [==============================] - 9s 18ms/step - loss: 0.4216 - accuracy: 0.8754
Epoch 8/10
500/500 [==============================] - 10s 20ms/step - loss: 0.3526 - accuracy: 0.8946
Epoch 9/10
500/500 [==============================] - 10s 21ms/step - loss: 0.3016 - accuracy: 0.9086
Epoch 10/10
500/500 [==============================] - 10s 20ms/step - loss: 0.2497 - accuracy: 0.9256
333/333 - 5s - loss: 0.1616 - accuracy: 0.9535
```

# Test Results Report 

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
