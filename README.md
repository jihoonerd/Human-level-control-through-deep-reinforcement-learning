# Human-level control through deep reinforcement learning

![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https://github.com/jihoonerd/Human-level-control-through-deep-reinforcement-learning)

![atlantis](/assets/atlantis.gif)
![boxing](/assets/boxing.gif)
![breakout](/assets/breakout.gif)
![Pong](/assets/pong.gif)


This repository implements the notable paper: **[Human-level control through deep reinforcement learning](https://www.nature.com/articles/nature14236)**.

This paper is widely known for a famous [video clip](https://www.youtube.com/watch?v=TmPfTpjtdgg), which surpasses human's playing by a large gap. The paper uses deep neural networks to map from complex visual information to optimal actions, known as Deep Q network.

## Features

* Employed ***TensorFlow 2*** with performance optimization
* Simple structure
* Easy to reproduce

You can see detailed explanation posting at ~[HERE]()~ (I am working on this yet :smile:)

## Requirements

Refer `requirements.txt` or `Pipfile`. You can set your virtual environment by `virtualenv`(*recommended*) or `pipenv`. 

***Default running environment is assumed to be CPU-ONLY. If you want to run this repo on GPU machine, just replace `tensorflow` to `tensorflow-gpu` in package lists.***

## How to install

### `virtualenv`

```bash
$ virtualenv venv
$ source venv/bin/activate
$ pip install -r requirements.txt
```
### `pipenv`

```bash
$ pipenv install
```

If you have trouble making virtual environment through `pipenv`, try followings:

Get your python interpreter by
```bash
$ which python
```
Use the python interpreter to make virtual environment.
```bash
$ pipenv install --three --python=[YOUR PYTHON PATH]
```

Also, in case of locking does not work, you can simply skip it.
```bash
$ pipenv install --skip-lock
```

## How to run

You can run Atari 2600 game with `main.py`. Running environment needs to be `NoFrameskip` from `gym` package.

```bash
$ python main.py --help
usage: main.py [-h] [--env ENV] [--train] [--play PLAY]
               [--log_interval LOG_INTERVAL]
               [--save_weight_interval SAVE_WEIGHT_INTERVAL]

Atari: DQN
optional arguments:
  -h, --help            show this help message and exit
  --env ENV             Should be NoFrameskip environment
  --train               Train agent with given environment
  --play PLAY           Play with a given weight directory
  --log_interval LOG_INTERVAL
                        Interval of logging stdout
  --save_weight_interval SAVE_WEIGHT_INTERVAL
                        Interval of saving weights
```

### Example 1: Train BreakoutNoFrameskip-v4

``` bash
$ python main.py --env BreakoutNoFrameskip-v4 --train
```

### Example 2: Play PongNoFrameskip-v4 with trained weights

```bash
$ python main.py --env PongNoFrameskip-v4 --play ./log/[LOGDIR]/weights
```

### Example 3: Control log & save interval

```bash
$ python main.py --env BreakoutNoFrameskip-v4 --train --log_interval 100 --save_weight_interval 1000
```

## Results

This implementation is guaranteed to work well for `Atlantis`, `Boxing`, `Breakout` and `Pong`. Tensorboard summary is located at `./archive`. Tensorboard will show following information:

* Average Q value
* Epsilon (for exploration)
* Latest 100 avg reward (clipped)
* Loss
* Reward (clipped)
* Test score
* Total frames

```bash
$ tensorboard --logdir=./archive/
```

Single RTX 2080 Ti is used for the results below. (Thanks to [@JKeun](https://github.com/JKeun) for allowing his computation resources)

### Atalntis

![atlantis](/assets/atlantis_result.png)

### Boxing

![boxing](/assets/boxing_result.png)

### Breakout

![breakout](/assets/breakout_result.png)

### Pong

![Pong](/assets/pong_result.png)


## BibTeX

```
@article{mnih2015humanlevel,
  added-at = {2015-08-26T14:46:40.000+0200},
  author = {Mnih, Volodymyr and Kavukcuoglu, Koray and Silver, David and Rusu, Andrei A. and Veness, Joel and Bellemare, Marc G. and Graves, Alex and Riedmiller, Martin and Fidjeland, Andreas K. and Ostrovski, Georg and Petersen, Stig and Beattie, Charles and Sadik, Amir and Antonoglou, Ioannis and King, Helen and Kumaran, Dharshan and Wierstra, Daan and Legg, Shane and Hassabis, Demis},
  biburl = {https://www.bibsonomy.org/bibtex/2fb15f4471c81dc2b9edf2304cb2f7083/hotho},
  description = {Human-level control through deep reinforcement learning - nature14236.pdf},
  interhash = {eac59980357d99db87b341b61ef6645f},
  intrahash = {fb15f4471c81dc2b9edf2304cb2f7083},
  issn = {00280836},
  journal = {Nature},
  keywords = {deep learning toread},
  month = feb,
  number = 7540,
  pages = {529--533},
  publisher = {Nature Publishing Group, a division of Macmillan Publishers Limited. All Rights Reserved.},
  timestamp = {2015-08-26T14:46:40.000+0200},
  title = {Human-level control through deep reinforcement learning},
  url = {http://dx.doi.org/10.1038/nature14236},
  volume = 518,
  year = 2015
}
```

## Author
Jihoon Kim ([@jihoonerd](https://github.com/jihoonerd))
