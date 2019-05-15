## Visualize Legged Robot Trajectories with Unreal Engine
The goal of this project was to exlore the capabilities of Game Engines for fancy robot motion visualization. The Trajectories were generated with [towr](https://github.com/ethz-adrl/towr), but any trajectories specified through endeffector and base positions can be used. Unreal's internal Inverse Kinematics function calculates the corresponding joint angles. I built the level using assets from the free Unreal Slum Environment. Hope you like it :)

**Youtube:** *https://youtu.be/zXK70yU8tw0*

[<img src="https://i.imgur.com/zm2nwF7.png" height="45" />](https://github.com/ethz-adrl/towr "Towr Github") &nbsp; &nbsp; &nbsp; &nbsp; [<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/20/UE_Logo_Black_Centered.svg/1200px-UE_Logo_Black_Centered.svg.png" height="55" />](https://www.unrealengine.com/en-US/feed?sessionInvalidated=true "Unreal Engine")

[![Watch Youtube video](https://i.imgur.com/oO0LI2p.jpg)](https://youtu.be/zXK70yU8tw0)

## Usage
To experiment with this project, playback your own motions or change the camera shots, feel free to download
this repo, open the `towr.uproject` with the Unreal Editor and then follow the steps below.


#### 1. Get the reference trajectory
I already generated some trajectories for the robot to follow in `Content/TowrTrajectories/`. These are CSV (comma separated values) files, that define the motion of the feet and the base at every time instance. 

You can also generate your own trajectories from ROS bags generated by towr. To convert towr bag files into CSV file data.txt (replace with the name of your towr.bag):
```bash
rostopic echo -b towr.bag -p /xpp/state_des > data.txt
```

#### 2. Tell Unreal which file to playback
You can specify which CSV trajectory the engine should use, by clicking on the "Robot" Actor in the Editor, and in the "Details" tab find the Slot "Towr Trajectory". Now hitting "Play" in the Editor will now cause the robot to move.

#### 3. Optional: Save the playback as Unreal Animation
Unreal provides the option to save motions in their own file format, which makes it easy to work with later. I've converted the provided examples to Unreal Animations, which can be found under `/Content/Robot/TowrAnimations/`. 

These animations were generated using the Unreal "Sequence Recorder". Select the "Robot" Actor and click "Add". Then make sure you hit the "Play" button in the 
Editor first, then the "Record" button in the Sequence Recorder. This otherwise causes problems. In the Recording settings, make sure you have:
- `Record in World Space` -> checked
- `Remove Root Animation` -> unchecked (because we want the root to move).

#### 4. Generate movie sequences 
After all the Animations are saved, you can stitch them together, move the camera around in neat ways and play with level and lighting. Unreal Provides the "Sequencer" for this. To see the sequence I setup to generate the Youtube video, open `Content/Cinematics/YoutubeVideo`.

