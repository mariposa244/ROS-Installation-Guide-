# ROS-Installation-Guide-
This comprehensive guide offers a detailed walkthrough for setting up the Robot Operating System (ROS) on a virtual machine, leveraging the power of VirtualBox and the Ubuntu 20.04 operating system. By following these step-by-step instructions, users will be able to seamlessly install and configure ROS on a virtual environment, opening up a world of possibilities for robotics development, experimentation, and learning. The guide covers all the necessary steps, from downloading the required software to configuring the virtual machine and installing the ROS distribution, ensuring a smooth and efficient setup process. Whether you're a seasoned robotics enthusiast or just starting your journey, this guide will provide you with the essential knowledge and tools to get your ROS-powered projects up and running in a virtual sandbox, allowing you to explore and develop your robotic applications with ease and confidence.


# step 1: Download and Install VirtualBox
Open your web browser and go to the [VirtualBox website] (https://www.virtualbox.org/). and then chose the version that fits your device.
![image](https://github.com/user-attachments/assets/cb0b96a3-4985-4bcd-b789-d323f6832cff)


# Step 2: Download Ubuntu 20.04 Desktop Image
Open your web browser and go to [the Ubuntu website](https://ubuntu.com/download/desktop).
![image](https://github.com/user-attachments/assets/d9c1603f-6b22-403b-920b-6e1f3f1f7c00)
Select "Ubuntu 20.04 LTS" and click on "Download".
Save the ISO file to your computer.

# Step 3: Create a New Virtual Machine in VirtualBox
## 1- Open VirtualBox and click on "New" to create a new virtual machine.
## 2-Name the machine (e.g., "Ubuntu 20.04") and choose the type of operating system as "Linux" and the version as "Ubuntu (64-bit)".
## 3-Set the memory size (RAM) (at least 2 GB is recommended) stick to the green reigon.
## 4-Set the size of the virtual hard disk (at least 25 GB is recommended) and click "Create".

# Step 4: Install Ubuntu 20.04
After creating the virtual machine, select it from the list in VirtualBox and click "Start".
the virtual machine would appear like the following image:
![telegram-cloud-photo-size-4-5827940071855212229-x](https://github.com/user-attachments/assets/fb923c05-915f-4b1f-a087-32c69f468fe0)
When a window appears showing that the machine failed to boot, choose the Ubuntu 20.04 ISO file you downloaded and click "Start"
![telegram-cloud-photo-size-4-5827940071855212230-x](https://github.com/user-attachments/assets/7c2c8759-c12c-4bb5-b23b-16cacaff1521)

and then Follow the on-screen instructions to install Ubuntu 20.04 on the virtual machine. and to avoid any errors go to settings> about> software updates and turn off the “Download updates while installing Ubuntu” option so that it does not update Ubuntu 20.04.
after that the OS will function perfectly :

![telegram-cloud-photo-size-4-5827940071855212227-y](https://github.com/user-attachments/assets/be868bc4-0590-4e89-9b81-c812b8e0265f)

#Step 5: Install ROS on Ubuntu 20.04
After installing and booting Ubuntu, open a terminal window. and follow the following steps :
## 1. Add Official Noetic repo to Ubuntu
The first step in installing ROS Noetic is to add the official ROS Noetic repository to Ubuntu 20.04 sources list file.

``` echo "deb http://packages.ros.org/ros/ubuntu focal main" | sudo tee /etc/apt/sources.list.d/ros-focal.list ```
## 2. Add official ROS keyring
The first method is to use the hkp://keyserver.ubuntu.com:80 Ubuntu key server. If this does not work, you can try to replace it with hkp://pgp.mit.edu:80. So, run the command below:

``` sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654 ```

The second method is to use the curl command to download the official ROS keyring and add it locally. but i found that the key server to work better

``` curl -sSL 'http://keyserver.ubuntu.com/pks/lookup?op=get&search=0xC1CF6E31E6BADE8868B172B4F42ED6FBAB17C654' | sudo apt-key add - ```
The output “OK”,  means the key has successfully been added.

## 3. Update the ROS package index
Next, we will update our Ubuntu system so as to get the ROS Noetic package information from the repository.
``` sudo apt update ```
## 4. Install ROS Noetic on Ubuntu 20.04
The package ros-noetic-desktop-full comes with all the packages in ros-noetic-desktop and also the perception (ros-noetic-perception) and simulation (ros-noetic-simulators) packages.

To install ros-noetic-desktop-full, run the following command:

``` sudo apt install ros-noetic-desktop-full ```
## 5. Set up ROS Noetic environment
The next step is to set up ROS Noetic environment. First source the setup.bash script in every bash terminal that use ROS, type:
``` source /opt/ros/noetic/setup.bash ```
Add in the .bashrc file located in your home directory to avoid running each time when you launch a new shell:
``` echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc ```
Verify by running the following command:
``` tail ~/.bashrc ```
For the changes to take effect, type:
``` source ~/.bashrc ```
After successfully installing ROS Noetic on Ubuntu 20.04, simply run the roscd command.
``` roscd ```
You will notice that the current directory of your prompt changes to  /opt/ros/noetic, which is where we installed Noetic.
We can also verify the installation by running roscore command in the noetic directory.  The output displays the ros distro and the ros version in the summary. 

```roscore```
![telegram-cloud-photo-size-4-5827940071855212225-x](https://github.com/user-attachments/assets/8c646c48-8724-4843-8eee-a61ffbc8d1ab)

Now you can program your robots using Noetic.


