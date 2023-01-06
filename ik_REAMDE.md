## Initial idea

One of the ideas was to use [YOLOv7](https://github.com/WongKinYiu/yolov7) model. This model can find objects on images and videos and classify them with high accuracy. But later we decided that such model won't fit to our task, as we do not need to find the object on an image, but rather to classify the whole image.

---

## The dataset

Ideally, we would gather a lot of images with different fill levels over a long period of time (around 6 months). But as we do not have that much time, we had to make an imitation of a real dataset. So we took around 200 photos of a bag filled with pellet. If our model proves to be working we can gather a larger amount of data over a longer period of time and use if with the model.

The dataset was split to 101 classes, which represent fill levels between 0 and 100%:

- Train - 70% (145 images) <br>
- Validation - 20% (41 images) <br>
- Test - 10% (20 images) <br>

The images were grayscaled and rescaled to 64x64px.

---

## Model, that didn't work

Model used [Keras](https://keras.io/)

Model code part:

```python
model = Sequential()
model.add(Conv2D(32, (2, 2), input_shape=input_shape))
model.add(Activation('relu'))
model.add(MaxPooling2D(pool_size=(2, 2)))

model.add(Conv2D(32, (2, 2)))
model.add(Activation('relu'))
model.add(MaxPooling2D(pool_size=(2, 2)))

model.add(Conv2D(64, (2, 2)))
model.add(Activation('relu'))
model.add(MaxPooling2D(pool_size=(2, 2)))

model.add(Flatten())
model.add(Dense(64))
model.add(Activation('relu'))
model.add(Dropout(0.5))
model.add(Dense(1))
model.add(Activation('sigmoid'))
```

This model showed **>1%** accuracy during training so it was considered to be non-fitting for out task. Maybe, this model could fit for tasks with binary classification.
