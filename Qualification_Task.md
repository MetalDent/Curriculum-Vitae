### Qualification Task:

I've completed the qualification task T1162 related to this project.
    
The task was to decrease the image size of the apertus° logo used on the firmware visualizer. The current image has 8-bit depth which is drawn using the DrawImage() method in Painter. I decreased the depth to 1-bit (black and white) and created a new method to draw the logo, DrawIcon().
    
To decrease further the total logo size, I dissected the "apertus°" logo into two parts: the text part, apertus and the ring, ° and drawn them separately using [DrawIcon()](https://github.com/MetalDent/AXIOM-Remote/blob/dev/Firmware/UI/Painter.cpp#L311-L329) method. 
    
For all the image manipulations, I used Imagemagick. The changes which are done on the original apertus° logo are written in [this](https://github.com/MetalDent/AXIOM-Remote/blob/dev/Firmware/Media/Images/convert.sh) file.
    
 The method reads a byte data from the image header file and then the method ProcessByte() gets 8 bits out of that byte and if the bit is '1' then it draws the pixel with the given color which was passed as a parameter.
                
 For the DrawIcon() method, I have also written a [unit test](https://github.com/MetalDent/AXIOM-Remote/blob/dev/FirmwareTest/PainterTest.cpp#L184-L202).
        
To test it, I used an image as an input and did all the manipulations which are done on the logo and then created an [expected output array](https://github.com/MetalDent/AXIOM-Remote/blob/dev/FirmwareTest/Images/logo_output.h).
        
In the test it is checked that the DrawIcon()'s output matches with the expected output array.
