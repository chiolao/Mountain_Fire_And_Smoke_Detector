# Mountain Fire And Smoke Detector

Discription:
-
A simple application to help people detect the mountain fire in a large scope to avoid casualties.


Problem Solution:
-
1. Based on the specific RGB formula to detect the fire.[1] </br>
2. Consider some of mountain fires are happened with the smoke first because the wet environment, so detect the smoke without specific RGB formular.</br>
  a) Using LBP or HARR training the data source.[2-4] </br>
  b) Tracking the smoke moving paths by using GMM(Gaussian Mixed Model). </br>
  
Part 1: without machine learning Working Processes:
-
1. Spliting the image to 3 channels image and get the R G B value. [code](https://github.com/Jayupp/Mountain_Fire_And_Smoke_Detector/blob/master/ReadMe%20source/Check_RGB_COLOR.PNG)</br> 
2. Build the positive smoke csv file and negative csv file for LBP or HARR training. [positive file code](https://github.com/Jayupp/Mountain_Fire_And_Smoke_Detector/blob/master/BuildCSV/build_positive_code.txt) [negative file code](https://github.com/Jayupp/Mountain_Fire_And_Smoke_Detector/blob/master/BuildCSV/build_negative_code.txt)<br>
Using opncv opencv_createsamples.exe and opencv_traincascade.exe to tain the data. After [training](https://github.com/Jayupp/Mountain_Fire_And_Smoke_Detector/blob/master/ReadMe%20source/createSamples.PNG), the test [result](https://github.com/Jayupp/Mountain_Fire_And_Smoke_Detector/blob/master/ReadMe%20source/cascade.xml) didn't show what I expect. <br>
May have these reasons:<br>
    a) The positive data source and negative source very samiliar. For emample the cloud images produce the small differences with smoke. <br>
    b) The CPU i5 is not that fast for training, some parameters based on the cpu performance which limit the data accuracy.<br>
3. By tracking smoke path(Gaussian Mixed Model) to replace by using training model to detect the smoke.[code](https://github.com/Jayupp/Mountain_Fire_And_Smoke_Detector/blob/master/ReadMe%20source/check_Smoke.PNG)<br>
4. Draw Rect to display the fire and smoke area.

Program Result:
-
Fire Image testing<br>
<img src="https://github.com/Jayupp/Mountain_Fire_And_Smoke_Detector/blob/master/ReadMe%20source/fire_image_check.PNG"/>
<br>
<br>
Smoke Video testing<br>
<img src="https://github.com/Jayupp/Mountain_Fire_And_Smoke_Detector/blob/master/ReadMe%20source/smoke_video_check.PNG"/><br>

Improvement:
-
1. Using Gaussian Mixed Model to detect the moving smoke also will be triggered by moving anaimals. Such as bird so need to double detect the thing's color to make sure the anaimal or the fire. But what if the mountain fire doesn't have light just smoke, how the program knows it is fire rather than anaimal when we use tracking model? I think still need to based on the training model and more training source. May try to use ANN or CNN in the future.
2. Another thing is that can add some sensors to help the program to detect the environment and collect more useful data. For example the tempure sensors and smoke sensors. 

Part 2: With machine learning CNN model to identify the smoke image
-
1)Preparetion:
-
    1. (IMPORTANT!) In order to match with the code, save the tranning file into the root of F:\ disk
    2. download and set the path for python v3.0+
    3. install necessary packages, such as tensorflow and numpy
    4. suggest to use pycharm
2)Training data:
-
    1. 0 represent the positive dataset, 1 represent the negative dataset.
    2. run main.py
  <img src="https://github.com/Jayupp/Mountain_Fire_And_Smoke_Detector/blob/master/ReadMe%20source/TrainingResult.jpg"/><br>

3)Testing data:
-
    1. save the image into the testing file, specific data path please check the code (so far each time can only take one image, will improve with a loop)
    2. modify the parameters for your necessary
    3.run test.py
    
   <img src="https://github.com/Jayupp/Mountain_Fire_And_Smoke_Detector/blob/master/ReadMe%20source/TestingResult.jpg"/><br>
   <img src="https://github.com/Jayupp/Mountain_Fire_And_Smoke_Detector/blob/master/ReadMe%20source/TrainingNegativeResult.jpg"/>
  <br>



Tools:
-
Visual Studio<br>
Opencv packages<br>

Developer:
-
Jay Zheng<br>
All rights reversed by Jie Zheng™ 2018

Reference:
-
[1] Experimental Study of Video Fire Detection and its Applications Arthur K.K.WongN.K.Fong<br>
[2] CVPR Lab. at Keimyung University.Wildfire smoke ideo Database[DB/OL]. http://cvp-r.kmu.ac.kr/, 2012/2015-12-20.<br>
[3] University of Salerno.Smoke Detection Dataset[DB/OL]. http://mivia.unisa.it/2012-7/2015-12-20.<br>
[4] Cetin, E., Computer Vision Based Fire Detection Dataset[DB/OL].http://sig-nal.ee.bilke-nt.edu.tr/VisiFire/Demo/SmokeClips/ 2014/2015-12-20.
