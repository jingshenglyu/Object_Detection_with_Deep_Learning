

<!--
 * @Author       : Jingsheng Lyu
 * @Date         : 2020-08-13 18:07:34
 * @LastEditors  : Jingsheng Lyu
 * @LastEditTime : 2020-08-13 22:37:59
 * @FilePath     : /undefined/home/jingsheng/Object_Detection_with_Deep_Learning/Chapter2/Environment_Setup.md
 * @Github       : https://github.com/jingshenglyu
 * @Web          : https://jingshenglyu.github.io/
 * @E-Mail       : jingshenglyu@gmail.com
-->
# Environment Setup

* Operation System: Linux - Ubuntu 18.04 LTS
* Time: 13.08.2020
* Author: Jingsheng Lyu

## 0. Uninstall anaconda, if you had an old anaconda 
```
rm -rf ~/anaconda
```

## 1. Install Anaconda 
### 1.1. Visit [Anaconda Web](https://www.anaconda.com/) --> Get Started -->  Install Anaconda Individual Edition --> [Download](https://www.anaconda.com/products/individual) --> For Linux: 64-Bit (x86) Installer (550 MB)
* You will get a file named Anaconda3-2020.07-Linux-x86_64.sh

### 1.2. Open a terminal
1.2.1 Copy the file to your folder
```
mkdir software
cp Anaconda3-2020.07-Linux-x86_64.sh /home/USER_NAME/software/
```
1.2.2 Install

```
cd /home/USER_NAME/software/
bash Anaconda3-2020.07-Linux-x86_64.sh
```

* Welcome to Anaconda3 2020.07 
In order to continue the installation process, please review the license agreement. Please, press ENTER to continue
    * Press ENTER
    * This license is very lang. If you want to skip the license-reading, enter `Ctrl + C`

* Do you accept the license terms? [yes|no]
    * input `yes`

* Anaconda3 will now be installed into this location:
/home/jingsheng/anaconda3

  - Press ENTER to confirm the location
  - Press CTRL-C to abort the installation
  - Or specify a different location below

    '' *If you want to change the path for installation, you can write down the path here. For example...* ''

[/home/jingsheng/anaconda3] >>> /home/jingsheng/Software/anaconda3

* Do you wish the installer to initialize Anaconda3
by running conda init? [yes|no]
[no] >>> 
    * Enter `yes`

## 2. Install detectron2
### 2.1 Create an enviroment named detectron2
* Detectron2 need a version for python >= 3.6. 
    * Please install not the new python-version **but python=3.6**, because after that we will install OpenCV, we need the python-version<=3.6 in 08.2020.
    ```
    conda create --name detectron2 python=3.6
    ```
* Press `y` for finished

* Input `conda env list` to check if you have already installed an enviroment named detectron2
    * You will get the followed information.
        ```
        # conda environments:
        #
        base                  *  /home/jingsheng/Software/anaconda3
        detectron2               /home/jingsheng/Software/anaconda3/envs/detectron2
        ```

### 2.2 Enter this new enviroment named detectron2
* Acticate the enviroment named detectron2
    ```
    conda activate detectron2
    ```
    * You will see the input area of this terminal is not (base) but (detectron2)

* Deactivate the enviroment named detectron2
    ```
    conda deactivate
    ```

## 2.3 Install pytorch and other libraries
* For PyTorch
    * [PyTorch](https://pytorch.org/) --> Get Started --> Choose the version for your PC --> **copy the command in the terminal**

* For OpenCV
    ```
    conda install --channel https://conda.anaconda.org/menpo opencv3
    ```
    * *** Python Version for OpenCV ***
    *If your python version is >= 3.6, you will get ***the followed error*** because of the conflict.
        ```
        Solving environment: failed with initial frozen solve. Retrying with flexible solve.
        Solving environment: - 
        Found conflicts! Looking for incompatible packages.
        This can take several minutes.  Press CTRL-C to abort.
        failed                                                                                                                                                          

        UnsatisfiableError: The following specifications were found
        to be incompatible with the existing python installation in your environment:

        Specifications:

          - opencv3 -> python[version='2.7.*|3.4.*|3.5.*|3.6.*']

        Your python: python=3.8

        If python is on the left-most side of the chain, that's the version you've asked for.
        When python appears to the right, that indicates that the thing on the left is somehow
        not available for the python version you are constrained to. Note that conda will not
        change your python version to a different minor version unless you explicitly specify
        that.
        ```
* For Cython and pycocotools
    ```
    pip install cython; pip install -U 'git+https://github.com/cocodataset/cocoapi.git#subdirectory=PythonAPI'
    ```

* Finally, you can input `conda list` by the actual enviroment to check if you have already installed all libraries you need.

## 2.4 Build Detectron2 from Source
* Go to [Detectron2 Github](https://github.com/facebookresearch/detectron2) --> [**INSTALL.md**](https://github.com/facebookresearch/detectron2/blob/master/INSTALL.md)

* You can choose a way to build Detectron2
    * Open a new terminal
    ```
    cd /home/USER_NAME/
    mkdir Code
    cd Code/
    git clone https://github.com/facebookresearch/detectron2.git 
    conda activate detectron2
    python -m pip install -e detectron2
    ```

## 3. Download the dataset from [COCO](https://cocodataset.org/#download)
* Here we need to download  
    * For images
        1. 2017 Train images [118K/18GB]
        2. 2017 Val images [5K/1GB]
        3. 2017 Test images [41K/6GB]
    * For Annotations
        1. 2017 Train/Val annotations [241MB]
        2. 2017 Testing Image info [1MB]


## 4. Install PyCharm
### 4.1. Download [PyCharm](https://www.jetbrains.com/pycharm/) --> Community (if you want to more functions, choose Professional, but it is not free)
* Open a new terminal
    ```
    cd /[Download-Path]/pycharm-community-2020.2/bin
    sh pycharm.sh
    ```

    * ***You can create a new **desktop entry** for start quickly. (Tools --> Create Desktop ENtry... by PyCharm)
    
