# Tracking head position while sleeping
In 2017 my new born son had formed a flat spot on his head due to Torticollis (stiff neck that makes it hard or painful to turn your head).  Fortunately, he had successful physical therapy to correct the condition.

That inspired this hobby project as a way to track how long an infant spent sleeping on one part of their head.  At the time (2017) I was a power system engineer for electric utilities.  I had learned some embedded system PCB designand programming in school, but was a little rusty.  It allowed me to explore embedded PCB design and programming and also introduced me to machine learning and AI applications.

As a result of Git not yet being serious part of my life in 2017, very few files were saved other than mentioned below.  I have since then adopted Git to save progress with my software and hardware projects!

## Development
I expermented on two different device concepts:  

1.  Wearable:  A battery powered tile worn as a head band.  It used an accelerometer to track the position of the head.  Though simple and inexpensive, this was quickly abandoned due to risks of choking and batteries near infants.

1.  Camera:  Camera to observe sleeping head pose without contact.  Used head pose detection AI and on-board accelerometer to estimate the head position relative to a flat level bed.  Two approaches were tried for the camera:

    * On-device AI model:  The camera used a Raspberry Pi to run a head pose detection AI model.  The head pose would then be corrected with the accelerometer data to estimate the head position relative to the bed.  I based the proof of concept on the LearnOpenCV blog post [Head Pose Estimation using OpenCV and Dlib](https://www.learnopencv.com/head-pose-estimation-using-opencv-and-dlib/).  This could only process 1 frame per 30 seconds. So, I would need to find a more efficient AI model or a more powerful (expensive) processor.

    * Cloud AI model:  The camera would send an image of the head to AWS Rekognition to calculate the head pose relative to the camera.  The head pose would then be corrected with the accelerometer data to estimate the head position relative to the bed.  This was the most promising approach, and least expensive hardware.  However, the cost of running the AI model on the cloud was too expensive to be practical.  The PCB I designed for this approach is the only work I have saved.  It is in the `hardware` directory.  (requires Fusion 360 to view or edit.)


## Current Status and Future Work
The cost of running the AI to track the head position was too cost prohibitive to be practical for most people at the time.  It would either require a lot of cloud computing resources or much more expensive processing on the device itself.

I have since moved on to other projects, but I would like to revisit this project in the future.  When I do, I would like to explore the following:
*  More efficient AI models (computer vision and machine learning have advanced a lot since 2017)
*  More efficient processing on the device (newer processors with AI acceleration)
