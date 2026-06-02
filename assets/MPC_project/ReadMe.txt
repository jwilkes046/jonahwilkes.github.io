MMAE 549
Final Project
Alec Weedman and Jonah Wilkes


Rocket Landing Model Notebook
-----------------------------
File: rocket_landing_model.ipynb

This notebook runs the main 3D rocket booster landing simulation. It compares a constrained Model Predictive Control (MPC) controller against a PD baseline controller for both nominal and wind-disturbed landing cases. The model includes gravity, drag, fuel usage, thrust limits, tilt limits, dry-mass limits, and engine cutoff conditions. The notebook prints the final landing metrics and saves the simulation data to rocket_landing_results.npz.

Note,  this solver optimizes the outcome of each case. These optimizations can vary between runs, despite the same weights. This solver averages a nominal solution at ~155sec. For the 134sec run presented in our paper, do NOT run this code, just look at the original print from this .ipynb. Otherwise, this code can be run as-is.

Instructions to Run:
1. Open rocket_landing_model.ipynb in Jupyter Notebook or JupyterLab.
2. To generate new simulation results, set:
   LOAD_DATA_INSTEAD = False  -> controls whether the notebook runs the simulation, or loads previously saved results.
   SAVE_DATA = True           -> saves data as a .npz file, for reprinting, saving and animating
   RUN_WIND_CASE = True       -> runs the wind case in addition to the nominal cse
3. Run the single cell.
4. The notebook will save the main results file as:
   rocket_landing_results.npz
5. If MAKE_ANIMATIONS = True and FFmpeg is available, animations will also be saved.




Rocket Landing Results Loader Notebook
--------------------------------------
File: rocket_landing_results_loader.ipynb

This notebook loads the saved rocket_landing_results.npz file from the main simulation notebook. It reprints the nominal and wind-case performance metrics, recreates the MPC vs. PD comparison plots, and saves the final figures and animations. The plots include position, velocity, speed, horizontal error, mass, thrust magnitude, thrust components, tilt angle, and 3D landing trajectories.

Instructions to Run:
1. Run rocket_landing_model.ipynb first so that rocket_landing_results.npz exists.
2. Open rocket_landing_results_loader.ipynb, and make sure rocket_landing_results.npz is in the same folder as this notebook.
3. Run the cell.
4. The notebook will create an images folder and save figures there as PDF and PNG files.
5. If SAVE_ANIMATIONS = True, the notebook will also save MP4 animations to the images folder. If FFmpeg is not available, it may save GIF files instead.
