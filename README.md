# ImJoy Plugin Engine
The plugin engine used for running python plugins in ImJoy (https://imjoy.io).

## Installation (Desktop App)

If you want to use the plugin engine from a desktop environment, download the latest ImJoy-App from [here](https://github.com/oeway/ImJoy-App/releases). Follow the instructions according to different operating systems.

You will get an executable file for starting the Plugin Engine.

## Installation (Linux servers/clusters)

For using it through a command line interface on a Linux host, run this command in your terminal to install the plugin engine:
```bash
wget https://raw.githubusercontent.com/oeway/ImJoy-Engine/master/utils/Linux_Install.sh  -O - | bash
```

NOTE: When you run the script above, it will first download and install Miniconda3 into `$HOME/ImJoyApp`, it may take considerably amount of space. If you want to uninstall it, run `rm -rf $HOME/ImJoyApp`.  

To start the plugin engine, run:
```
export PATH=~/ImJoyApp/bin:$PATH
python -m imjoy --host=0.0.0.0 --port=9527 --serve
```

Please notice that if you are trying to use ImJoy Plugin Engine running on a remote server, please use the ImJoy web App served on your server (`http://YOUR_REMOTE_IP:9527`) instead of `https://imjoy.io`. This is because most browser do not allow a web application served throught `https` to connect to a unsecured server (your remote server). Alternatively, you use proxy to enable `https` for the plugin engine, then you will be able to use it with `https://imjoy.io`.


## Installation (alternative solution)
  If you you have trouble in using the above ImJoyEngine, do the following:
  * Download and install [Miniconda with Python 3.7](https://conda.io/miniconda.html) (or [Anaconda with Python 3.6](https://www.anaconda.com/download/) if you prefer a full installation). If you have installed any of these, please skip this step.
  * Start a **Terminal**(Mac and Linux) or **Anaconda Prompt**(Windows), then run the following command:

    ```conda -V && pip install -U git+https://github.com/oeway/ImJoy-Engine#egg=imjoy```
  * If you encountered any error related to `git` or `pip`, try to run : `conda install -y git pip` before the above command. (Otherwise, please check **FAQs**.)
  * You can also use the same command if you want to upgrade the Plugin Engine to the latest version.

  To use it after the installation:
  * Run `python -m imjoy` in a **Terminal** or **Anaconda Prompt**, and keep the window running.
  * Go to https://imjoy.io, connect to the plugin engine. For the first time, you will be asked to fill a token generated by the plugin engine from the previous step.
  * Now you can start to use plugins written in Python.

## Upgrading

  Normally, the Plugin Engine will upgrade itself when it starts.
  In case you have problem with starting or upgrading the App, try to manually upgrade it by running the following command in a **Terminal**(Mac and Linux) or **Anaconda Prompt**(Windows):
  ```
  PATH=~/ImJoyApp/bin:$PATH pip install -U git+https://github.com/oeway/ImJoy-Engine#egg=imjoy
  ```

## Accessing the ImJoy Engine Conda environment
If you installed the Plugin Engine with the [ImJoyEngine](https://github.com/oeway/ImJoy-Engine/releases), it will setup an Miniconda environment located in `~/ImJoyApp`.

To access the environment on Linux and Mac, you just need to add `~/ImJoyApp/bin` to your `$PATH`:
```
export PATH=~/ImJoyApp/bin:$PATH

# now you can use `conda`, `pip`, `python` provided from ~/ImJoyApp
which conda

```
For windows, you can use powershell to add the ImJoyApp to `$env.Path`:
```
$env:Path = '%systemdrive%%homepath%\ImJoyApp;%systemdrive%%homepath%\ImJoyApp\Scripts;' + $env:Path;

# now you can use `conda`, `pip`, `python` provided from ~/ImJoyApp
(Get-Command conda.exe).Path

```

## Uninstall/remove ImJoy Engine
In order to uninstall or remove ImJoy Engine, you need to remove two folders located in your home/user folder: `ImJoyApp` and `ImJoyWorkspace`.

 * `ImJoyApp` contains a Miniconda environemnt and the virtual environemtns used for running ImJoy plugins
 * `ImJoyWorkspace` contains user data for each ImJoy workspace, you may want to backup the data.

On Linux/OSX, you can run the following command:
```
rm -rf $HOME/ImJoyApp   
rm -rf $HOME/ImJoyWorkspace # please backup important data inside this folder
```
On windows, it's typically located in `C:\Users\<CurrentUserName>`, you can remove `ImJoyApp` and `ImJoyWorkspace` manually.

## More details and FAQs in [Docs](http://imjoy.io/docs/#/user-manual)
