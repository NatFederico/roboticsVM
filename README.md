# Parallels VM for M1 and M2 Mac
> This guide presumes you have paralles installed on your Mac - dosen't matter how you've got it  as long as it's working on ARM architectures.

The [VM you've received](https://drive.google.com/drive/folders/1Q6OkYr6agKa93yyv6uFuvo9Ly5jnFkvd?usp=sharing) is **almost** ready to use and, if you follow the instructions correctly, you should be ready in no time.

## Adding Locosim

Once you've started the virtual machine [ **password:** `/roboarm` ] open terminal and go straight to your catkin workspace from your home and clone the locosim repo:   
```console
cd ros_ws/src/
git clone https://github.com/mfocchi/locosim.git
```
Once you've cloned the repo in your workspace, in order to be able to use the submodules, you'll need to generate an SSH key to add to your GitHub account.

### Setting up GitHub
In order to setup your GitHub account on your terminal you'll need to run:
```console
git config --global user.name "username"
git config --global user.email "youremail@github.com"
```
Now, using your preferred browser, go on GitHub and head over to **Settings** (you can find them by clicking your profile pic in the top right corner) - and you'll find the **SSH and GPG keys** where you'll be able to add the SSH key we're going to generate next.

Going back to the console we'll head right over the `/.shh` folder and generate our key:
```console
cd ~/.ssh/
ssh-keygen
```
Once prompted give a name to the key (I'd reccomend robotics) - and then execute cat to copy and paste it on your GitHub
```console
cat robotics.pub
```
Once you've added the key to your GitHub account, we can finish up setting up locosim, head back to terminal and execute:
```console
cd ~/ros_ws/src/locosim
git submodule update --init --recursive
cd ~/ros_ws
catkin_make install
rospack profile
```
I've already configured the enviroment variables, so you don't have to worry about it.

## Up and running with Python
In the VM you'll find alreasy Pycharm installed (**do not update it!**) and you can execute it from terminal using the command `pycharm`.  
As your first time operning it there are a few step to follow:
- Open one of the projects already in locosim like `locosim/robot_control/base_controllers/base_controller_fixed.py`  
- Check if you are using the correct interpeter `/usr/binpython3.8` - but it should have picked it up automatically
- To be able to keep the plots alive at the end of the program and to have access to variables, you need to "Edit Configurations..." and tick "Run with Python Console". Otherwise the plot will immediately close.  
And now you can run whater project you wanna work on just by using:
```console
python3 -i ~/ros_ws/src/locosim/robot_control/base_controllers/base_controller.py
```

Created by [Federico Natali](https://github.com/natfederico) for the Fundamentals of Robotics course at [UniTN](https://www.unitn.it)
