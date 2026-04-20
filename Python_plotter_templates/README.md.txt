These Python scripts use SDF-xarray to extract and plot data from sdf files produced by EPOCH. An environment can be set up to use these by opening a Linux terminal and running:

```
python3 -m venv epoch_env
source epoch_env/bin/activate
pip install sdf-xarray
```

We can rejoin an environment which has already been created by re-running the activate script through source

```
source epoch_env/bin/activate
```

Once in an environment, the scripts can be run from the same Linux terminal using (for example):

```
python3 plot_1d_density.py 
```

These scripts are provided as examples to show how the package may be used, but **they will not work immediately** in their current form. These scripts point to data using commands like:

```
input_dir = Path("datasets/4_3_basic_target")
```

These paths are read as being relative to your current working directory. In this example, it will only work if your current working directory contains "plot_1d_density.py", and your sdf files are in the subdirectory "datasets/4_3_basic_targets". You can change this to point to your data of interest.

Additionally, when you open your data-set using a line like:

```
ds = sdfxr.open_dataset(input_dir / "0000.sdf", keep_particles=True)
```

Any subsequent variables referenced by ds, like ds["Particles_Px_Electron"], will refer to output variables associated with a specific input deck. If you have different variables printed by your output-block, or have species-blocks with different names, you will have to change the names of the variables you access. The sdf-xarray documentation provides instructions on how to check what variables are present in your file.

Finally, there are rare compatability issues when running some features with sdf-xarray, particularly with 2D GIFs. A "legacy" directory has also been included, if you experience issues with plotting 2D GIF files.

These plotters work at the time of writing, but they will not be maintained after the workshop. See SDF-xarray online documentation for the latest changes if these scripts no longer function.