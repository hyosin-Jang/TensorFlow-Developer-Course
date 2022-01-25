## rock, paper, and scissors

it's one of the things that's really exciting about the image data generator is how your images get automatically labeled based on the directories that they're in.

## File directory for multiclass classifications

![Untitled (47)](https://user-images.githubusercontent.com/71035113/150999686-6e6de457-4f66-4e5b-af76-e388037072a2.png)

## multi-class with Rock Paper Scissors dataset

- it consists of about 3,000 images.
- They've all been generated using CGI with a diverse array of models, male and female, and lots of different skin tones, and here's some examples.
- For multiple classes, you'll have to change binary to categorical like this.
- The next change comes in your model definition where you'll need to change the output layer.
    - it's activated by softmax which turns all the values into probabilities that will sum up to one.

![Untitled (48)](https://user-images.githubusercontent.com/71035113/150999695-77a852a1-a0a0-48fb-96ab-a7aaa34f6a3c.png)

- The final change then comes when you compile your network. If you recall with the earlier examples, your loss function was binary cross entropy.
- Now, you'll change it's a categorical cross entropy like this

## Test the Rock Paper Scissors classifier

```python
import numpy as np
from google.colab import files
from keras.preprocessing import image

uploaded = files.upload()

for fn in uploaded.keys():
 
  # predicting images
  path = fn
  img = image.load_img(path, target_size=(150, 150))
  x = image.img_to_array(img)
  x = np.expand_dims(x, axis=0)

  images = np.vstack([x])
  classes = model.predict(images, batch_size=10)
  print(fn)
  print(classes)
```

- neurons are in the order paper then rock then scissors because it's alphabetical.
- Result

```python
[[0. 0. 1.]] # rock, paper, scissors
```
