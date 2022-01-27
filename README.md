# ParaDySE 

ParaDySE (Parametric Dynamic Symbolic Execution) is a tool 
that automatically generates search heuristics for concolic testing. 
The tool is implemented on top of [CREST][crest], 
a publicly available concolic testing tool for C.

## Install ParaDySE. 
You need to install [Ubuntu 16.04.3(64 bit)][ubuntu].
Then follow the steps:
```sh
$ sudo apt-get install ocaml #(if not installed) 
$ git clone https://github.com/kupl/ParaDySE.git 
$ cd ParaDySE/cil
$ ./configure
$ make
$ cd ../src
$ make
```

## Automatically generate a search heuristic.
The script for automatically generating a search heuristic is run on an instrumented program. 
For instance, we can generate a search heuristic for **tree-1.6.0** as follows:
```sh
$ screen 
# Initially, each benchmark should be compiled with ParaDySE:
$ cd ParaDySE/benchmarks/tree-1.6.0
$ make
$ cd ~/ParaDySE/scripts
$ python fullauto.py pgm_config/tree.json 1000 20 
```

Each argument of the last command means:
-	**pgm_config/tree.json** : a json file to describe the benchmark.
-	**1000** : the number of parameters to evaluate in **Find Phase**
-	**20** : the number of cpu cores to use in parallel

If the script successfully ends, you can see the following command:
```sh
#############################################
Successfully Generate a Search Heuristic!!!!!
#############################################
```

[crest]: https://github.com/jburnim/crest
[ubuntu]: https://www.ubuntu.com/download/desktop
[FSE]: https://dl.acm.org/citation.cfm?id=2635872&CFID=1004243459&CFTOKEN=16632066
