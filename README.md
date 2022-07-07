# opencv-airside-vehicle-speed-monitoring
OpenCV based Airside Vehicle Speed Monitoring

# Airside Vehicle Speed Detection using OpenCV

![output.gif](output.gif)

Tool / Library used :
- Python
- opencv
- dlib
<br>

Tasks breakdown
1. Vehicle Detection
    - I am using Haarcascade classifier to identify vehicles.
2. Vehicle Tracking - ( assigning IDs to vehicles )
    - I have used corelation tracker from dlib library.
3. Speed Calculation
    - I am calculating the distance moved by the tracked vehicle 
		  in a second, in terms of pixels, we need pixel per meter
		  to calculate the distance travelled in meters.
	- With distance travelled per second in meters, we will get the 
		  speed of the vehicle.

#### How to run the script? 

Follow steps:

1. Clone repo :
`git clone https://github.com/kraten/vehicle-speed-check`

2. cd (change directory) into vehicle-speed-check
`cd vehicle-speed-check`

3. Create virtual environment
`python -m venv venv`

4. Activate virtual environment
`./venv/bin/activate`

5. Install requirements
`pip install  -r requirements.txt`

6. run speed_check.py script
`python speed_check.py`

#### Script Explanation: 

I have estimated these values manually for the current path at airside to calculate pixels per metre(ppm). Therefore, the value will vary from road to road and have to be adjusted to be used on any other video captured at airside. 

If I talk about the part how I estimated ppm, we need to know the actual width in metres of the road at airside (you can measure the road width by visiting the path at any of the airside zone of the respective airport). Also, I have taken the video frame and calculated the width of the path in pixels digitally. Now, we have the width of the path in metres from a real world airport zone and in pixels from our video frame. To map the distances between these two worlds, I have calculated pixels per metre by dividing distance of the respective path in pixels to metres.

d_pixels gives the pixel distance travelled by the vehicle in one frame of our video processing. To estimate speed in any standard unit first, we need to convert d_pixels to d_metres.

Now, I can calculate the speed(speed = d_meters * fps * 3.6). d_meters is the distance travelled in one frame. I have already calculated the average fps during video processing. So, to get the speed in m/s, just (d_metres * fps) will do. I  have multiplied that estimated speed with 3.6 to convert it into km/hr.

### Pull requests are welcome
