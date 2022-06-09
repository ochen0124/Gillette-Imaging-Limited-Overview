Engineering Addendum
Gillette Imaging - Team 19

Welcome to our README! In this guide, you will find how to set up our software using the anaconda virtual environment set up, followed by a basic introduction to Numpy STL, the main python library used in this project. Next, we will outline the gotchas of our project, types of things to look out for, the current state of the project, future goals and anything else needed to pick up the project from where it is!

How to install the project software stack from scratch
To ensure that all systems such as Windows, MacOs, and Linux can run our code, we have decided to use Anaconda as a virtual environment that houses all the necessary dependencies and configurations. As a result, no individual component is required to be downloaded on a personal computer as these components will be automatically installed on the Anaconda environment.

In your preferred directory in local machine, run the following code in the terminal:

git clone https://github.com/wooae/gillette-bu-cad.git
Then, set up the Anaconda environment please use the follow steps:

1. Download Anaconda Navigator
Go to https://www.anaconda.com/ and locate the Individual Edition inside the Products drop down menu. Install the correct edition for your operating system.

2. Create the FiveRazors virtual environment
Once installed, you may notice that there is a "base" default environment inside the Anaconda Navigator. We will not be using that base environment as it does not contain all the necessary dependencies and packages required for our code. To create the FiveRazors virtual environment. Download the file named "environment.yml" inside the "gillette-bu-cad/anaconda/" folder. This file hosts all the packages required. You can feel free to open up the environment.yml file in any code editor and in the first line of code, change what you want your new environment to be called. By default it is called FiveRazorsTest. Locate the directory where you installed Anaconda and drop the "environment.yml" file inside that folder. Open up the terminal under the same folder and run the following command:

cd gillette-bu-cad/anaconda
conda env create --file environment.yml
conda activate FiveRazorsTest
This will create a new environment with the name specified in the first line of the "environment.yml" file as well as install all the dependencies and packages needed in that new environment.

3. Check that the new virtual environment is running properly (Optional)
Once your new virtual environment is created, you can run:

conda list --name yourEnvironmentName
This command will list all the packages and versions of the environment you just installed Once your new virtual environment is created, open Anaconda environment and change the "Channel" to your new environment. You can try running JuypterLab and running the ipynb file which will try to import numpy stl and create a new stl file. If a new cube stl file is created then you have successfully created a working Anaconda environment for FiveRazors' code.

After setting up the virtual environment, type in the following code to run the program:

cd ..
python MainloopGUI_v5.py
Numpy STL Documentation How-To
1. Creating Mesh
To create a 3D object, we use numpy STL's "mesh". To create one, we must locate the vertices and from there we add surfaces that are each composed of three of those vertices to form triangles.
newcube = mesh.Mesh(np.zeros(yourcube.shape[0], dtype=mesh.Mesh.dtype))

2. Input of STL file
To input an stl file from file "NAME.stl":
your_mesh = mesh.Mesh.from_file('NAME.stl')

3. Output of STL file
To write the mesh to file "NAME.stl":
newmesh.save('NAME.stl')

4. How to read in vertices from numpy STL
As we cannot directly modify the mesh objects, we must first obtain an array of their vertices:
e.g.: yourcube = your_mesh.vectors
From here, we can append a numpy array to create a flash ('vertices' are coordinates of a defect made out of two triangles):
yourcube = np.append(yourcube,vertices, axis=0)

Further Information
Our project uses the Numpy STL library as the basis for every edit made to the STL objects. To achieve the desired defects on the output files, we had to exploit the features of this library as described in the Software Read me.

Currently, our project performs four defects well. These include: shortshot, flash, splay, and surface delamination. Our GUI that is written in Python does the job well but it is not the most aesthetic one out there. To improve upon this, we would recommend using REACT for a modernized look.

Moreover, After creating the virtual environment with the environment.yml file and activating it. It may be easier to go on Anaconda Navigator, change the channel to the new environment and run our main loop code through VSCode. Make sure that the VSCode interpreter is set to FiveRazorsTest.

Further, The .stl files that our code runs on are Binary STL files as opposed to ASCII STL. Due to this, there are only non-standard possibilities of adding color to our .stl files to highlight locations of defects and changes. These non-standard practices of VisCAM and SolidView are third-party softwares that are difficult to integrate into our current working code. Therefore, we explored other options such as showing a preview of the 3D-model of the .stl file with matplotlib.

Our recommendation for future directions with this project include implementing a machine learning model and refining the current defects. This machine learning model could be trained using images created by the current project. To refine the current defects, here are a few ideas on how what could be improved:

Opacity: often in production line defects, edges can be transparent as the plastic is a lot thinner. We could add some sort of gradient going from opaque to transparent to replicate this.

Rounded edges: as of now, our defects have hard cuts, but in the real world, defects are often smoother and look a little more natural.

Implementing different shapes: currently, our defects follow the same rectangular pattern. To improve on this, we could use a randomized function to create defects based off of different shapes.
