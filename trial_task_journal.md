# Journal of Triumphs and Failures in the DLC Trial Task 
## Reorganize data into appropriate directory structure
### Notes
1. Figure out difference between line 14 and line 32 of pyvm/metadata file (behavior range fields)
2. Use video monkey env (the one in videomonkey folder, not the one in the sharma folder!!)
3. Change code to allow monkey name in directory
## Copy checkerboard movies by hand 
### Come on we can automate this... seriously??
## Checkerboard calibration
### Smooth, with properly setup environments
One exception is that the selected frames for each camera were misaligned with the actual camera ordering, leading to out of bounds issues. This, however, is only a problem in this particular run.
## Preprocessing :(
### Lots of issues here, mainly with CUDA.
Fun fact nvidia drivers are apparently the #1 way to break ubuntu 18.04
1. Follow this guide to get nvidia and cuda drivers squared away. Whatever you think is the correct way to do it is probably wrong :). If the guide doesn't work then, well, it's between you, God, and a new linux distro.
2. Use the [yaml file](https://github.com/Danhan71/hand_track_shid/blob/18d60b0771d00f87dea14a5138a94c5f11fc9c13/test.yaml) in this directory, idk why this one works and the other three that you can find tucked away don't, but it does. You will still have the pip install -e all the relevant items (DLC, pyvm, pylib).
## Handlabelling Frames
smooth just make sure you have the proper infrastructure to attach your conda environments to jupyter notebooks, and read the "Help" popup when labelling the videos for useful information about how to do it! Also ensure that when you click next the previous image keeps the dots you placed. If not thee might be an issue (happened to me with the wand category, just closed and tried again and it worked...).
```bash
#if not already had
mamba install jupyerlab
mamba install -c anaconda ipykernel
python -m ipykernel install --user --name=[YOUR ENV NAME]
#Done
```
Might also need to install pytorch 
```bash
mamba install pytorch
```
## Train DLC Models
Here got a bit annoying. If the screen shows a bunch of errors and then says "Starting Training" but nothing else after that, it has not, in fact, started training and you must address those those errors. For me the issue was that pytorch was not installed and also that python version was out of date. CUDA REQUIRES PYTHON VERSION >3.9!!!!!!!. To update python version just do a
```bash
conda install python=3.9
```
After doing this you will need to go and re add all the custom libraries (dlc, pyvm, and pylib).
If, after doing this you still have issues and see an error like ```Value Error: ‘a’ must be greater than 0 unless no samples are taken``` this probably means that your labelling did not work for some of the videos, and thus there is no training data avaliable.

## Refine Labels
The videos were decent, however here were some skipping frames/random jumps/wrong finger ids so I did the refine labels step. This step went smoothly, although the GUI for refining the extracted frames was a bit shoddy, e.g. it was not obvious which folders/files were the ones to click on and everytime you wanted to access a new folder the GUI would have to be closed and the code rerun, also it crashed sometimes. This may have been a dependency error though, I am not sure.

## Extract campy data
Smooth, no issues here. However, I could not figure out the "inspect data" Jupyter notebook part.

## Wand Calibration
Had a slight issue with file naming, the program was searching for ...```*100000*``` ... when my files had a 10000 in them (the model went through 10k instead of 100k iterations. I think somewhere along the way some config file must have gotten messed up since 100000 iters is the normal amount and I believe there was an analysis step thsat was run with maxiters was set to 100k so perhaps that is the issue. Or maybe 100k is hardcoded somewhere, time will tell.

## DLTdv8


