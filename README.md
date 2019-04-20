## CS744
### Big Data Systems @ UW-Madison


Assignment 1 :
==============
[Problem Statement](http://pages.cs.wisc.edu/~akella/CS744/S19/assignment1_html/assignment1.html)

[Solution](https://github.com/chakshuahuja/CS744/tree/master/Assignment%201)

Technologies: Apache Spark and Scala

Assignment 2 :
==============
[Problem Statement](http://pages.cs.wisc.edu/~akella/CS744/S19/assignment2_html/assignment2.html)

[Solution](https://github.com/chakshuahuja/CS744/tree/master/Assignment%202)

Technologies: TensorFlow and AlexNet

Project 1:
==========
##### System Support for Elastic ML Model Training

Problem Statement :

ML Model Training for supervised learning tasks takes as input a parameterized ML model and a training dataset. The training involves learning the right set of parameters for this ML Model for maximizing accuracy on the training dataset. Stochastic Gradient Descent (SGD) is a common technique to learn these parameters. However, the size of datasets and models has grown progressively and it is difficult to do this training on a single machine. A common strategy to scale ML Model Training across multiple machines is Data Parallelism. Data Parallelism involves spawning multiple workers. Each worker keeps the latest copy of the model parameters and computes gradients on exclusive mini-batches of the dataset in each iteration followed by a synchronous gradient exchange for gradient aggregation and updating the model parameters at each worker. This process repeats over multiple iterations until convergence.


Existing ML Model Training frameworks such as PyTorch, Tensorflow, Caffe, etc. are inelastic. The number of workers is user input and remains fixed across iterations in these frameworks. This can lead to head-of-line blocking - wherein if all the compute resources in a shared cluster are occupied by workers from already running training jobs then a training job that has just arrived needs to wait until a job vacates the compute resources required by the new training job’s workers. 


In this project, you will design and implement a system to enable elastic ML model training. This will involve making open source contributions to the Apache Hadoop Submarine Project [1] and Tensorflow. Submarine enables spawning Tensorflow containers for distributed ML Model training with Tensorflow and is an up-and-coming “Major” Priority project in the Hadoop community [1]. The contributions will touch upon three aspects. First, you will design and implement an API between Tensorflow and Submarine. This API will enable passing application-level metrics such as loss value per iteration from Tensorflow to Submarine. Submarine will use these application-level metrics and job arrival/departure events to decide the updated number of workers for a job. Second, you will enable mechanisms in Submarine to achieve changing the number of workers associated with a ML model training job during runtime. Third, towards the end you will collaborate with the team working on [DM1] to integrate transparent gradient aggregation in Horovod/Tensorflow with Submarine.

References:
[Hadoop {Submarine} Project: Simple and scalable deployment of deep learning training / serving jobs on Hadoop](https://issues.apache.org/jira/browse/YARN-8135)
