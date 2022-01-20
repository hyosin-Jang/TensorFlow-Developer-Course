So one of the ideas that make these neural networks work much better is to use convolutional neural networks, where instead of looking at every single pixel

## What are convolutions and pooling?

- So, what's convolution? You might ask. Well, if you've ever done any kind of image processing, it usually involves having a filter and passing that filter over the image in order to change the underlying image
- For every pixel, take its value, and take a look at the value of its neighbors. If our filter is three by three, then we can take a look at the immediate neighbor, so that you have a corresponding three by three grid.
- Then to get the new value for the pixel, we simply multiply each neighbor by the corresponding value in the filter.

![Untitled (35)](https://user-images.githubusercontent.com/71035113/150285140-cf36c0c8-8b16-460c-beff-bd569003642f.png)

## Max pooling layer

- It takes the maximum value.
- 만약 필터 사이즈가 2x2라면, 4픽셀마다 가장 큰 값의 픽셀만 살아남음

## models.summary

- This allows you to inspect the layers of the model, and see the journey of the image through the convolutions

## 3x3 픽셀로 28x28의 데이터를 컨볼루션하면 26x26이 되는 이유

- left top 픽셀은 margin이 없으므로 사용할 수 없음. right top도 같은 이유임
- so the output of the convolution will be two pixels smaller on x, and two pixels smaller on y.
- filter가 5x5라면 ouput은 (x-4)x(y-4)
