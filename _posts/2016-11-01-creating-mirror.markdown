---
layout: post
title:  "Simulating Mirror Zoom in 2D: Attempt 1"
excerpt: "Using image processing or computer vision to simulate a mirror"
date:   2016-11-01 1:00 PM
---

This post describes my ongoing attempts at simulating the reflections from a planar mirror using image processing techniques. 

In particular, my task is to simulate planar mirror reflections given the following conditions/assumptions/input:

1. 2D image of the background

2. Background is mostly static

3. Single user in front of a display surface that will act as planar mirror. User is freely moving in x, y, or z directions where +z points away from the mirror

4. A single high resolution camera is facing the user. The camera is attached to a robotic arm. Thus, the camera tracks the location of the user's face.

5. Camera cannot move in z direction. 

6. The camera is positioned behind the display surface. Mirror reflections are to be rendered to the display surface.

7. Realtime for realistic interactions

# Why do I want to simulate a mirror

Mirrors are used for many purposes, one of which is medicine. In medicine, mirrors are used in pain therapy [1], and beyond this, self-imagery (reflection/viewing of your face/person) are being used in behavioral interventions. For instance, Video Self-Modeling (VSM)[2,3] is a behavioral intervention where the user learns by watching a video of herself perform an action. Learning occurs by observng herself perform, an unlearned(?) action that she can acquire (*observational learning*). VSM, and technologies like it (eg. virtual reality dopplegangers[4]) have been shown to be effective in their various applications. However, they are often difficult to produce. VSM requires hours of footage, in order to piece together a short video, showing the user *seemingly* performing the desired action. Dopplegangers are virtual reality replicas of the user, and requires tedious 3D capture of the user's face (and body). Furthermore, these technologies often do not provide any feedback or other form of interaction to the user. In addition, there is little work on the relationship, if any, of a user's learning speed or retention and feedback (or interaction) from a user's self-image during the learning process. 

# What do you propose

For the particular case of behavioral interventions (such as VSM or dopplegangers), a modifiable mirror-like display can provide some answers to the above stated problems. Imagine a programmable planar mirror where a user can interact with their reflection. And... their reflection talks back to them and has its own reactions to the user's actions. 


# What has been done

Generating a virtual mirror is a relatively solved problem in computer graphics. However, computer graphics solutions require a 3D model of the environment. They need a description of all the objects within the environment (lights, models, textures etc). These things are not available in the real world and would require extensive calculations and much tedious work to produce, if it can be produced. 

Image processing and computer vision techniques offer an alternative. In fact, they have been used in all work in generating virtual mirrors, and many commercial applications exist for different virtual mirror products. For instance, virtual try-ons (cosmetics like modiface app, fashion items like eye-glass try-on ) are easy notable examples in this space. A relatively recent paper in this space created a virtual plane mirror display, extendable to arbitrary shape and size mirrors, using 4 networked kinect cameras[5]. Shen et. al proved that the viewer's location, not so much eye gaze, was necessary in determining the correct mirror image to render. However, a 3D model of the background was necessary, required networking kinect cameras, and extensive cleaning of the depth images returned from the cameras. 

While I need to do more work in my research into relevant papers, I do not believe there have been many more advances in the real-time simulation of a virtual mirror (Please let me know via email or twitter if you disagree, with the attendant papers for reference). 

# What now

In this work, I want to modify the work of Shen et. al[5] in the following ways:

1. To remove the need for a 3D background model, use a 2D background image instead. This will be faster to acquire than depth-scanning the environment.

2. To track the user's location in 3D space, track the user's x-y location. That is, track the eye/face location using a camera attached to a robotic arm. As the user's head moves, the camera moves with it. Then hallucinate the zooming effect on the mirror image when the user moves away or toward the display. 

3. To segment out the user without a kinect, use a high def stereo camera that works realtime. The estimated depth can provide an easy layer-wise depth segmentation scheme. 

4. To ensure the camera tracks the user's face, the display can be a one-way mirror, with the camera behind the mirror, and the user in front of it. The allows the camera to center the user's face in the image at all times. It should make the rendering easier. Will prove/disprove it later. 

# Thus far

Thus far, I am working on hallucinating the zooming effect, and will explain my progress and my experiments in my next post. 



# References


1. Ramachandran, Vilayanur S., Diane Rogers-Ramachandran, and Steve Cobb. "Touching the phantom limb." Nature 377.6549 (1995): 489-490.

2. Dowrick, Peter W. "A review of self modeling and related interventions." Applied and preventive psychology 8.1 (2000): 23-39.

3. Buggey, Tom. Seeing is believing: Video self-modeling for people with autism and other developmental disabilities. Woodbine House, 2009.

4. Fox, Jesse, and Jeremy N. Bailenson. "Virtual self-modeling: The effects of vicarious reinforcement and identification on exercise behaviors." Media Psychology 12.1 (2009): 1-25.

5. Shen, Ju, et al. "Virtual mirror rendering with stationary rgb-d cameras and stored 3-d background." IEEE Transactions on Image Processing 22.9 (2013): 3433-3448.


