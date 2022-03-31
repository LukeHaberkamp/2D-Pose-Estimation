# "Validity of single-leg squat kinematics determined by an artificial intelligence, human pose estimation model" Colab Code
The code features an implementation of OpenPose which can be found at https://github.com/CMU-Perceptual-Computing-Lab/openpose

By using OpenPose, 2D kinematics can be evaluated
## Prerequisites
The code implements OpenPose to calculate lower body kinematics in Google Colab, which is a free virtual Jupyter notebook environment in the cloud. Therefore, the user does not need any local installation. 

## Usage
Click on "Open in Colab" from the 2D_Pose_Estimation.ipynb file, to open the code in colab.

<img width="159" alt="Screen Shot 2022-03-30 at 6 47 38 PM" src="https://user-images.githubusercontent.com/75814890/160943467-704660c4-04a3-459b-962d-b9af24579604.png">

Run each cell in the code to install, buid, and perform kinematic analysis using OpenPose. 

Ensure that cells are run in a specific order:
1) install and build OpenPose and ensure your video is imported with the path correctly set
2) run the kinematics code applying OpenPose
3) view your results

## Importing Videos
Currently a cell in the notebook prompts the user to upload a video to the Colab enviroment. 

``````
from google.colab import files
uploaded = files.upload()
myVideo = next(iter(uploaded))
``````

If you would like to analyze multiple videos it is recommended to first upload the videos to Google Drive. Once the videos are uploaded, uncomment the below cell and alter the name of the video in the path to analyze your video. 

``````
from google.colab import drive
drive.mount('/content/drive')
myVideo = "/content/drive/MyDrive/myVideo.mp4"
``````

Be sure to change the name of "myVideo.mp4" to include your video along with its corresponding extension.

## Viewing the Results
To view your video with OpenPose overlayed, view the output.mp4 video.

![output](https://user-images.githubusercontent.com/75814890/160946348-d0c42dfd-9724-41ec-9bb1-d695096bbaef.gif)

The kinematics portion of the Google Colab code, will calculate either sagittal or frontal plane joint angles based off the field of view.
The joint angles include:

Sagittal
- Forward Trunk Lean 
- Hip Flexion (+ flexion/ -extension)
- Knee Flexion (+ flexion/ -extension)
- Ankle Dorsiflexion (+ flexion/ -extension)

Frontal
- Pelvic Drop (+ contralateral drop)
- Hip Adduction (+ adduction/- abduction)
- Knee Abduction (+ abduction/- adduction)



The kinematics are exported to Microsoft Excel with the name excelResults.xlsx


Running the code from the cell below will download these files for the user
``````
from google.colab import files
files.download('output.mp4') 
files.download('excelResults.xlsx')
```````


Graphs can be viewed locally in Colab by adjusting the dropdown in the final cell. Shown below is a sample graph of Knee Flexion vs. Time from the .gif above

<img width="840" alt="Screen Shot 2022-03-30 at 7 17 21 PM" src="https://user-images.githubusercontent.com/75814890/160946182-fac240aa-b0ea-476c-86ce-c01dd772f97a.png">
