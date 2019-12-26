For 50 epochs
-------------
val_gender_output_acc	0.8234
val_image_quality_output_acc	0.7174
val_age_output_acc	0.8009
val_weight_output_acc	0.8258
val_bag_output_acc	0.7459
val_footwear_output_acc	0.7606
val_pose_output_acc	0.8408
val_emotion_output_acc	0.8534

Total params: 1,146,959
Trainable params: 1,146,567
Non-trainable params: 392

Model Explanation
------------------
- Mounted the file in gdrive, unzipped and loaded to dataframe
- One hot encoding was done as this is a multi-class multi-label problem
Data generator class created. 'Persondatagenerator' will feed the images based on batch size on the fly to model while executing model.fit_generator
Cut-out function 'get_random_eraser' copied from github. Cut-out is a data augmentation technique which we will use in data generator 
Train_test_split done. Test:Train ratio = 0.15. Gave random_state=42 to avoid data leakage
Created train_gen and valid_gen - datagenerators for train and validation data respectively with required image data augmentation, image rescaling and image normalization
Created backbone for our model. Model is a sequential model as this was giving better accuracy compared to Resnet50.
Each convolution layer has batch normalization & dropout included. Padding was set as 'valid' as change in accuracy was not observed by keeping padding as 'same'.
Then flatten and dense layer with 512 layers was used to create a fully connected layer, it is called.
8 different heads are created for each class to connect to backbone via neck.
Layers to build each head was parametrized by employing build_tower functions.
model is compiled and ran for 50 epochs.
