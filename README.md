# PostureDetection
# PoseNet
Posenet is a real-time pose detection technique with which you can detect human beings’ poses in Image or Video. It works in both cases as single-mode(single human pose detection) and multi-pose detection(Multiple humans pose detection). In simple words, Posenet is a deep learning TensorFlow model that allows you o estimate human pose by detecting body parts such as elbows, hips, wrists, knees, ankles, and form a skeleton structure of your pose by joining these points.
# How does PoseNet work?
PoseNet is trained in MobileNet Architecture. MobileNet is a Convolutional neural network developed by google which is trained on the ImageNet dataset, majorly used for Image classification in categories and target estimation. It is a lightweight model which uses depthwise separable convolution to deepen the network and reduce parameters, computation cost, and increased accuracy. There are tons of articles related to MobileNet that you can find on google.

The pre-trained models run in our browsers, that is what differentiates posenet from other API-dependent libraries. Hence, anyone with a limited configuration in a laptop/desktop can easily make use of such models and built good projects.
# Posenet gives us a total of 17 key points which we can use, right from our eye to and ears to knees and ankles.
![96263posnet_keypoints](https://github.com/VaibhavAjayy/PostureDetection/assets/88434684/204fa844-88a0-4e56-9814-0493a6c3d201)

# Applications of PoseNet in the Real-world used by organizations
1) Used in Snapchat filters where you see the tongue, aspects, glimpse, dummy faces.
2) Fitness apps like a cult which uses to detect your exercise poses.
3) A very popular Instagram Reels uses posture detection to provide you different features to apply on your face and surrounding.
4) Virtual Games to analyze shots of players.

# Posture Detection using PoseNet
# 1) Boiler Template
Create a new folder and create one HTML file which will work as our website to users. here only we will import our javascript file, Machine learning, and deep learning libraries that we will use.
# 2) p5.js
It is a javascript library used for creative coding. There is one software known as Processing on the top of which P5.js is based. The Processing was made in java, which helps creative coding in desktop apps but after that when there was a need for the same thing in websites then P5.js was implemented. Creative coding basically means that It helps you to draw various shapes and figures like lines, rectangles, squares, circles, points, etc on the browser in a creative manner(colored or animated) by just calling an inbuilt function, and provide height and width of shape you want.

Create one javascript file, and here we will try to learn P5.JS, and why we are using this library. before writing anything in the javascript file first import P5.js, add a link to a created javascript file in the HTML file.

There are basic 2 things in P5.js that you implement. write the below code in the javascript file.

a) setup – In this function, you write a code that is related to the basic configuration you need in your interface. one thing you create is canvas and specify its size here. And all the things you implement will appear in this canvas only. Its work is to set up all the things.

function setup() {  // this function runs only once while running
    createCanvas(800, 500);
 }
b) Draw –  The second function is to draw where you draw all things you want like shapes, place images, play video. all the implementation code placed in this function. Understand it as a main function in compiled languages. Its work is to display things on the screen.

let us try drawing some shapes, and take the hands-on experience with the P5.Js library. The best thing is for each figure there is an inbuilt function, and you only need to call and pass some coordinates to draw a shape. to give background colour to canvas call background function and pass colour code.

i) Point – to draw a simple point use point function and pass x and y coordinates

ii) line – line is something which connects two points to only you have to call line function and pass coordinates of 2 points means 4 coordinates.

iii) rectangle – call rect function and pass height and width. If height and width are the same then it will be square.

some other functions used for creativity are.

i) stroke – It defines the outer boundary line of shape

ii) stroke-weight – It defines how much width the outer line should be.

iii) fill – the color you want to fill in the shape

Below is a code snippet as an example for each function we learned. Try this code once and observe changes and figures in a browser by running an HTML file as on a live server.

function draw() {
  background(200);
    //1.point
  point(200, 200);
    //2.line
  line(200, 200, 300, 300);
    //3.trialgle
  triangle(100, 200, 300, 400, 150, 250);
    //4.rectangle
  rect(250, 200, 200, 100);
    //5. circle
  ellipse(100, 200, 100, 100);
 // color circle using stroke and fill
 /*
    fill(127, 102, 34);
    stroke(255, 0, 0);
    ellipse(100, 200, 100, 100);
    stroke(0, 255, 0);
    ellipse(300, 320, 100, 100);
    stroke(0, 0, 255);
    ellipse(400, 400, 100, 100);
*/ 
}
An important feature of P5.js is that the setup function runs only one time for setting up the things but the draw function code runs in an infinite loop till the interface is open. You can check this out by printing anything using the console log command. And by using this you can create amazing designs. With P5js you can load images, capture images, video, etc.

function getRandomArbitrary(min, max) { // generate random num
    return Math.random() * (max - min) + min;
}
/*
    r = getRandomArbitrary(0, 255);
    g = getRandomArbitrary(0, 255);
    b = getRandomArbitrary(0, 255);
    fill(r,g,b);
    ellipse(mouseX, mouseY, 50, 50);
*/
Use this above-commented code in the draw function and new function above it and run code, and observe changes on the browser, and experience the magic of the P5.js library.
# 3) ML5.js
The best way to share code applications with others is the web. Only share URL and you can use other applications on your system. keeping this google implemented tensorflow.js, but working with tensorflow.js requires a deep understanding So, ML5.js build a wrapper around tensorflow.js and made the task simple by using some function so indirectly you will deal with TensorFlow.js through ml5.js. The same you can read on official documentation of Ml5.js

Hence, It is the main library that consists of various deep learning models on which you can build projects. In this project, we are using the PoseNet model which is also present in this library.

let’s import the library, and use it. In the HTML file paste the below script code to load the library.

Now let’s set up the Image capture and load the PoseNet model. the capture variable is a global variable, and all the variables we will be creating have global scope.

let capture;
function setup() {  // this function runs only once while running
    createCanvas(800, 500);
    //console.log("setup function");
    capture = createCapture(VIDEO);
    capture.hide();
    //load the PoseNet model
    posenet = ml5.poseNet(capture, modelLOADED);
    //detect pose
    posenet.on('pose', recievedPoses);
}
function recievedPoses(poses) {
    console.log(poses);
    if(poses.length > 0) {
        singlePose = poses[0].pose;
        skeleton = poses[0].skeleton;
    }
}
As we load and run the code, so Posenet will detect 17 body points(5 facial points, 12 body points) along with information that at what pixel the point is been detected in an Image. And if you print these poses then it will return an array(python list) that consists of a dictionary with 2 keys as pose and skeleton that we have assessed.

pose – It is again a dictionary that consists of various keys and a list of values as key points, left eye, left ear, nose, etc.
skeleton – In skeleton, each dictionary consists of two subdictionaries as zero and one that has a confidence score, part name, and position coordinate. so we can use this to make a line and construct a skeleton structure.
Now if you want to display any single point in front of the pose then you can do it by using these separate points in a pose.
