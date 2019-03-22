# ResNet50
ResNet50 is a 50 layers residual nerual network.
In this project, I use it to classify hand signs.

The details of Identity Block are listed as follow:

First component of main path: 
- The first CONV2D has $F_1$ filters of shape (1,1) and a stride of (1,1). 
- The first BatchNorm is normalizing the channels axis.
- Then apply the ReLU activation function.

Second component of main path:
- The second CONV2D has $F_2$ filters of shape $(f,f)$ and a stride of (1,1).
- The second BatchNorm is normalizing the channels axis.
- Then apply the ReLU activation function.

Third component of main path:
- The third CONV2D has $F_3$ filters of shape (1,1) and a stride of (1,1).
- The third BatchNorm is normalizing the channels axis.

Final step: 
- The shortcut and the input are added together.
- Then apply the ReLU activation function.

The CONV2D layer in the shortcut path is used to resize the input $x$ to a different dimension, so that the dimensions match up in the final addition needed to add the shortcut value back to the main path.The CONV2D layer on the shortcut path does not use any non-linear activation function. Its main role is to just apply a (learned) linear function that reduces the dimension of the input, so that the dimensions match up for the later addition step. 

The details of Convolution Block are listed as follow:

First component of main path:
- The first CONV2D has $F_1$ filters of shape (1,1) and a stride of (s,s).
- The first BatchNorm is normalizing the channels axis.
- Then apply the ReLU activation function.

Second component of main path:
- The second CONV2D has $F_2$ filters of (f,f) and a stride of (1,1).
- The second BatchNorm is normalizing the channels axis.
- Then apply the ReLU activation function. 

Third component of main path:
- The third CONV2D has $F_3$ filters of (1,1) and a stride of (1,1).
- The third BatchNorm is normalizing the channels axis.
Shortcut path:
- The CONV2D has $F_3$ filters of shape (1,1) and a stride of (s,s).
- The BatchNorm is normalizing the channels axis.

Final step: 
- The shortcut and the main path values are added together.
- Then apply the ReLU activation function.
