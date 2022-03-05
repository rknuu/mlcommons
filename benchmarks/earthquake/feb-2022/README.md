# Running the code

To run this code, you have two pathways:

1. Using the native python ecosystem via `pip`, or
2. Using the conda ecosystem.

## GET THE DATA

```bash
mkdir earthquake
wget https://github.com/laszewsk/mlcommons-data-earthquake/raw/main/data.tar.xz
tar xvz data.tar.xz
mv data EarthquakeDec2020
```

this will create all data files in the mv data `EarthquakeDec2020` drectory


## Running using pip from the commandline



To preserver the original code, we first create a copy

```
cp FFFFWNPFEARTHQ_newTFTv29.ipynb FFFFWNPFEARTHQ_newTFTv29-$USER.ipynb 
```

To run this code using pip, execute

```bash
python -m venv --prompt mlcommons-science venv
source venv/bin/activate # or .\venv\Scripts\activate.bat on windows
python -m pip install -rrequirements.txt
jupyter nbconvert --to notebook --execute FFFFWNPFEARTHQ_newTFTv29-$USER.ipynb
```

To see the output, you d need to open the notebook

If you are interested in doing interactive development, you can install the 
developer-focused modules by running 

```bash
source venv/bin/activate # or .\venv\Scripts\activate.bat on windows
python -m pip install -rrequirements-dev.txt
jupyter lab .
```

## Running using Conda

To get this running in Conda, run

```bash
conda env create -f environment.yml
conda activatge mlcommons-science
jupytext --to py:percent FFFFWNPFEARTHQ_newTFTv29.ipynb
python FFFFWNPFEARTHQ_newTFTv29.py
```

If you're interested in doing interactive development, you can install the developer-focused modules by running

```bash
conda activate mlcommons-science
python -m pip install -rrequirements-dev.txt
jupyter lab .
```

## Building the container image

To build a container image of the entire benchmarking system (but not run the benchmark), you can run the commands

```bash
# If running docker
$ docker image build --tag mlcommons-science-earthquake:latest
# If running nerdctl
$ nerdctl image build --tag mlcommons-science-earthquake:latest
```