# BTV POG Exercise

Welcome to the BTV POG Exercise held at CMSPO&DAS@Hamburg 2023!

## Intro
A set of slides with introductory material, definitions, useful links is available at [Indico](https://indico.desy.de/event/38207/contributions/152481/).
<!-- ## Setup with SWAN
Connect to https://swan.cern.ch/

If you are a participant of CMSPO&DAS@Hamburg 2023 for this POG exercise, chances are all you need to do is to go to pick the default environment (no additional environment script necessary, no paths), choose 10GB memory, and then navigate to Share -> Projects shared with me to find the project called „CMS-PODAS-2023-POG-Ex-BTV“. Pick this project, it will contain all the relevant notebooks for the exercises.

If you come here independently, no need to worry. Start similar, pick the default environment, choose 10GB memory, click the Console symbol on the top navigation bar ("New terminal") and proceed with these commands:
1. Checkout the exercise repository into new directory (example directory given below for convenience)
```shell
mkdir -p ~/SWAN_projects/POG-Exercises
cd ~/SWAN_projects/POG-Exercises
git clone https://gitlab.cern.ch/cms-podas23/pog/b-tagging.git -b podas
```
2. Start ipython notebooks via SWAN  
You can now go back to the browser tab you started with that holds your SWAN projects. Navigate to the recently cloned directory and open the individual exercises from the `notebooks` folder. -->

## Setup with lxplus
To start with the exercises, perform these initial steps for the setup at lxplus (e.g. after doing `ssh -l your-lxplus-username@lxplus.cern.ch` from your own machine):

1. Get Miniconda (if you have not yet done so in another exercise)
```shell
wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh
```
Special note: installation may take a while, therefore we recommend (if possible) to start early with the instructions. 

2. Checkout this repository into new directory (example directory given below for convenience)
```shell
mkdir -p ~/private/Tagging
cd ~/private/Tagging
git clone https://gitlab.cern.ch/cms-podas23/pog/b-tagging.git -b HATS2024
```
(_Alternatively, if you don't have your ssh-key connected to github, replace the above URL with `https://gitlab.cern.ch/cms-podas23/pog/b-tagging.git` in the command_)

3. Install relevant python packages into a conda-environment (comes with the Git repo)
```shell
conda env create -f env.yml
```
4. Connect to a screen session (start jupyter lab server) and open in browser
```shell
screen -S server
```
In that new screen-session, make sure to have the active conda environment:
```shell
conda activate btag-Tutorial
```  
and start a jupyter lab server with forwarding to a specific port (choose a random four-digit number, don't all choose the same - the 7890 is just an example, do not use 7890!)
```shell
jupyter lab --no-browser --port=7890
```
Note down the machine you were working with (most likely, something like naf with XY some numbers. Note down the port you have chosen above. Copy-paste the first http-link presented to you after starting the jupyter server instance, this should be opened by you in a new web browser tab on your own machine. In this first ssh connection, you may detach from the screen via `Ctrl + A` (hold `Ctrl`) followed by `Ctrl + D`. One can always go back to this screen-session via `screen -r server`. From a new ssh-terminal (**on your own machine!**), connect to the port on which you started the server, pick the exact machine you worked with for the previous step:
Example:
```shell
ssh -L 7890:localhost:7890 username@lxplus934.cern.ch
```
General case, to be filled by you:
```shell
ssh -L port-you-picked:localhost:port-you-picked your-naf-username@lxplusXYZ.cern.ch
```
Now open the http-link from jupyter lab in your browser and navigate to the short exercise. All packages to work with the exercises should be available from there, you don't need to use the terminal from now on, just keep the session open while you're working.

## Tutorials
All individual tutorials / exercises are available from the `notebooks` directory. There are three .ipynb files which are plug-and-play, just (double-)click to open in SWAN (jupyter lab) and follow the instructions inside.

### Inputs, Targets and Tagger Outputs
Explore the inputs which are used to perform jet flavour tagging with some example files. Understand what the machine learning algorithms need to predict by investigating the targets, and compare with what the taggers actually do when passing inputs through the networks by looking at the output scores.
### Performance
Learn how network performance is evaluated and which performance metrics play a key role for flavour tagging. Perform more studies to evaluate performance as a function of certain parameters and compare across samples.
### Bonus
Explore how performance depends on kinematic quantities related to the jet. This is one concept to keep in mind, differential distributions *do* matter (not only inclusive metrics), in this case explored for simple features like pseudorapidity and transverse momentum. Most likely you will also need to adapt to differentially measured scale factors (in bins of disciminators, though) when using such algorithms in an analysis.
## Contact
**_Spandan Mondal, 2024_**  
:email: [spandan.mondal@cern.ch](mailto:spandan.mondal@cern.ch)

Orignal credits to:
**_Annika Stein, 2023_**  
:email: [annika-stein@cern.ch](mailto:annika-stein@cern.ch), :computer: [@AnnikaStein](https://github.com/AnnikaStein)