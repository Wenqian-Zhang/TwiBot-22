### Preprocessing framework for Twitter bot detection
---

- **authors**: Mücahit Kantepe, Murat Can Ganiz

- **link**: https://ieeexplore.ieee.org/abstract/document/8093483

- **file structure**: 

```python
├── Twibot-20
│   ├── preprocess.py
│   └── train.py  # model on cresci-2015 and Twibot-20 
└── Twibot-22
    ├── preprocess.py
    └── train.py  # model on Twibot-22 
```

- **implement details**: In the original paper, the Gradient Boosted tree classification method has the best effect, but in our experiment, the effect of this method is significantly worse. The SVM method with the second best effect in the original paper is relatively better in our experiment, but the experiment is time-consuming. Since the core
of this paper is feature selection rather than classification methods, we finally use the random forest method.

  

#### How to reproduce:

1. convert the raw dataset into standard format by running 

   `python preprocess.py`

   this command will create related features in corresponding directory.

2. train random forest model by running:

   `python train.py`

   the final result will be showed.



#### Result:

random seed: 0, 100, 200, 300, 400

| dataset     |      | acc   | precison| recall| f1    |
| ----------- | ---- | ----- | ------- | ----- | ----- |
| Cresci-2015 | mean | 0.975 | 0.813   | 0.753 | 0.782 |
| Cresci-2015 | var  | 0.001 | 0.001   | 0.002 | 0.001 |
| Cresci-2017 | mean | 0.982 | 0.830   | 0.761 | 0.794 |
| Cresci-2017 | var  | 0.001 | 0.000   | 0.001 | 0.001 |
| Twibot-20   | mean | 0.803 | 0.634   | 0.610 | 0.622 |
| Twibot-20   | var  | 0.003 | 0.001   | 0.000 | 0.002 |
| Twibot-22   | mean | 0.764 | 0.786   | 0.468 | 0.587 |
| Twibot-22   | var  | 0.002 | 0.001   | 0.002 | 0.002 |







| baseline | acc on Twibot-22 | f1 on Twibot-22 | type | tags|
| -------- | ---------------- | --------------- | ---- | --- |
| Varol et al.|0.764|0.587|F T|`random forest`|

