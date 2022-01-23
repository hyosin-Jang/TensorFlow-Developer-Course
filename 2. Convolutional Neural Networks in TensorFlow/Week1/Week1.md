# Kaggle의 dogs and cats dataset

### The good things with a lager dataset than a smaller dataset

- One of the things that working with a larger dataset, then helps with is over-fitting.
- So with a smaller dataset, you are at great risk of overfitting

### A method dealing with overfitting

- data augmentation
    - rotation
    - skewing
    - flipping
    - moving it around the frame
    

👉 This is all done as part of TensorFlow’s Image Generation libraries!

### Training with the cats vs. dogs dataset

1. Download the set of images
    - training images - 2,000장
    - testing images - 1,000장
2. Access to the underlying operating system of the VM
    - This code will unzip the cats and dogs data that you just downloaded, into the /tmp directory.
3. Set up directories as variables
    - We can point the generators at them
    - We can pass them to the os.list to take the files from those directories.
4. Visualize the data using `Matplotlib` libraries
5. Build neural network
6. Compile model
    - Defining the loss function and the optimizer
    - Set up the two generators pointing at two directories, training and validation sub-directories
7. Training model with `model.fit generator`

### Q. Why is the validation accuracy a better indicator of model performance than training accuracy?

A) The validation accuracy is based on images that the model hasn't been trained with, and thus a better indicator of how the model will perform with new images.
