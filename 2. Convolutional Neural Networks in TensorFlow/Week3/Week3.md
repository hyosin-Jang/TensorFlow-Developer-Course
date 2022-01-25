# Concepts of transfer learning

![Untitled (43)](https://user-images.githubusercontent.com/71035113/150965310-559489f8-42be-441d-932e-ded760c36977.png)

- You can lock them(convolutions) instead of retraining them on your data, and have those just extract the features from your data using the convolutions that they've already learned.
- Then you can take a model that has been trained on a very large datasets and use the convolutions that it learned when classifying its data.
- large dataset을 통해 훈련된 모델의 convolution layer를 사용해 특징을 추출한다.

### Which convolution layers we might lock?

- We can lock all the convolutions.
- We can also choose to retrain some of the lower ones too because they may be too specialized for the images at hand.
- ⇒ It takes some trial and error to discover the right combination.
- 어떤 층을 동결시킬지 정하려면 시행착오를 거쳐야 한다.

### Coding your own model with transferred features

- All of the layers have names, so you can look up the name of the last layer that you want to use.

```python
last_layer = pre_trained_model.get_layer('mixed7')

last_output = last_layer.output

# define out new Dense model
x = layers.Flatten()(last_ouptut)
```

- So now we'll define our new model, taking the output from the inception model's mixed7 layer, which we had called last_ouput.
- You start by flattening the input, which just happens to be the output from inception.
- 인셉션 모델의 마지막 레이어에서 나온 아웃풋을 flatten한 다음 Dense 레이어를 추가한다.

# Dropout

- Here is the graph of the accuracy of training versus validation.
- it started out well, the validation is diverging away from the training in a really bad way.

![Untitled (44)](https://user-images.githubusercontent.com/71035113/150965321-3cbf3ec9-33c0-44fb-b907-c512fa6d9558.png)

- The idea behind Dropouts is that they remove a random number of neurons in your neural network. This works well for two reasons.
    
    1) neighboring neurons often end up with similar weights, which can lead to overfitting, so dropping some out at random can remove this.
    
    2) The second is that often a neuron can over-weigh the input from a neuron in the previous layer, and can over specialize as a result. Thus, dropping out can break the neural network out of this potential bad habit!
    

### Dropout in code

```python
tf.keras.layers.Dropout(
    rate, noise_shape=None, seed=None, **kwargs
)
```

| Args |  |
| --- | --- |
| rate | Float betwen 0-1. Fraction of the input units to drop. |
| noise_shape | 1D integer tensor representing the shape of the binary dropout mask that will be multiplied with the input. For instance, if your inputs have shape (batch_size, timesteps, features) and you want the dropout mask to be the same for all timesteps, you can use noise_shape=(batch_size, 1, features). |
| seed | A Python interger to use as random seed. |

### Impact of the dropout

![Untitled (45)](https://user-images.githubusercontent.com/71035113/150965322-7eb5e80e-ad96-408a-bd02-7effe45c72b8.png)

# code

```python
for layer in pre_trained_model.layers:
  layer.trainable = False
  
# pre_trained_model.summary()

last_layer = pre_trained_model.get_layer('mixed7')
print('last layer output shape: ', last_layer.output_shape)
last_output = last_layer.output
```

- last_output
    
    We will pull one of the convolutional layers as our input layer, and then take its output.
    

# Quiz.

### Q1. Why is transfer learning useful?

A) Because I can use the features that were learned from large datasets that I may not have access to

### Q2. How do you change the number of classes the model can classify when using transfer learning? (i.e. the original model handled 1000 classes, but yours handles just 2)

A) When you add your DNN at the bottom of the network, you specify your output layer with the number of classes you want

### Q3. Can you use Image Augmentation with Transfer Learning Models?

A) Yes, because you are adding new layers at the bottom of the network, and you can use image augmentation when training these

### Q4. What would the symptom of a Dropout rate being set too high?

A) The network would lose specialization to the effect that it would be inefficient or ineffective at learning, driving accuracy down

## Result

![Untitled (46)](https://user-images.githubusercontent.com/71035113/150965326-c3a1c39c-2e12-4e80-af26-12daf8a7d519.png)
