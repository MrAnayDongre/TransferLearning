# TransferLearning
This project is in 'TensorFlow in Practice Specialization' where I've tried to improve the performance using transfer learning.



# When we have a relatively small dataset, a super-effective technique is to use Transfer Learning where we use a pre-trained model. 

This model has been trained on an extremely large dataset, and we would be able to transfer weights which were learned through hundreds of hours of training on multiple high powered GPUs.

Many such models are open-sourced such as VGG-19 and Inception-v3. They were trained on millions of images with extremely high computing power which can be very expensive to achieve from scratch.

# We are using the Inception-v3 model in the project.

Transfer Learning has become immensely popular because it considerably reduces training time, and requires a lot less data to train on to increase performance.


**Get the data (3000 total images)**


![1](https://user-images.githubusercontent.com/56868253/123132857-d2048480-d46c-11eb-897f-dc5138234358.png)

**Import the Inception-v3 model**


![2](https://user-images.githubusercontent.com/56868253/123132932-e21c6400-d46c-11eb-84f0-65b94aa6b003.png)

We are going to use all the layers in the model except for the last fully connected layer as it is specific to the ImageNet competition.


![3](https://user-images.githubusercontent.com/56868253/123133029-f6f8f780-d46c-11eb-94e9-6f41927a0901.png)

Make all the layers non-trainable (We can retrain some of the lower layers to increase performance. Keep in mind that this may lead to overfitting)

![4](https://user-images.githubusercontent.com/56868253/123133133-0e37e500-d46d-11eb-9f70-a0079eb74112.png)

We use binary_crossentropy as the loss metric as we have 2 target classes (it's a binary classification problem)
Our optimizer is RMSprop with a learning rate of 0.0001 (We can experiment with this; Adam and Adagrad optimizers would also work well)

![5](https://user-images.githubusercontent.com/56868253/123133273-31629480-d46d-11eb-9117-5bcad87d04f6.png)


After rescaling the images, and using Image Augmentation, we flow them in batches of 20 using train_datagen and test_datagen. Details can be found in my previous post.

![6](https://user-images.githubusercontent.com/56868253/123133323-3b849300-d46d-11eb-8a27-9d5e4f851829.png)


We have 2000 training images and a 1000 for validation.

**Let’s Train**

![7](https://user-images.githubusercontent.com/56868253/123133386-50612680-d46d-11eb-8ba1-78ce44c39580.png)

![11](https://user-images.githubusercontent.com/56868253/123133445-5a832500-d46d-11eb-8280-d89aeef51478.png)


After about 35 minutes, we were able to achieve an accuracy of 94%. A callback can very easily be implemented after we reach a certain accuracy.
This is the kind of result we were hoping for using Transfer Learning; Building upon a pre-trained model and using it in our custom application which was able to achieve great performance after training on just 2000 images.
Another approach to this problem would be not using all the layers of Inception-v3.

![8](https://user-images.githubusercontent.com/56868253/123133486-67a01400-d46d-11eb-9403-ba82dab2efbf.png)


![9](https://user-images.githubusercontent.com/56868253/123133511-6f5fb880-d46d-11eb-9359-2649c65ad458.png)


# Here I achieved an accuracy of 96% .

![10](https://user-images.githubusercontent.com/56868253/123133563-80a8c500-d46d-11eb-806e-c13eebadf637.png)







