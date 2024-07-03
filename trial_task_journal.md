# Journal of Triumphs and Failures in the DLC Trial Task 
## Reorganize data into appropriate directory structure
### Notes
1. Figure out difference between line 14 and line 32 of pyvm/metadata file (behavior range fields)
2. Use video monkey env (the one in videomonkey folder, not the one in the sharma folder!!)
3. Change code to allow monkey name in directory
## Copy checkerboard movies by hand 
### Come on we can automate this... seriously??
## Checkerboard calibration
### Pretty smooth, with properly setup environments
One exception is that the selected frames for each camera were misaligned with the actual camera ordering, leading to out of bounds issues. This, however, is only a problem in this particular run.
## Preprocessing :(
### Lots of issues here, mainly with CUDA.
Fun fact nvidia drivers are apparently the #1 way to break ubuntu 18.04
1. Follow this guide to get nvidia and cuda drivers squared away. Whatever you think is the correct way to do it is probably wrong :). If the guide doesn't work then, well, it's between you, God, and a new linux distro.
2. Use the yaml file in this directory, idk why this one works and the other three that you can find tucked away don't, but it does. You will still have the pip install -e all the relevant items (DLC, pyvm, pylib)

