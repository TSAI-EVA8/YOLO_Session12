
## Below are the instructions from the canvas (copy pasted)


## Problem Statement

1. OpenCV Yolo: [SOURCE](https://pysource.com/2019/06/27/yolo-object-detection-using-opencv-with-python/)  
    1. Run this above code on your laptop or Colab.  
    2. Take an image of yourself, holding another object which is there in COCO data set (search for COCO classes to learn).  
    3. Run this image through the code above.  
    4. Upload the link to GitHub implementation of this  
    5. Upload the annotated image by YOLO. 
2. Training Custom Dataset on Colab for YoloV3  
    1. Refer to this Colab File: [LINK](https://colab.research.google.com/drive/1LbKkQf4hbIuiUHunLlvY-cc0d_sNcAgS)
    2. Refer to this GitHub [Repo](https://github.com/theschoolofai/YoloV3)
    3. Download this [dataset](https://drive.google.com/file/d/1sVSAJgmOhZk6UG7EzmlRjXfkzPxmpmLy/view?usp=sharing). This was annotated by EVA5 Students. Collect and add 25 images for the following 4 classes into the dataset shared:  
        1. class names are in custom.names file.   
        2. you must follow exact rules to make sure that you can train the model. Steps are explained in the README.md file on github repo link above.  
        3. Once you add your additional 100 images, train the model  
    4. Once done:  
        1. [Download](https://www.y2mate.com/en19) a very small (~10-30sec) video from youtube which shows your classes. 
        2. Use [ffmpeg](https://en.wikibooks.org/wiki/FFMPEG_An_Intermediate_Guide/image_sequence) to extract frames from the video.  
        3. Upload on your drive (alternatively you could be doing all of this on your drive to save upload time)
        4. Infer on these images using detect.py file. **Modify** detect.py file if your file names do not match the ones mentioned on GitHub.  
        python detect.py --conf-three 0.3 --output output_folder_name
        5. Use  [ffmpeg](https://en.wikibooks.org/wiki/FFMPEG_An_Intermediate_Guide/image_sequence) to convert the files in your output folder to video
        6. Upload the video to YouTube. 
        7. Also run the model on 16 images that you have collected (4 for each class)  
    5. Share the link to your GitHub project with the steps mentioned above - 1000 pts (only if all the steps were done, and it resulted in a trained model that you could run on video/images)  
    6. Share the link to your YouTube video - 500 pts  
    7. Share the link of your YouTube video shared on LinkedIn, Instagram, medium, etc! You have no idea how much you'd love people complimenting you! [TOTALLY OPTIONAL] - bonus points  
    8. Share the link to the readme file where we can find the result of your model on YOUR 16 images. - 500 pts. 

3. Bonus: [YoloV4 Training on Colab!](https://colab.research.google.com/drive/1b08y_nUYv5UtDY211NFfINY7Hy_pgZDt#scrollTo=1YW7jPF1BOAw). 

Questions on the submission page asked are:  
1. Upload the link to your YOLOv3OpenCV code on Github. - 100 pts  
2. Upload the link to the image annotated by OpenCV YOLO inference.  - 100 pts  
3. Share the link to your GitHub project with the steps mentioned above (for YoloV3 training on Colab).  -1000 pts  
4. Share the link of your YouTube video (your object annotated by your YoloV3 trained model). - 800 pts.  








# This is a multipart assignment 

## Part1:

Using OpenCV to identify the objects in the COCO dataset. 
As a part of the assignment we were supposed to take our photo holding a COCO dataset object . So here I am :

![alt text](OpenCV/rohit_coco_detected.png "Title")


The associated code is in [OpenCV](https://github.com/TSAI-EVA8/YOLO_Session12/blob/master/OpenCV/Yolo_CV2.ipynb)


## Part2:
code: 
[part2](https://github.com/TSAI-EVA8/YOLO_Session12/blob/master/part1/YoloV3Sample_Part1.ipynb)

This part is about training YOLO on a COCO like dataset. The following steps were done:
 1. Fine tune YOLO for 300 epochs. The initial weights were already given at  https://drive.google.com/file/d/1vRDkpAiNdqHORTUImkrpD7kK_DkCcMus/view?usp=share_link

2. The idea is to detect "WALLE" 

3. After training the algo for 300 epochs using the smalcoco dataset here are the results

![alt text](part1/walle1.png "Title")

![alt text](part1/walle2.png "Title")

![alt text](part1/walle3.png "Title")

![alt text](part1/walle4.png "Title")


## Part3:
code is [part3](https://github.com/TSAI-EVA8/YOLO_Session12/blob/master/part2/YoloV3Sample_Part2.ipynb)

This is the main part where we need to train the model to detect custom objects . In this case the model is detecting 4 classes instead of just 1

The classes are : **boots**, **vest**, **hats**, **masks**

The dataset is from the previous EVA courses and has been augmented by me

Some of the changes that needed to be done in comparison to part1 (since there are 4 classes)

1. Update the cfg/yolov3-custom.cfg file with the changes of
filters=27
classes=4
as we have 4 classes in the custom dataset

2. Make the following changes to the utlity.py file
```
##line 470
t=t.to(targets.device)
a=a.to(targets.device)

##line 870
ns = int(np.ceil(bs ** 0.5)
```



The model is supposed to be fine tuned for 300 epochs but because of the computation resources constraint I trained for 20 epochs. 
However the results are good even with 20 epochs of the training

Following are some of the samples 

## class: Boots
![alt text](part2/test_images/boots1.jpg "Title")
![alt text](part2/test_images/boots4.jpg "Title")

## class: vests
![alt text](part2/test_images/vest1.jpg "Title")
![alt text](part2/test_images/vest4.jpg "Title")

## class: mask
![alt text](part2/test_images/mask1.jpg "Title")
![alt text](part2/test_images/mask4.jpg "Title")


## class: hat
![alt text](part2/test_images/hat1.jpg "Title")
![alt text](part2/test_images/hat4.jpg "Title")


## Youtube video

After the training we were also supposed to create a video for multiple images with object detection done and upload to the youtube

here is the link of the youtube video 
**https://www.youtube.com/shorts/bQiKnpnHSbg**




