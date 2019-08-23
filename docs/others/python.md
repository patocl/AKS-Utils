# Python Topics

Python is an interpreted, object-oriented, high-level programming language with dynamic semantics. Its high-level built in data structures, combined with dynamic typing and dynamic binding, make it very attractive for Rapid Application Development, as well as for use as a scripting or glue language to connect existing components together. Python's simple, easy to learn syntax emphasizes readability and therefore reduces the cost of program maintenance. Python supports modules and packages, which encourages program modularity and code reuse. The Python interpreter and the extensive standard library are available in source or binary form without charge for all major platforms, and can be freely distributed.

## Installing Python

On ubuntu systems

To updaye apt-get and force upgrade of this module

``` bash
sudo apt-get update && sudo apt-get upgrade
```

Install python 3.7

``` bash
sudo apt-get install python3.7
```

## Updating Python

To Update python

``` bash
sudo apt-get update python3.7
```

## Dealing between python 2.7 and python 3.7

Python have 2 realeases that are bein used, so sometimes is needing use an specific version of it

To install modules for python 2.7 you should use **pip** command.

Esample

``` bash
pip install numpy
```

To install modules for python 3.7 you should use **pip3** command.

Esample

``` bash
pip3 install numpy
```

## getting the version of Python

``` bash
python --version
```

``` bash
python3 --version
```

## Creating an alias to python3.7

Esample

``` bash
pip install numpy
```

## to install **pip3**

``` bash
sudo apt install python3-pip
```

## Installing Requiremments.txt

Some modules have dependencies than are described on requirements.txt file To install dependencies based on requirements.txt file

``` bash
pip3 install -r requirements.txt
```
