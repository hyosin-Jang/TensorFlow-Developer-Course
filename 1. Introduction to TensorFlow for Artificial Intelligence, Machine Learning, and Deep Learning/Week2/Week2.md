# Week2.

## Computer vision

- Computer vision is the field of having a computer understand and label what is present in an image

## 컴퓨터가 recognize하는 방법

- So one way to solve that is to use lots of pictures of clothing and tell the computer what that's a picture of and then have the computer figure out the patterns that give you the difference between a shoe, and a shirt, and a handbag, and a coat.

## MNIST Fashion 데이터셋

- 70 thousand images spread across 10 different items of clothing.
- These images have been scaled down to 28 by 28 pixels.
- Now usually, **the smaller the better** because the computer has less processing to do
- grey scale image
- Each pixel can be represented in values from **zero to 255** and one byte per pixel.

## Exploring how to use data

We will learn how to...

- load data
- prepare it for training

## Writing code to load training data

- MNIST API 있어서 Keras에서 loading해서 쓸 수 있음
- Return ⇒ training data, the training labels, the testing data, and the testing labels
- So in the Fashion-MNIST data set, 60,000 of the 70,000 images are used to train the network, and then 10,000 images, one that it hasn't previously seen
- 전체 7만 개 중 훈련용 6만 개, 테스트용 1만 개

## label을 숫자로 하는 이유

- Reason 1. First, of course, is that computers do better with numbers than they do with texts.
- Reason 2. Second, importantly, is that this is something that can help us reduce bias.

## Coding a Computer Vision Neural Network

![Untitled (34)](https://user-images.githubusercontent.com/71035113/150184899-66e9e9c4-e0b4-4668-9151-a50d9fce52aa.png)

- We have three layers
- The first layer is a flatten layer with the input shaping 28 by 28
    - Flatten takes this 28 by 28 square and turns it into a simple linear array.
- The last layer has 10 neurons in it because we have ten classes of clothing in the dataset.

## Walk through a Notebook for computer vision

- The data for a particular image is a grid of values from zero to 255 with pixel Grayscale values
- Our image has values from zero to 255, but neural networks work better with normalized data. ⇒ 255로 나눠서 normalize함
- layer 설명
    - input layer ➡️ in the shape of the data
    - an output layer ➡️ in the shape of the classes,
    - one hidden layer ➡️ that tries to figure out the roles between them
- Now we compile the model to finding the loss function and the optimizer
    - 컴파일하는 이유: To make a guess as to what the relationship is between the input data and the output data
- We can then try to fit the training images to the training labels
- TODO: Your job now is to go through the workbook, try the exercises and see by tweaking the parameters on the neural network or changing the epochs. loss를 0.71보다 작게 만들기
