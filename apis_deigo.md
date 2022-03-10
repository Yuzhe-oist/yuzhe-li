# How to set up APIS on deigo 
## Base Pakages needed for APIS  on deigo : 
### Type I: Already installed on deigo
- git: already installed (check by: `git --version`)
- make:already installed (check by:`make --version`)
- java-jdk: already installed (check by:`java --version` )
### Type II:  come with python3.9 (need to install python3.9, see below conda env)
- python3-venv: pre-installed with python3.9 (check by:`virtualenv --version`)
- python3-pip: pre-installed with python3.9 (check by:`pip --version`)
### Type III: need to install manually on deigo
- mave: (check by:'mvn --version` or `mvn -v`)
- groovy:  (check by:`groovy --version`)
- mongodb-org
### Type IV: X-clinent on your local PC
SSH is already installed on the Mac. If you want to display graphics, you first need to install a piece of software called XQuartz. The installation is straightforward:

download Xquartz from this page
click it to open.
agree to the install.
You may need to restart the computer to make it work.



## 1. Quick install of mave and mongodb-org
### 1. copy the binary source code to a folder under /home 
you can copy from my folder on Deigo: `/home/y/yuzhe-li/apps`. 
Or you can also find the download instructions  below. 
### 2. Manually add the directory of bin to $PATH
`export PATH="$PATH:$HOME/apps/maven/bin:$HOME/apps/mongodb/bin"`

## 2. groovy: sdk install 
ref: https://groovy-lang.org/install.html#_maven_repository
### SDKMan install 
Simply enter the following commands:
- `curl -s get.sdkman.io | bash`
- `source "$HOME/.sdkman/bin/sdkman-init.sh"`
- `sdk install groovy`

### directory 
groopy is installed at: $HOME/.sdkman/candidates





## 3. Build and Run APIS on deigo 
### 1. Copy APIS to deigo 
`scp -r localpath_of_apis-master yourname@deigo.oist.jp:/home/anypath`

### 2. Build 
#### 1. ask for allocation computation node 
`srun -p compute -t 1:00:00 --pty bash`
#### 2. build 
`make build`

### 3. Run 
#### 1. aks for allocation computation node with x11
`srun -p compute -t 1:00:00 --x11 --pty bash`

#### 2. run 
`make run`


____________________



## Install miniconda on deigo 
ref: https://conda.io/projects/conda/en/latest/user-guide/install/linux.html
### Download minconda installer 
Download minconda installer (.sh) from https://docs.conda.io/en/latest/miniconda.html, and move it to deigo under any folder of /home.
### Install miniconda 
Install by running: `bash Miniconda3-latest-Linux-x86_64.sh`
### create conda env assining python version (3.9)
`conda create -n apis python=3.9`
### activate a conda env 
`conda activate apis`
### other useful commonds of conda env 
- check all envs: `conda info --evs`
- deactivate: `conda deactivate`



## maven: manually install maven on deigo 
ref:https://maven.apache.org/install.html
### Download binary distribution of maven 
- Download https://maven.apache.org/download.cgi
- unzip, and move the folder to deigo under any folder of /home 

### Manually add directory to Path
add the path of bin to PATH 
`export PATH=$PATH:/maven/path/bin/`
for example: `export PATH=$PATH:/home/y/yuzhe-li/apps/maven/bin`

$PATH might be automatically cleaned up everytime when you login to deigo again, in that case need to add path every time before use, write in makefile.

### check if maven is installed 
`mvn -v`
### useful command of PATH
check PATH:
`echo "$PATH"`
or `echo "${PATH//:/$'\n'}"`


## mongodb: manually install mongodb on deigo
### 1. Download binary version of installer 
https://www.mongodb.com/try/download/community
- Download .tgz version for CentOS. 
- untar the intsllar, and scp the folder to deigo:/home
### 2. add /bin to PATH
for example:
`export PATH = $PATH:/home/y/yuzhe-li/apps/mongodb/bin`






