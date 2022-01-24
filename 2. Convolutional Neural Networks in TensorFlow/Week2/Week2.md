## Image Augmentation

- if you're dealing with a dataset and you want to experiment with different augmentations, you're not overriding the data.
- generate a library lets you load it into memory and just in memory, process the images and then stream that to the training set to the neural network we'll ultimately learn on.

[Click for more details]([https://github.com/keras-team/keras-preprocessing](https://github.com/keras-team/keras-preprocessing))

### When we have a small dataset, we can have some mistakes in our classification

- when the dataset is small, we have relatively few examples and as a result, we can have some mistakes in our classification. ⇒ overfitting’

### The reason why we do augmentation

- So if the network was never trained for an image of a cat reclining like this, it may not recognize it.
- If you don't have the data for a cat reclining, then you could end up in an overfitting situation.
- But if your images are fed into the training with augmentation such as a rotation, the feature might then be spotted, even if you don't have a cat reclining, your upright cat when rotated, could end up looking the same.

[Keras - Image data preprocessing API (Link)](https://keras.io/preprocessing/image)

### ImageDataGenerator Parameters

![Untitled (36)](https://user-images.githubusercontent.com/71035113/150721041-3906910d-ccf3-4ae5-be8e-e65e15225032.png)

- `rescale`: That saved you from converting all of your images on the file system and then loading them in, you just re-scaled on the fly
- `rotation_range`: Rotation range is a range from 0-180 degrees with which to randomly rotate images
- `shifting`: Shifting, moves the image around inside its frame. Many pictures have the subject centered. So if we train based on those kind of images, we might over-fit for that scenario. These parameters specify, as a proportion of the image size, how much we should randomly move the subject around.
- `shearing(전단)`: It will shear the image by random amounts up to the specified portion in the image.
- `zoom`: if we zoom while training, we could spot more generalized examples.
- `horizontal_flip`: 수평 방향으로 랜덤하게 뒤집는 것. 오른손을 들고 있는 사람의 사진이 training dataset에 있고, 왼손을 들고 있는 사람의 사진이 test dataset에 있는 경우 horizontal_flip=True를 주는게 더 잘 훈련된 모델임
- `fill_mode`: This fills in any pixels that might have been lost by the operations.
    - `nearest`: It uses neighbors of that pixel to try and keep uniformity.

### Why we must also do image augmentation for testing dataset

- the image augmentation introduces a random element to the training images but if the validation set doesn't have the same randomness, then its results can fluctuate like this.
- So bear in mind that you don't just need a broad set of images for training, you also need them for `testing` or the image augmentation won't help you very much.
- 트레이닝 데이터셋만 image augmentation을 하게 되면, training 정확도는 100%에 가깝게 잘 나와도 validation 정확도는 60-70%이 나왔음
- validation dataset이 트레이닝 데이터셋과 같은 randomness를 가지고 있지 않으면 이와 같은 결과가 나오게 됨

### Q. **When training with augmentation, you noticed that the training is a little slower. Why?**

A) **Because the image processing takes cycles**
