**PROJECT TITLE**
Soccer Analytics: Action Recognition.  



**Introduction**

A GUI which enables action classification and labelling of soccer player’s action in a broadcast video based on teams.

    
**Focus Areas:** 
dribbling,kicking, running and passing using over 2000 sample images. 

** Methodology:** 
- Create a flask application
- Connect to the User Interface(React)
- Use the trained model to process video frames
- Detect the skeleton(s) in each frame
- Label each detected skeleton(s)
- Give live analytics from the processing based on each team.
- Display the processed frames in a video format for the user.
- Get real-time action metrics  for each team.

**Getting Started**
These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.


**Prerequisites** 

- Go to web.ipynb, download the file, open in colab and run. Run each cell up until the cell that has "!python run.py".
  This will install all the dependencies that you need for the application to work.
  
- Go to Soccer_Analysis folder and clone the folder in your google drive

- Go to Action_recognition_Ui and download the folder.This folder contains the react application which displays a UI for Soccer Action Metrics Recognition.

**Installing**
- After opening "web.ipynb" in Colab start running each cell.
  * The first cell helps with Accessing data on Google Drive.
    Code below mounts your Google Drive to /content/drive/My Drive directory.
    from google.colab import drive
    drive.mount("/content/drive/", force_remount=True)

  * The second send directs you to the flask application which is located in your Google Drive directory.
    Code below shows an example of how to locate the Soccer_Analysis folder in your Drive.
    %cd /content/drive/My Drive/Colab Notebooks/Soccer_Analysis
    
    * The rest of the cells up until "!python run.py", have all the libraries and requirements needed to run the application.

**Running the tests** 
- Go to the last cell in "web.ipynb" and run the cell "!python run.py"
  This would generate an ngrok Url.Which you would copy
- Go to computer's terminal, copy and paste: "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)". This will install homebrew on your device. 
- Go to the Action_recognition_UI which you downloaded and open with any IDE preferably "VS Code"
- Go to the terminal in the IDE and go to the folder directory using "cd <path to directory>.
  If you don't have npm, install npm package by going to their website and downloading npm to your system Or you can use "brew install node" which will install npm
  If you don't have yarn installed with npm, by doing "brew install yarn".
- After installing the npm package as well as the yarn package. Go to the Action_recognition_UI folder and open a ".env" file which is located in the base directory.
  *Open it up and you will make some changes to it. Example:
            **REACT_APP_REMOTE_SERVICE_BASE_URL="<copy and paste the ngrok url that was generated initially from the first step>"**
- Go back to the terminal and type the following:
     *Run "yarn".
     *Run "npm run start". This will show you a UI which contains and upload button, table and a textarea for hex color code input for teams.(If this starts up in chrome copy the url and paste it in Safari)
-  Choose any soccer video of your choice.
-  Check the color of each team jersey and check online for their corresponding hex color code. Eg. Team1: #730324——red,  Team2: #89afcb——-blue
-  Copy each hex color code and paste in each text box respectively.
- Click on choose file, then go to the directory of the soccer video file that you decided to pick. 
-  Click on ** "Upload".**

 

**Conclusion**
This sends the video and the hex color codes to the flask application where it is processed and the outcome is shown in a tabular form in the UI which comprises the action metrics count for each team. In this case we are considering "dribbling, running, kicking, passing".
The output video which shows how the player's actions are detected is also shown to the user and can either be played or paused depending on the user.

In this application users can upload a video and hex color code for team1 and team2, where the hex color code will be validated  in the flask application and also converted to rgb color code respectively.
Which will be used as a reference or basis for rgb color code difference and  color thresholding(thresholding is required for better classification of players to teams). After this Openpose is used to  generate skeletons on each player, which will be tested against the trained model and be classified based on their actions either dribbling, running, kicking, passing. Those actions will be incremented every time an action is detection, these counts will be extracted for each player with respect to their teams. Which will be shown in a tabular form in the UI alongside the processed video.
