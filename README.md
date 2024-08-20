# Tagging HATS

Welcome to the Tagging HATS 2024!

## Intro
A set of slides with introductory material, definitions, useful links is available on [Indico](https://indico.cern.ch/event/1443889/sessions/560661/attachments/2913418/5112216/HATS2024.pdf).
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

### Option 1: Setup with Purdue AF


- Navigate to the [Purdue AF website](https://analysis-facility.physics.purdue.edu/) and click “Login to Purdue Analysis Facility”.
- On the CILogon page, choose CERN account to log in (using Fermilab or Purdue credentials is also possible).
- You will be redirected to the “Server Options” page. The default resource selection (4 CPUs, 16 GB RAM) is enough for the HATS exercises, but you can select more resources if needed. **Do not add GPUs** to your session – there are not enough GPUs for all participants.
- Click “Start” to create your Analysis Facility session. It may take a couple of minutes to load.
- Done! Your session is ready.

- On the left panel, click on the "Git" icon. Then click on "Clone a Repository".
- Paste this git path in the text box `https://gitlab.cern.ch/cms-analysis/cmsdas/pog/b-tagging.git`.
- Enter your CERN username and password in the prompt.
- Go back to the file browser by clicking on the top "File Browser" icon in the left panel. You should now see a new `b-tagging` directory.

- Open a terminal from the main workspace (under "Other").
- Type
```shell
cd b-tagging
conda env create -f env.yml     #This will take a while
python -m ipykernel install --user --name=FTAG-Tutorial
```

- Go back to the file browser and navigate to `b-tagging/notebooks`. Your exercise notebooks are available here. Open the first notebook to start the exercise.


### Option 2: Setup with lxplus
<details>
  <summary>Click here if you cannot set things up on Purdue AF...</summary>
Perform these initial steps for the setup at lxplus (e.g. after doing `ssh -l your-lxplus-username@lxplus.cern.ch` from your own machine):

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
git clone https://gitlab.cern.ch/cms-analysis/cmsdas/pog/b-tagging.git -b HATS2024  # Enter your CERN username and password when prompted
cd b-tagging
```

3. Install relevant python packages into a conda-environment (comes with the Git repo)
```shell
conda env create -f env.yml
```
4. Connect to a screen session (to start jupyter lab server and open in browser). A screen session ensures that your jupyter server keeps running within lxplus even if your ssh session get disconnected from lxplus.
```shell
screen -S server
```
Within that new screen-session, make sure to have the active conda environment:
```shell
conda activate FTAG-Tutorial
```  
and start a jupyter lab server with forwarding to a specific port (choose a random four-digit number XXXX: the 7890 is just an example, ***do not use 7890***!)
```shell
jupyter lab --no-browser --port=7890
```
Note down
- the machine you were working with (most likely, something like lxplusXYZ).
- the port you have chosen above.
- the first http-link presented to you after starting the jupyter server instance (something like http://localhost:XXXX...). You can copy this with `Ctrl/Cmd+C`

Useful `screen` commands: Within this ssh connection, you may detach from the screen via `Ctrl + A` (hold down `Ctrl`) followed by `D` (while `Ctrl` is pressed). One can always go back to this screen-session via `screen -r server` from the same lxplus machine.

On your **own laptop/machine**: from a new terminal, connect to the port on which you started the server (pick the exact machine you worked with for the previous step):
Example:
```shell
ssh -L 7890:localhost:7890 username@lxplus934.cern.ch
```
General case:
```shell
ssh -L XXXX:localhost:XXXX your-username@lxplusXYZ.cern.ch
```
Now open your browser and paste the http-link you copied. Navigate to `notebooks` on your left panel.

All packages to work with the exercises should be available from there, you don't need to use the terminal from now on, just keep the session open while you're working.
</details>

## Tutorials
All individual tutorials / exercises are available from the `notebooks` directory. There are three .ipynb files which are plug-and-play, just (double-)click to open and follow the instructions inside.

Jupyter tip: To run a command, click on it inside the Jupyter notebook and click the play button on the top panel. You can edit the command and rerun it by clicking the run button again. Click the play button again to run the next command, and so on.

### Inputs, Targets and Tagger Outputs
Explore the inputs which are used to perform jet flavour tagging with some example files. Understand what the machine learning algorithms need to predict by investigating the targets, and compare with what the taggers actually do when passing inputs through the networks by looking at the output scores.
### Performance
Learn how network performance is evaluated and which performance metrics play a key role for flavour tagging. Perform more studies to evaluate performance as a function of certain parameters and compare across samples.
### Bonus
Explore how performance depends on kinematic quantities related to the jet. This is one concept to keep in mind, differential distributions *do* matter (not only inclusive metrics), in this case explored for simple features like pseudorapidity and transverse momentum. Most likely you will also need to adapt to differentially measured scale factors (in bins of disciminators, though) when using such algorithms in an analysis.
## Contact
This session:

**_Spandan Mondal, 2024_**  
:email: [spandan.mondal@cern.ch](mailto:spandan.mondal@cern.ch), :computer: [@mondalspandan](https://github.com/mondalspandan)

Maintained by:

**_Sebastian Wuchterl, CMS PO&DAS 2023_**  
:email: [sebastian.wuchterl@cern.ch](mailto:sebastian.wuchterl@cern.ch), :computer: [@SWuchterl](https://github.com/SWuchterl)

**_Svenja Diekmann, CMS PO&DAS 2023_**  
:email: [svenja.diekmann@cern.ch](mailto:svenja.diekmann@cern.ch), :computer: [@SvenjaDiekmann](https://github.com/SvenjaDiekmann)


Orignal credits to:
**_Annika Stein, 2023_**  
:email: [annika-stein@cern.ch](mailto:annika-stein@cern.ch), :computer: [@AnnikaStein](https://github.com/AnnikaStein)