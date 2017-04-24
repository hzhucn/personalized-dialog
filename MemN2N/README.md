# MemN2N Chatbot in Tensorflow

Implementation of [Learning End-to-End Goal-Oriented Dialog](https://arxiv.org/abs/1605.07683) with sklearn-like interface using Tensorflow. Tested on the [bAbl](https://research.facebook.com/research/babi/) dataset and our modified dataset. Built on top of [this](https://github.com/vyraun/chatbot-MemN2N-tensorflow) code.

![MemN2N picture](https://www.dropbox.com/s/3rdwfxt80v45uqm/Screenshot%202015-11-19%2000.57.27.png?dl=1)

### Usage

Train the model

```
python single_dialog.py --train True --task_id 1 --interactive False
```

Running a [single bAbI/modified task](./single_dialog.py) Demo

```
python single_dialog.py --train False --task_id 1 --interactive True
```

### Requirements

* tensorflow
* scikit-learn
* six
* scipy

### Results - bAbI Tasks

Unless specified, the Adam optimizer was used.

The following params were used:
* epochs: 200
* learning_rate: 0.01
* epsilon: 1e-8
* embedding_size: 20

Task  |  Training Accuracy  |  Validation Accuracy  |  Testing Accuracy	 |  Testing Accuracy(OOV)
------|---------------------|-----------------------|--------------------|-----------------------
1     |  99.9	            |  99.1		            |  99.3				 |	76.3
2     |  100                |  100		            |  99.9				 |	78.9
3     |  96.1               |  71.0		            |  71.1				 |	64.8
4     |  99.9               |  56.7		            |  57.2				 |	57.0
5     |  99.9               |  98.4		            |  98.5				 |	64.9
6     |  73.1               |  49.3		            |  40.6				 |	---

### Results - Modified Tasks

Unless specified, the Adam optimizer was used.

The following params were used:
* epochs: 30 (Task 1), 10 (Task 2)
* learning_rate: 0.01
* epsilon: 1e-8
* embedding_size: 20

Task  |  Training Accuracy  |  Validation Accuracy  |  Testing Accuracy	 |  Testing Accuracy(OOV)
------|---------------------|-----------------------|--------------------|-----------------------
1     |  99.2	            |  98.9		            |  98.8				 |	74.4
2     |  99.9               |  99.8 	            |  99.8				 |	78.8

### Notes

I didn't play around with the epsilon param in Adam until after my initial results but values of 1.0 and 0.1 seem to help convergence and overfitting.