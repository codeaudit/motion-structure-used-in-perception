# [UNDER CONSTRUCTION]

# motion-structure-used-in-perception
Python code and experiment data for Bill et al. "Hierarchical structure is employed by humans during visual motion perception" (2019). This repository allows you to:
* Generate figures 2, 3 and 4 from the main paper,
* Collect your own data,
* Run the full analysis pipeline (if you are willing to dig into the code, a bit).


__Remark:__ We assume a Ubuntu-based linux installation. On Mac, you should be able to homebrew with sip and pyqt.


## Installation

We suggest to use a virtual environment with Python 3.6+:

```
$ python3 -m pip install --user --upgrade pip   # Install pip (if not yet installed)
$ sudo apt-get install python3-venv             # May be needed for environment creation
$ python3 -m venv env                           # Create environment
$ source env/bin/activate                       # Activate env
$ python3 -m pip install --upgrade pip          # Make sure the local pip is up to date
$ pip3 install wheel                            # Install wheel first
$ pip3 install -r requirements.txt              # Install other required packages
$ deactivate                                    # Deactivate env
```

## Usage

__Always__ start your session by running `source run_at_start.sh` and end it with `source run_at_end.sh`. These will set up the virtual environment and python path. Here are some cookbooks.

### Plot figures

```
$ source run_at_start.sh
$ cd plot
$ python3 plot_fig_2.py   # Plot Figure 2
$ python3 plot_fig_3.py   # Plot Figure 3
$ python3 plot_fig_4.py   # Plot Figure 4
$ cd ..
$ source run_at_end.sh
```

All figures will be saved in './plot/fig/' as png and pdf.

### Collect your own data

#### MOT experiment

[Todo:
* Generate trials in python
* Trans-code to matlab
* Copy to Trials directory
* Make sure Psychtoolbox is set up
* Run thresholding
* Run test
* Copy results to data]


#### Prediction experiment

```
$ source run_at_start.sh
$ cd pred/gui
$ python3 play.py presets/example_trials/GLO.py -f -T 10   # EITHER: try out 10 trials (ca. 2 min)
$ ./run_full_experiment.sh -u 12345                        # OR: run the full experiment (ca. 75 min)
$ cd ../..
$ source run_at_end.sh
```
If you run the full experiment, your data will be stored in `/data/pred/myexp/`.
Please refer to [`/pred/gui/README.md`](./pred/gui/README.md) for further information -- especially to ensure a stable frame rate before running a full experiment.


### Analyze your own data

[Todo: Analysis chain]

... or use above analysis chain to recreate the data files provided in `/data` from the raw data in `/data/rmot/paper` and `/data/pred/paper`.

## List of directories

* `data`: Experiment data and simulation/analysis results
* `pckg`: Python imports of shared classes and functions
* `plot`: Plotting scripts for Figures 2, 3 and 4
* `pred`: Simulation and analyis scripts for the prediction task
* `rmot`: Simulation and analyis scripts for the rotational MOT task


## Miscellaneous

### Fonts

If the 'Arial' font is not installed already:

```
$ sudo apt-get install ttf-mscorefonts-installer
$ sudo fc-cache
$ python3 -c "import matplotlib.font_manager; matplotlib.font_manager._rebuild()"
```
...and if you really want it all: the stars in Figure 3 indicating significance use font type "FreeSans".

