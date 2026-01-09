---
title: Setup
---

## Connecting to cmslpc

Open a terminal/console, connect to `cmslpc-el9` and prepare your working area.

> ## Choose your port number
> Because we are forwarding jupyter notebooks to local browsers, you need to pick a 3-digit port number `XXX` in the ssh command:
{: .caution}

~~~
kinit username@FNAL.GOV
ssh -L localhost:8XXX:localhost:8XXX <YOUR USERNAME>@cmslpc-el9.fnal.gov
~~~
{: .language-bash}
### Folder structure
All your code should live in `~/nobackup/` area. 
You should have a folder structure like this:
~~~
~/nobackup/cmsdas/
├── preexercises 
├── Muon 
│   └── MuonDAS  <-- this is the repo
├── ShortEx2 
├── ShortEx3 
├── ... 
└── LongExercise
~~~
{: .language-bash}
### Commands to clone the code
~~~
source /cvmfs/cms.cern.ch/cmsset_default.csh
mkdir -P ~/nobackup/cmsdas/Muon
cd ~/nobackup/cmsdas/Muon
git clone git@github.com:FNALLPC/MuonDAS.git
~~~
{: .language-bash}
### Getting jupyter notebook from LCG software

The following commands one has to do it *everytime you log in into a new session*. They load the environment and the packages needed for the exercises and open a jupyter notebook:
~~~
source {{ site.LCG_path }} 
jupyter notebook --no-browser --port=8XXX --ip 127.0.0.1
~~~
{: .language-bash}

> ## Remember
> The port number `8888` needs to match the port number you log-in to `cmslpc`.
> 
> If someone has taken the `8888` port on the cmslpc node, you will need to use another one. 
{: .callout}

If those two lines are running sucessfully, you should see something like this:
~~~
[I 08:22:45.871 NotebookApp] Serving notebooks from local directory: /uscms_data/d2/pivarski/CMSSW_9_0_0_pre6/src
[I 08:22:45.871 NotebookApp] 0 active kernels 
[I 08:22:45.871 NotebookApp] The Jupyter Notebook is running at: http://localhost:8888/?token=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
[I 08:22:45.871 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
[C 08:22:45.873 NotebookApp] 
    
    Copy/paste this URL into your browser when you connect for the first time,
    to login with a token:
        http://localhost:8888/?token=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
~~~
{: .output}

Copy and paste one of the last two urls in your favorite browser and now you can continue with the lesson 1 (Episode 1).

### Useful tips
Since we launch jupyter server frequently, you can make an `alias` for that command in your `~/.bashrc` file
~~~
alias sourcelcg='source {{ site.LCG_path}}'
alias launchJupyter='jupyter notebook --no-browser --port=8XXX --ip 127.0.0.1'
~~~
{: .language-bash}
then you can just do 
~~~
sourcelcg
launchJupyter
~~~
after you login.
{: .language-bash}


{% include links.md %}
