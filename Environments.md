# Setting up a new conda environment

An environment is essentially a set of packages installed together. You can create as many different environments as you like, with different packages installed, and even different versions of the same package. You can switch which environment you are using by activating or deactivating an environment.

To learn more about conda environments:

- [Conda environments](https://conda.io/projects/conda/en/latest/user-guide/concepts/environments.html)
- [Managing environments - conda documentation](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html) -- if you are comfortable using a terminal.
- [Managing environments - Anaconda Navigator](https://docs.anaconda.com/anaconda/navigator/tutorials/manage-environments/#creating-a-new-environment) -- if you prefer using Anaconda Navigator.

The default environment, when you install Anaconda, is called 'base', and includes by default all the packages that come pre-installed with Anaconda. Creating a new environment allows us to start fresh, and only include the packages that we need.

One way to do this is with an environment file. The conda documentation gives some examples; there is also an example `environment.yml` in this repo, which you can use or modify depending on the packages you want. Let's look at the content of the file:

- The name of the environment will be `migs-pp-23`.
- The conda packages that we want to install are listed under `dependencies:`.
- Note that the last package we install is `pip`. This is because some packages can't be installed directly with conda. `pip` is another utility which allows you to install packages.
- The packages that can only be installed with pip are listed under `- pip:`. Here, this is only the `py-openaq` package (which provides tools to retrieve air quality data -- this is just for the sake of example).

Now, we will use `environment.yml` to create the environment.

- If you use Anaconda Navigator:
    - In the "Environments" menu, click "Import" at the bottom.
    - Click on the folder icon in front of "Specification file", and select the file `environment.yml`. (You will need to download it first from here, or to create your own.)
    - Click "Import", and wait for the setup to finish.
    - Once it's done, your new environment `migs-pp-23` will appear below `base (root)`.
    - Select `migs-pp-23` to activate it, then go back to the "Home" menu, and launch Jupyter as usual. Jupyter will now be using your new environment.
- If you prefer using the terminal:
    - On Windows, launch Anaconda Prompt. On MacOS and Linux, launch the Terminal.
    - Run the command `conda env create -f path/to/environment.yml` and wait for the setup to finish. Replace the path by the actual path of the `environment.yml` file.
    - Once it's done, run the command `conda activate migs-pp-23` to activate your new environment. You can launch Jupyter after this by running the command `jupyter notebook`.

Remember to activate `migs-pp-23` before every time you launch Jupyter, otherwise it will use the base environment by default.

## Checking that it works

Activate your new `migs-pp-23` environment, open a .py script or a Jupyter notebook, and try the command `import openaq`. If it works, you're all set!
