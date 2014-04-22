# IPython Notebook Desktop

This is a proof of concept desktop interface for the Ipython Notebook. 

## Concept
It's well established that IPython is awesome.

Most IPython users end up using local installs of the IPython notebook in their browser. However this is somewhat clunky, mixing the browser interface and the notebook interface and generally requiring a trip to the command line to get the server running.

The IPython Notebook Desktop wraps the webapp in a more friendly interface, powered by node-webkit. You can configure a notebook to run to power the interface (optionally have it run on startup).

What this does **NOT** do is provide you with a Python installation. This is deliberate, since people have different needs and tastes with regards to their python installs. Some people want to use the python bundled with their operating system, others use Python distributions like Canopy or Anaconda. With IPython desktop the python distribution and the interface are seperate, but you must confiure IPython desktop to use your IPython installation.

The IPython Notebook Desktop doesn't aim to make it easier to install a scientific python environemnt, but should be easy enough to get by itself. It could eventually be a candidate for bundling with existing packages or with IPython itself.


## Pretty pictures
IPython embedded

![Screenshot1](https://raw.githubusercontent.com/mangecoeur/ipython-desktop/master/assets/Screenshot1.png "Screenshot1")

Start Screen:

![Screenshot2](https://raw.githubusercontent.com/mangecoeur/ipython-desktop/master/assets/Screenshot2.png "Start screen")

Config Screen:

![Screenshot3](https://raw.githubusercontent.com/mangecoeur/ipython-desktop/master/assets/Screenshot3.png "Screenshot3")
https://raw.githubusercontent.com/mangecoeur/ipython-desktop/master/assets/Screenshot1.png

## Get it!
[App bundle for Mac](https://github.com/mangecoeur/ipython-desktop/blob/master/apps/ipython-desktop.zip)

You also need to have IPython installed. My personal recommendation is the Anaconda python distribution if you are mainly doing science and engineering work.

**Coming sometime - binary bundles for each platform. Contribuitions welcome**

## Configuration

Ipython desktop can either launch the Ipython notebook server for you or connect to an existing URL. To launch a server you must define an appropriate command (this will be made more user friendly in the future). Simply click the configure button on the start screen or go to the Server > Configure menu

**IMPORTANT** - you must supply the full path to your IPython install otherwise the mac bundle will fail to launch the ipython server

**WARNING:** ipython-desktop is by no means idiot proof at the moment. If you don't configure the command correctly the page will simply fail to load without explanation. This should improve in future versions.

By default, IPython-desktop attempts to launch the system default ipython using

`/usr/bin/ipython notebook --no-browser`

You can use all allowed ipython options, but you MUST keep the `--no-browser` option.

### Examples
Using an Anaconda virtual env (conda env)

`/Users/yourusername/anaconda/envs/yourenvname/bin/ipython notebook --no-browser`

Using a profile

`/Users/yourusername/anaconda/envs/yourenvname/bin/ipython notebook --no-browser --profile=myprofile`

Using an arbitraty ipython executable

`/foo/bar/env/bin/ipython notebook --no-browser`


### URL only
If you set the "remote" option in the config you can simply type in the URL of your IPython server **including `http://` at the front!** handy if you just want a nicer interface for a remote system or just for testing.


## Building ipython-desktop
In theory, the followin steps should work (on Mac):

Requirements - you must have Xcode developer tools installed as well as `nodejs` with `npm` and `grunt`. If you use Homebrew (and you should) just do brew install node. Then install Grunt via npm with `npm install grunt`.

In the terminal, `cd` to the source folder and run `npm install` then `grunt install` to set up the dependancies for ipython desktop, this might take a while. 

FINALLY you should be able to run `grunt run` and see you shiny new ipython-desktop app, ready to configure.

## Known Issues

- IMPORTANT - you must configure ipython desktop with the FULL PATH of your ipython executable
- Certain combinations of starting/stopping ipython servers and opening/closing windows might leave orphaned IPython processes (especially if you force quit the app)

## TODO
- Bundles for all OSes
- Add fault tolerance e.g. for missing or misconfigured Ipython
- More user friendly configuration of ipython
- better integration with ipython notebooks - start/stop events, clean shutdown
- Integration with Native menus!

## Similar Work
Enthought provide their Canopy desktop interface with IPython notebook integration. However this ties you into the EPD distribution. The IPython Notebook Desktop aims to be a lighter, more versatile solution


## Credits
IPython desktop is powered by Node Webkit and makes use of the angular-desktop-app template.

## LICENCE
This software is currently under LGPL licence.
