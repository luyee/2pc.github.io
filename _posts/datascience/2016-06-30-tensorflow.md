---
layout: post
title: "google tensorflow notes"
keywords: ["ML","mechine learning","SVM","","Dtree","classification","tensorflow"]
description: "svm"
category: "Datascience"
tags: ["ML","Datascience"]
---
## google tensorflow的安装

可以参考文档[Google tensorflow Download and Setup](https://github.com/tensorflow/tensorflow/blob/master/tensorflow/g3doc/get_started/os_setup.md#virtualenv-installation）,有很多中方式)

在自己的Mac上安装，这里选择了[Virtualenv installation](https://github.com/tensorflow/tensorflow/blob/master/tensorflow/g3doc/get_started/os_setup.md#virtualenv-installation)，也可以选择Anaconda或者其他安装方式

Install pip and Virtualenv:

```
sudo  pip  install --upgrade virtualenv 
```

Create a Virtualenv environment in the directory ~/tensorflow:

```
virtualenv   --system-site-packages  ./tensorflow
```
Activate the environment and use pip to install TensorFlow inside it:

```
tensorflow/bin/activate
pip install --upgrade https://storage.googleapis.com/tensorflow/mac/tensorflow-0.7.1-cp27-none-any.whl
```
When you are done using TensorFlow, deactivate the environment.

```
(tensorflow)$ deactivate
```
To use TensorFlow later you will have to activate the Virtualenv environment again:

```
source  tensorflow/bin/activate
```
 测试是否安装ok
 
 ```
 (tensorflow) bogon:develop luping$ python
Python 2.7.5 (default, Aug 25 2013, 00:04:04) 
[GCC 4.2.1 Compatible Apple LLVM 5.0 (clang-500.0.68)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import tensorflow as tf
>>> hello = tf.constant('Hello, TensorFlow!')
>>> sess = tf.Session()
>>> print(sess.run(hello))
Hello, TensorFlow!
>>> a = tf.constant(10)
>>> b = tf.constant(32)
>>> print(sess.run(a + b))
42
>>> 
 ```
 
实例学习[TensorFlow-Examples](https://github.com/aymericdamien/TensorFlow-Examples)
 
 ```
bogon$ git clone https://github.com/aymericdamien/TensorFlow-Examples.git
 ```

