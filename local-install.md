# Installing the CheckIt Platform locally

## Windows

### Windows Subsystem for Linux

We recommend using the Windows Subsystem for Linux, because the Windows version of Sage can't be run on the Windows command line. Instructions for installing Ubuntu on WSL are [here](https://ubuntu.com/wsl).

### Updating to current versions of various things
Once your WSL is installed, run your shiny new Ubuntu shell and issue the following commands:
```
sudo apt-get update -y && apt-get upgrade -y
sudo apt install sage jupyter
pip install --upgrade pip
export PATH="$HOME/.local/bin:$PATH"
```

### Installing python modules with pip 
Eventually we should bake this into a `requirements.txt` but:
```
pip install jupyterlab lxml latex2mathml pystache
```

### getting widgets working correctly
You'll need to do [some crap involving `nvm` and `nodejs`](https://docs.microsoft.com/en-us/windows/dev-environment/javascript/nodejs-on-wsl).

Once that's done:
```
pip install --upgrade ipywidgets
sudo jupyter nbextension enable --py --sys-prefix widgetsnbextension
jupyter labextension install @jupyter-widgets/jupyterlab-manager
jupyter lab clean
jupyter lab build
```

### Cloning the project from github

You will probably need a new ssh key for github since your WSL install is probably fresh. Follow the directions to [generate a new key](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) and then [add it to your GitHub account](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account). Don't do this thing it says with "clip" because that doesn't work for some reason in WSL. Instead, do `cat .ssh/id_ed25519.pub`, highlight the string that comes out, and right-click. Now it's on your Windows clipboard and you can paste it into the web gui.

Then you can [follow the directions from the GitHub checkit repo](https://github.com/StevenClontz/checkit#developing-the-checkit-dashboard).
