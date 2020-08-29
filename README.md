# Welcome to the African IXP Observatory

This project is a fork from https://github.com/CoNexDat/latam-ixp-obs

The aim of this project is to study the evolution of the African IXP fabric by using the methodology as described in: https://dl.acm.org/doi/pdf/10.1145/3390251.3390255

## 1. System pre-requisits

### 1.1 Install pip3

```
sudo apt-get -y install python3-pip
```

### 1.2 Install JupyterLab

```
sudo pip3 install jupyter
```

More about JupyterLab: (https://www.digitalocean.com/community/tutorials/how-to-set-up-jupyter-notebook-with-python-3-on-ubuntu-18-04)

## 2. Install BGPdump


BGPdump home page: (https://bitbucket.org/ripencc/bgpdump/wiki/Home)

### 2.1 System pre-requesitis

```
sudo apt-get install autoconf zlib1g-dev libbz2-dev liblzma-dev
```

### 2.2 Install


```
sudo apt install mercurial
hg clone https://bitbucket.org/ripencc/bgpdump
cd bgpdump
sh ./bootstrap.sh
make
sudo make install
# Remember to go back to whatever directory where you’d like to create the working space
cd ..
```

## 3. Enabling repo working space

### 3.1 System pre-requisits

```
sudo apt-get install python3-venv
```

It might be necessary to upgrade pip3


```
sudo pip3 install --upgrade pip
```


### 3.2 Clone repo

Time to finally clone this repo


```
git clone git@github.com:AFRINIC-Labs/africa-ixp-obs.git
```


### 3.3 Create python’s virtual environment

To the ones who are not familiar with, ```venv``` the following lines will create a local copy of Python 3 as well as all libraries necessary to run our code (scripts and notebooks).
Having a local copy of Python's library will isolate our working space from the rest of the OS, which prevents dealing with broken package dependencies.

More info: (https://docs.python.org/3/library/venv.html)

```
cd latam-ixp-obs
python3 -m venv latam-ixp-obs
source latam-ixp-obs/bin/activate
pip3 install ipykernel
ipython kernel install --user --name=latam-ixp-obs
pip3 install -r requirements.txt
```

## 4. Reproduce and replicate 

Our entire research was documented in Jupyter Notebooks, where code is displayed along with results.
However, in case you would like to **rerun** our code, we provide two scripts ```fetch_data.sh``` and ```run_notebooks.sh```.
The former script invokes several python script to fetch a wide variety of datasets (BGP table dumps, delegation files, etc) from different data providers (PCH, RouteViews, etc.).
We decided to take a _non-aggresive_ download strategy to avoid overwhealming data repositories as well as users connection.
Hence, it could take long (even more than a day) to download the entire dataset.
The latter script will rerun our analyses.
To avoid overwritting source files, after latest results will appear on new notebooks in ```notebooks/v4/RERUN_*.ipynb``` 


To download our dataset (whether you are interested or not in rerunning the notebooks)
```
sh fetch_data.sh
```

To rerun our notebooks
```
sh run_notebooks.sh
```

To open any of our notebooks (either source notebooks or rerun ones) from repo's root

```
jupyter notebook notebooks/v4/NOTEBOOK_FILE_NAME
```
