# Facial_expression_detector  
## A pre-trained SSD neural network for the use of analyzing human emotions
### 1.Description
This project is based on Single Shot Multibox Detector(SSD), the article is in https://arxiv.org/abs/1512.02325, the orignal SSD neural network is written in Caffe framework:https://github.com/weiliu89/caffe/tree/ssd, however in this design, what I used is the SSD in the tensorflow objection detection API:https://github.com/tensorflow/models/tree/master/research/object_detection which I think has a more comfortable input file format(TFRecord).
### 2.Dataset
The training dataset we use is Karolinska Directed Emotional Faces (KDEF) which is a set of totally 4900 pictures of human facial expressions, and this set is also publicly available from http://kdef.se. However, I just randomly pick up 110 of them for training use, and I will enlarge my training set in the future.
### 3.Approach
There are several steps to do in the data preprocessing, First is label training set, what I use is LabelImg which is a convenient tool is able to label imgaes into xml file whcich contains coordinate of bounding box and class(PASCAL format). and using xml_2_csv script to transfer xml into csv which can be transfered into TFRecord, then using csv_2_tfrecord script to transfer csv into TFRecord which can be input into SSD.

After preparing the input files, next step will be download model from https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/detection_model_zoo.md, what I use is ssd_mobilenet_v1_coco(It is a pre-trained one but I will discard its pretrained checkpoint), and then download the ssd_mobilenet_v1_facial.config that I upload, after that run train.py follow the instruction in the file to train the model.

Wait until loss function is stable, training can be stopped and I also upload my training checkpoint in the training directory. Then run the export_inference_graph.py follow the instruction inside of this file. 

Finally. use jupyter notebook open the object_detection_tutorial.ipynb file and input your test image and get your own ouput.
### 4.Output
I tested 4 images from KDEF library, and here are my outputs:
![alt text](https://github.com/Zhangchi95/Facial_expression_detector_SSD/blob/master/Myoutput/output1.png)
![alt text](https://github.com/Zhangchi95/Facial_expression_detector_SSD/blob/master/Myoutput/output2.png)
![alt text](https://github.com/Zhangchi95/Facial_expression_detector_SSD/blob/master/Myoutput/output3.png)
![alt text](https://github.com/Zhangchi95/Facial_expression_detector_SSD/blob/master/Myoutput/output4.png)
### 5.Acknowledge
For more information, I highly recommend this step by step Tensorflow objection detection tutorial:https://pythonprogramming.net/introduction-use-tensorflow-object-detection-api-tutorial/
