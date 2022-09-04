# learning-tensor-flow
These notes are just my own personal notes taken while learning a subject.  You may find this of interest.  They may not be completed, they may not make sense, but they are here.

## Course
https://learning.edx.org/course/course-v1:Google+WebML102+3T2021/home

## Handy Links
* [Teachable Machine](https://teachablemachine.withgoogle.com/) - Very fast model training.
* [Glitch](https://glitch.com/) - Program HMTL/CSS/JavaScript online

## Key Terms

### Tensor
A Tensor is the primary datastructure used in TensorFlow.  These are comparible to arrays, but are specific to holding data in a known way.  Tensors are ranked 1 - 6 which is akin to an array's dimension.  A tensor may only contain a single datatype.  Machine learning models take tensors as inputs and provide tensors as outputs. 

Tensors have the following properties.

* Data Type (DType) - Such as int, dint..
* Shape - Holds the length of each axis (dimension)
* Rank / Axis - Tensor flow supports 1 to 6 ranks
* Size - Total number of elements in a tensor

Tensors of 0 dimensions are called scalers.  These are single values.  Tensors can be reshaped.

Example of tensor coding
```javascript
let tensor = tf.tensor2d([[1, 2, 3], [4, 5 ,6]]);
let scalar = tf.scalar(2);
let newTensor = tensor.mul(scalar);
newTensor.print();
let reshaped = tensor.reshape([6]);
```
