Pytext Lab
------------
This lab uses DocClassification to evalute if a SMS text is a SPAM or not. The dataset used to train the model was [**SMS Spam Collection Data Set**](https://archive.ics.uci.edu/ml/datasets/sms+spam+collection) which has 2 features, category {ham, spam} and the sms text.

Install
-------
```
$ virtualenv venv --python=python3
$ source venv/bin/activate
$ pip install -r requiriments.txt
```
Train
------
```
$ pytext train < ./configs/docnn.json
```
Test
------
```
$ pytext test < ./configs/docnn.json
```
Export
------
```
$ pytext export --output-path exported_model.c2 < ./configs/docnn.json
```
Run
------
```
$ python flask_app.py ./configs/docnn.json exported_model.c2
```
Example
-----
```
$ function ask_about() { curl http://127.0.0.1:8080/is_spam -H "Content-Type: text/plain" -d "$1" }
$ ask_about 'You have won a car, please call 000 111 222'
{
  "type": "spam"
}
ask_about 'Hi, your package has already sent.'
{
  "type": "ham"
}
```
---
https://pytext-pytext.readthedocs-hosted.com/en/latest/index.html
