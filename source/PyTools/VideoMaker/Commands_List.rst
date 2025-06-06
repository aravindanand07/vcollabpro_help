**************************
List of Commands
**************************


Set Parameters
==============


VPANIM_PARAMS
**************

This command contains parameters responsible for smoothness of the video generation.

.. code-block:: 

    VPANIM_PARAMS,nFrame_VP2VP,nImgsPerView=1,iSpeed,iSectionAnimFrames,iExplodeAnimFrame

- [1] nFrame_VP2VP: Specify number of frames while navigating from ViewPoint to ViewPoint
- [2] nImgsPerView: Specify number of images to be captured for video creation for the view
- [3] iSpeed: Specify video speed, *-4* is the slowest, *3* is the fastest
- [4] iSectionAnimFrames: Specify number of frames while showing a section cut
- [5] iExplodeAnimFrame: Specify number of frames for Explode operation for smoother video


VPANIM_CAEPARAMS
*****************

This command contains parameters to control CAE animation smoothness.

.. code-block:: 

    VPANIM_CAEPARAMS,bCAEAnim(Y/N),nCylesPerView,nFramesPerCyle,nImgsPerCAEFrame

- [1] bCAEAnim: Specify if CAE Animation capture is required for video generation, Yes or No
- [2] nCylesPerView: Specify the number of repetitions of the CAE animation
- [3] nFramesPerCyle: Specify the number of frames to be captured in the CAE animation for a smoother video
- [4] nImgsPerCAEFrame: Specify the number of images per CAE frame to be captured


ViewPoint Animation
====================


VP2VP_ANIM
***********

This command captures ViewPoint animation of the ViewPoints as listed in index.

.. code-block:: 

    VP2VP_ANIM,index1,index2 => index2 = 0 => all

- [1] index1: Specify ViewPoint index number to start from
- [2] index2: Specify ViewPoint index number to end with. If index is 0, all ViewPoints are animated


GO2VP_ANIM
***********

This command resets the model view to the specified ViewPoint.

    .. code-block::

        GO2VP_ANIM,ViewPath/N,ViewPointName/Index

    - [1] ViewPath/index: Specify the ViewPath to be selected, user can select *N* for current ViewPath
    - [2] ViewPoint/index: Specify the ViewPoint name or index to which the model view will be reset to


APPLY_VP
*********

This command applies the specified ViewPoint.

.. code-block:: 

    APPLY_VP,vpindex

- [1] vpindex: Specify the ViewPoint index value (starts from 1)


Model movements
================


ROTATE_MODEL
*************

This command rotates the model about an axis with respect to the center.

.. code-block:: 

    ROTATE_MODEL,Axis[x,y,z],bScreen(Y/N),fTeta,nFrames,PartNameInfo=ALL/NONE/ADD/DEL/ONLY/INVERT/VP,Part name list

- [1] Axis x,y,z: Specify the axis of rotation. For example: Rotation about Z-axis will be denoted as 0,0,1
- [2] bScreen: Specify if coordinate system for rotation should be Global or Camera/Screen
- [3] fTheta: Specify the angle of rotation
- [4] nFrames: Specify the number of frames for a smoother video capture
- [5] PartNameInfo: Specify the moving parts list for rotation. Optional(Default is current moving parts list)

    - ALL/NONE: All visible parts are considered. [6] is not used for this option
    - INVERT: All visible parts which are not present in current moving parts list. [6] is not used for this option
    - ADD: Add user specified parts to the current moving parts list. [6] is parts list
    - DEL: Delete user specified parts from the current moving parts list. [6] is is parts list
    - ONLY: Only user-specified parts will be considered. [6] is parts list
    - VP: Displayed parts in the user-specified ViewPoint will be considered

- [6:] Specify the part names list(Wild card character '*' is supported), or ViewPoint and ViewPath


MOVE_MODEL
***********

This command translates the model in a user-specified direction.

.. code-block::

    MOVE_MODEL,Vector[x,y,z],bScreen(Y/N),fLength,nFrames,PartNameInfo=ALL/NONE/ADD/DEL/ONLY/INVERT/VP,Part name list

- [1] x,y,z: Specify vector direction for translation. For example: Translation in Z-axis will be denoted as 0,0,1
- [2] bScreen: Specify if coordinate system for rotation should be Global or Camera/Screen
- [3] fLength: Specify the length of translation
- [4] nFrames: Specify the number of frames for a smoother video capture
- [5] PartNameInfo: Specify the moving parts list for translation. Optional(Default is current moving parts list)

    - ALL/NONE: All visible parts are considered. [6] is not used for this option
    - INVERT: All visible parts which are not present in current moving parts list. [6] is not used for this option
    - ADD: Add user specified parts to the current moving parts list. [6] is parts list
    - DEL: Delete user specified parts from the current moving parts list. [6] is is parts list
    - ONLY: Only user-specified parts will be considered. [6] is parts list
    - VP: Displayed parts in the user-specified ViewPoint will be considered

- [6:] Specify the part names list(Wild card character '*' is supported), or ViewPoint and ViewPath


SET_MOVING_PARTS
*****************

This command specifies the user-defined part name list for *ROTATE_MODEL* or *MOVE_MODEL*.

.. code-block::

    SET_MOVING_PARTS,ALL/NONE/ADD/DEL/ONLY/INVERT/VP,Part name list

- [1] PartNameInfo: Specify the part selection option:
    - ALL/NONE: All visible parts are considered. [2] is not used for this option
    - INVERT: All visible parts which are not present in current moving parts list. [2] is not used for this option
    - ADD: Add user specified parts to the current moving parts list. [2] is parts list
    - DEL: Delete user specified parts from the current moving parts list. [2] is is parts list
    - ONLY: Only user-specified parts will be considered. [2] is parts list
    - VP: Displayed parts in the user-specified ViewPoint will be considered
- [2:] Specify the part names list (Wild card character '*' is supported), or ViewPoint and ViewPath


RESET_ALLMOVES
****************

This command resets all moves previously specified, and no image is captured for this command for video command.

.. code-block::

    RESET_ALLMOVES


Camera movements
=================


ROTATE_CAMERA
**************

This command rotates the camera to capture video while the model remains at the same location.

.. code-block::

    ROTATE_CAMERA,Axis[x,y,z],fDegrees,nFrames,bRelativeToScreen(Y/N),vector<float> rotation_centervector

- [1:3] Axis x,y,z: Specify the axis of rotation. For example: Rotation about Z-axis will be denoted as 0,0,1
- [4] fDegrees: Specify the angle of rotation in degrees
- [5] nFrames: Specify the number of frames for a smoother video capture
- [6] bRelativeToScreen: Specify if rotation of camera is with respect to screen
- [7:9] Rotation_Center [x,y,z]: Specify the rotation center


MOVE_CAMERA
************

This command translates the camera to capture video while the model remains at the same location.

.. code-block::

    MOVE_CAMERA,Translation Vector[x,y,z],nFrames,bRelativeToScreen(Y/N)

- [1:3] Vector x,y,z: Specify the translation vector. For example: Camera translation of 10 units in Z-axis will be denoted as 0,0,10
- [4] nFrames: Specify the number of frames for a smoother video capture
- [5] bRelativeToScreen: Specify if translation of camera is with respect to screen


MOVE_CAMERA_DIR
****************

This command translates the camera to capture video while the model remains at the same location. Translation vector is defined by direction vector and distance.

.. code-block::

    MOVE_CAMERA_DIR,Direction Vector[x,y,z],Distance,nFrames,bRelativeToScreen(Y/N)

- [1:3] Direction Vector x,y,z: Specify the direction unit vector. For example: Camera translation in Z-axis will be denoted as 0,0,1
- [4] Distance: Specify the distance.
- [5] nFrames: Specify the number of frames for a smoother video capture
- [6] bRelativeToScreen: Specify if translation of camera is with respect to screen


Explode Animation
==================


EXPLODE_ANIM
*************

This command captures the exploded animation.

.. code-block::

    EXPLODE_ANIM,iPercent(0-100),bReset,nFrames

- [1] iPercent: Specify the explode percentage
- [2] bReset: Specify if model needs to be reset after explosion
- [3] nFrames: Specify number of frames for smoother video capture


EXPLODE_DIR
************

This command captures the exploded animation in a user-defined direction.

.. code-block::

    EXPLODE_DIR,dirvec,Scale,SortBy(Top/Bot/Mid/Width),bReset,nFrames

- [1] dirvec: Specify the explosion direction. For example: Explosion in z-axis will be denoted as 0,0,1
- [2] Scale: Specify the explosion scale
- [3] SortBy: Specify the parts being sorted in the direction vector

    - Top: Parts are arranged from the top
    - Bot: Parts are arranged from the bottom
    - Mid: Parts are arranged from the middle of the assembly
    - Size: Parts are arranged in the width direction of the assembly

    .. image:: media/EXPLODE_DIR.png
        :width: 200


- [4] bReset: Specify if model needs to be reset after explosion
- [5] nFrames: Specify number of frames for smoother video capture


CUTSECTION_ANIM
****************

This command Captures animation of cut section.

.. code-block::

    CUTSECTION_ANIM,nFrames,bReset,Plane Normal(dx,dy,dz),NodeID/Position(x,y,z)

- [1] nFrames: Specify number of frames for smoother video capture
- [2] bReset: Specify if cutsection animation needs to move back to original position
- [3:5] Plane Normal: dx,dy,dz defining the normal vector of the plane
- [6,<:8>] NodeID/Position: Specify the node ID or position(x,y,z) upto which cut section plane should move


Capture CAE Animation
======================


CAPUTRE_CAEANIM
*****************

This command captures the CAE Animation in the current ViewPoint.

.. code-block::

    CAPUTRE_CAEANIM

- No Arguments

.. note:: It is recommended to preceed this command with *VPANIM_CAEPARAMS*. All parameters set will be used for capturing CAE animation.


START_CAEANIM
***************

This command defines parameters for CAE animation indicating to start the animation during camera movement.

.. code-block::

    START_CAEANIM,nCycles,Animtype(0/1/3),nFrames,bDeform(Y/N)

- [1] nCycles: Specify the number of times the animation would run for
- [2] Specify the CAE Animation type:

    - 0 indicates Linear Animation
    - 1 indicates Transient Animation
    - 3 indicates animating contour color based on Legend Palette using transparency

- [3] nFrames: Specify the number of frames for smoother video capture
- [4] bDeform: Specify if deformation is required in the animation or not


STOP_CAEANIM
*************

This command stops the CAE Animation during tha camera movement.

.. code-block::

    STOP_CAEANIM

- No Arguments


Parallel Animation
===================


PA_START
*********

This command starts Parallel (PA\_) Animation Commands.

.. code-block::

    PA_START,nFrames


- [1] nFrames: Number of Frames for all subsequent PA\_ Commands till *PA_END*


PA_END
*******

This command indicates the end of Parallel (PA\_) Animation Commands.

.. code-block::

    PA_END


- No Arguments


PA_MOVE
********

This command rotates and translates the selected parts.

.. code-block::

    PA_MOVE,T0=starttime,T1=endtime,fRotAxis[x,y,z],fTeta,fTransDir[3],fTLen,sPartlist


- [1] T0: Specify the start time(T0=0 to 1) of the animation, it is the fraction of total duration at which the command begins
- [2] T1: Specify the end time(T1=0 to 1) of the animation, it is the fraction of total duration at which the command ends
- [3:5] fRotAxis: Specify the axis of rotation. For example: Rotation about Z-axis will be denoted as 0,0,1
- [6] fTeta: Specify the angle of rotation in degrees
- [7:9] fTransDir: Specify the translation direction vector. For example: Translation in Z-axis will be denoted as 0,0,1
- [10] fTLen: Specify the length of translation
- [11:] sPartlist: Specify the part names list (Wild card character '*' is supported)


PA_ROTATE
**********


This command rotates the selected parts.

.. code-block::

    PA_ROTATE,T0=starttime,T1=endtime,fRotAxis[x,y,z],bScreen,fTeta,sPartlist


- [1] T0: Specify the start time(T0=0 to 1) of the animation, it is the fraction of total duration at which the command begins
- [2] T1: Specify the end time(T1=0 to 1) of the animation, it is the fraction of total duration at which the command ends
- [3:5] fRotAxis: Specify the axis of rotation. For example: Rotation about Z-axis will be denoted as 0,0,1
- [6] bScreen: Specify if coordinate system for rotation should be Screen or Global
- [7] fTeta: Specify the angle of rotation in degrees
- [8:] sPartlist: Specify the part names list (Wild card character '*' is supported)


PA_TRANS
*********

This command translates the selected parts.

.. code-block::

    PA_TRANS,T0=starttime,T1=endtime,fTransDir[x,y,z],bScreen,fTLen,sPartlist


- [1] T0: Specify the start time(T0=0 to 1) of the animation, it is the fraction of total duration at which the command begins
- [2] T1: Specify the end time(T1=0 to 1) of the animation, it is the fraction of total duration at which the command ends
- [3:5] fTransDir: Specify the translation direction vector. For example: Translation in Z-axis will be denoted as 0,0,1
- [6] bScreen: Specify if coordinate system for rotation should be Screen or Global
- [7] fTLen: Specify the length of translation
- [8:] sPartlist: Specify the part names list (Wild card character '*' is supported)


PA_OPAQUE
**********

This command changes transparancy of the selected parts.

.. code-block::

    PA_OPAQUE,T0=starttime,T1=endtime,Tranparancy(0-100),sPartlist


- [1] T0: Specify the start time(T0=0 to 1) of the animation, it is the fraction of total duration at which the command begins
- [2] T1: Specify the end time(T1=0 to 1) of the animation, it is the fraction of total duration at which the command ends
- [3] Tranparancy: Specify the tranparancy value (0-100) of the selected parts
- [4:] sPartlist: Specify the part names list (Wild card character '*' is supported)


PA_PARTCOLOR
**************

This command changes material color of the selected parts.

.. code-block::

    PA_PARTCOLOR,T0=starttime,T1=endtime,Color[R,G,B],sPartlist


- [1] T0: Specify the start time(T0=0 to 1) of the animation, it is the fraction of total duration at which the command begins
- [2] T1: Specify the end time(T1=0 to 1) of the animation, it is the fraction of total duration at which the command ends
- [3:5] Color: Specify the RGB value of color(floats 0 to 1) for the selected parts
- [6:] sPartlist: Specify the part names list (Wild card character '*' is supported)



PA_COLORPLOT
*************

This command sets the color plot animation On/Off for the selected parts.

.. code-block::

    PA_COLORPLOT,T0=starttime,T1=endtime,Color Plot(Y/N),sPartlist


- [1] T0: Specify the start time(T0=0 to 1) of the animation, it is the fraction of total duration at which the command begins
- [2] T1: Specify the end time(T1=0 to 1) of the animation, it is the fraction of total duration at which the command ends
- [3] Color Plot(Y/N): Specify if color plot animation is to be turned On(Y) of Off(N) for the selected parts
- [4:] sPartlist: Specify the part names list (Wild card character '*' is supported)


PA_CAEANIM
***********

This command plays the CAE Animation.

.. code-block::

    PA_CAEANIM,T0=starttime,T1=endtime,nFrames,Animtype(0/1/3),bDeform(Y/N)


- [1] T0: Specify the start time(T0=0 to 1) of the animation, it is the fraction of total duration at which the command begins
- [2] T1: Specify the end time(T1=0 to 1) of the animation, it is the fraction of total duration at which the command ends
- [3] nFrames: Specify the number of frames for smoother video capture
- [4] Animtype: Specify the CAE Animation type:

    - 0: Linear Animation
    - 1: Transient Animation
    - 3: Animating contour color based on Legend Palette using transparency

- [5] bDeform: Specify if deformed or undeformed CAE Animation is required

To use current animation settings: AnimType=NA,nFrames=0


PA_SHOWHIDE
************

This command shows or hides the selected parts.

.. code-block::

    PA_SHOWHIDE,T0=starttime,T1=endtime,Show/Hide Parts(Y/N),sPartlist


- [1] T0: Specify the start time(T0=0 to 1) of the animation, it is the fraction of total duration at which the command begins
- [2] T1: Specify the end time(T1=0 to 1) of the animation, it is the fraction of total duration at which the command ends
- [3] Show/Hide Parts: Specify if the selected parts are to be shown(Y) or hidden(N)
- [4:] sPartlist: Specify the part names list (Wild card character '*' is supported)


ViewPoint
==========


SELECT_VPATH
*************

This command selects the user-defined ViewPath and ViewPoint.

.. code-block::

    SELECT_VPATH,ViewPath Name,VP index

- [1] Viewpath Name: Specify the user-defined ViewPath Name
- [2] VP index: Specify the user-defined ViewPoint index


Insert Video / Image File
==========================


INSERT_VIDEO
*************

This command inserts the video from a user-specified file path.

.. code-block::

    INSERT_VIDEO,filepath

- [1] filepath


INSERT_IMGFOLDER
*****************

This command inserts images from a user-specified folder path.

.. code-block::

    INSERT_IMGFOLDER,folderpath

- [1] folderpath


Capture Images
===============


CAPUTRE_WAIT
*************

This command waits on a GUI display for a specified number of frames before capturing the next motion.

.. code-block::

    CAPUTRE_WAIT,nFrames

- [1] nFrames: Specify the user-defined number of frames


CAPTURE_IMAGE
**************

This command captures the current view as image.

.. code-block::

    CAPTURE_IMAGE


Save Video to File
===================


SAVE_VIDEO
************

This command saves the video in the user-defined file path.

.. code-block::

    SAVE_VIDEO,filepath,iSpeed[-4 to 3]

- [1] filepath: Specify user-defined location(along with filename and extension) for saving the video
- [2] iSpeed: Specify speed of the video, -4 being the slowest and 3 being the fastest


Others
=======


SHOWCMDS
*********

This command enables displaying the given commands.

.. code-block::

    SHOWCMDS,bCmd=Y/N

- [1] bCmd: Specify to show commands by Y/N, default is N(False)


EXIT
*****

This command stops the execution of command statements.

.. code-block::

    EXIT

- No Arguments