# Group13_AI_Project
AI project of group 13 in the lecture AI at university of applied sciences Bingen. 


## Initial Idea
The idea was to use a ten class model for bundle several fill velues in 10 percent steps to work against small amount of our data.
After trying several out the decission went to a model which worked on the cifar10 dataset from cifar10.
```python 
from keras.datasets import cifar10 
```

## Model snippit:
```python
model.add(keras.layers.Conv2D(32, 3, input_shape=(32, 32, 3), activation='relu', padding='same'))
model.add(keras.layers.Dropout(0.2))
model.add(keras.layers.BatchNormalization())

model.add(keras.layers.Conv2D(64, (3, 3), padding='same', activation='relu'))
model.add(keras.layers.MaxPooling2D(2))
model.add(keras.layers.Dropout(0.2))
model.add(keras.layers.BatchNormalization())

model.add(keras.layers.Conv2D(64, 3, padding='same', activation='relu'))
model.add(keras.layers.MaxPooling2D(2))
model.add(keras.layers.Dropout(0.2))
model.add(keras.layers.BatchNormalization())
    
model.add(keras.layers.Conv2D(128, (3, 3), padding='same', activation='relu'))
model.add(keras.layers.Dropout(0.2))
model.add(keras.layers.BatchNormalization())

model.add(keras.layers.Flatten())
model.add(keras.layers.Dropout(0.2))
model.add(keras.layers.Dense(32, activation='relu'))
model.add(keras.layers.Dropout(0.3))
model.add(keras.layers.BatchNormalization())

model.add(keras.layers.Dense(class_num, activation='softmax'))

model.compile(loss='categorical_crossentropy', optimizer='adam', metrics=['accuracy'])

print(model.summary())
```

### Possible problems
With too high workload the kernel can crash. This happens mostly on the remote AI server.
On the local machine under Windows 10 there was nearly no issues.
Tensorflow only uses the CPU if certain packages of NVidia hadn't been installed.


### Conclusion
The accuracy was around 80% with 60,000 images, using 50,000 for training and 10,000 for validation from the cifar10 dataset.
With our dataset of 206 images, the accuracy is roughly 50-60%. 
That shows the model works better with a larger dataset

