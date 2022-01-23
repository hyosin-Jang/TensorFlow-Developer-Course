### Understanding ImageGenerator

- When you put sub-directories in these for horses and humans and store the requisite images in there, 
the image generator can create a feeder for those images and auto label them for you.
- The names of the sub-directories will be the labels for your images that are contained within them
- the input data all has to be the same size, so the images will need to be resized to make them consistent.
- The nice thing about this code is that the images are resized for you as they're loaded. So you don't need to preprocess thousands of images on your file system.


### Training the ConvNet with fit_generator

1. 다중분류할 때 loss function ⇒ categorical_crossentropy
2. 이진분류할 때 loss function ⇒  binary_crossentropy
3. RMSprop ⇒ you can adjust the learning rate to experiment with performance.
4. model.fit 대신 model.fit_generator 사용
    - 첫 번째 파라미터: training generator. 
    - batch: 한 번에 다룰 이미지 수
    - step: 한 배치씩 반복할 횟수
    - ex. 256개의 이미지가 있고, batch_size가 32라면 8 step임 
5. verbose: It specifies how much to display while training is going on.


### 300x300을 150x150으로 줄이면 발생하는 일

- When we use 300 by 300 before and more convolutions, she was correctly classified. But now, she isn't. 
- This is a great example of the importance of measuring your training data against a large validation set, inspecting where it got it wrong and seeing what you can do to fix it.
