# Project 1: Navigation


This README demonstrates how to train and visualize a solution to the Navigation Project in the Udacity Deep Reinforcement Learning Nanodegree. It is adapted from the course README.

### Getting Started

1. Follow the instructions [here](https://github.com/udacity/deep-reinforcement-learning#dependencies) to set up the Deep Reinforcement Learning Nanodegree (DRLND) GitHub repository.

2. Replace the contents of `p1_navigation/` folder with this repository.

3. (Linux Only) To operate pytorch and tensorflow with CUDA and cuDNN:

```
conda activate drlnd

pip uninstall tensorflow
conda install -c anaconda tensorflow-gpu

pip uninstall torch
conda install pytorch torchvision cudatoolkit=9.0 -c pytorch
```

4. Download the environment from one of the links below.  You need only select the environment that matches your operating system:
    - Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux.zip)
    - Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana.app.zip)
    - Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86.zip)
    - Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86_64.zip)
    

5. In the DRLND GitHub repository, create a folder `deep-reinforcement-learning/unity_environments/`, place the downloaded environment inside, and unzip the file. 

### Training and Visualization

1. Navigate to `p1_navigation/` and run the following:

```
conda activate drlnd
jupyter notebook Navigation.ipynb
```

2. To train the environment without visualization, set the variable **visible_environment** to **False**. <br /> At the top of the jupyter notebook, click *Kernel -> Restart & Run All*. 

3. To train the environment *with* visualization, set the variable **visible_environment** to **True**. 
<br /> At the top of the jupyter notebook, click *Kernel -> Restart & Run All*. 

4. To visualize the trained environment, set the variable **visible_environment** to **True**. 
<br /> At the top of the jupyter notebook, click *Kernel -> Restart*.
<br /> Run each section _**except**_ for **3. Train the Agent with DQN**

