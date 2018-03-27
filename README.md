
# Expanding the work of Jean Harb, Pierre-Luc Bacon, Martin Klissarov and Diona Precup

## Fixes I had to do in order to make the code run:

- Install the dependencies
- Make sure that .theanorc has floatX=float32 configured
- Lasagne is incompatible with the latest version of Theano. You need to manually edit it and change "from theano.tensor.signal import downsample" to "from theano.tensor.signal.pool import pool_2d" and then corresponding function calls, so instead of downsample.max_pool_2d you will now simply call pool_2d.


# Original content from forked repo:


# When Waiting is not an Option : Learning Options with a Deliberation Cost

Arxiv link: https://arxiv.org/pdf/1709.04571.pdf

## Installation

Here's a list of all dependencies:

- Numpy
- Theano
- Lasagne
- Argparse
- OpenAI Gym [Atari]
- matplotlib
- cv2 (OpenCV)
- PIL (Image)

## Training

To train, run following command:
```
python train.py --sub-env Breakout --num-options 8 --num-threads 16 --folder-name Breakout_model
```

To view a list of available parameters, run:
```
print train.py --help
```

During training, you can run utils/plot.py to view the training curve. Every argument given can be a path to a different run, which will put all runs on the same plot.
```
python utils/plot.py models/Breakout_model/ models/Breakout_model_v2/ models/Breakout_model_v3/
```

## Testing

To watch model after training, run watch.py and give it the path the saved model files. e.g.:
```
python watch.py models/Breakout_model/
```

