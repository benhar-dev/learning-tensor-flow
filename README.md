# learning-tensor-flow
These notes are just my own personal notes taken while learning a subject.  You may find this of interest.  They may not be completed, they may not make sense, but they are here.

## Course
https://learning.edx.org/course/course-v1:Google+WebML102+3T2021/home

## Handy Links
* [Teachable Machine](https://teachablemachine.withgoogle.com/) - Very fast model training.
* [Glitch](https://glitch.com/) - Program HMTL/CSS/JavaScript online

## What to concider when selecting the model to use

* Does it do the job?
* Processing speed based on the target platform
* Size of the model on disk space
* Size of the model on memory

In the smart camera example it was shown that pose and object detection were a possible match, however pose was limited to 6 people, vs 20+ people could be found with object detection.  Object detection was used and processing of a crowed was possible. 

## Key Terms

### Tensor
A Tensor is the primary datastructure used in TensorFlow.  These are comparible to arrays, but are specific to holding data in a known way.  Tensors are ranked 1 - 6 which is akin to an array's dimension.  A tensor may only contain a single datatype.  Machine learning models take tensors as inputs and provide tensors as outputs. 

Tensors have the following properties.

* Data Type (DType) - Such as int, dint..
* Shape - Holds the length of each axis (dimension)
* Rank / Axis - Tensor flow supports 1 to 6 ranks
* Size - Total number of elements in a tensor

Tensors of 0 dimensions are called scalers.  These are single values.  Tensors can be reshaped.

#### Example of tensor coding
```javascript
let tensor = tf.tensor2d([[1, 2, 3], [4, 5 ,6]]);
let scalar = tf.scalar(2);
let newTensor = tensor.mul(scalar);
newTensor.print();
let reshaped = tensor.reshape([6]);
```

#### Important
Tensors are excluded from the standard JavasScript memory management and must be disposed of using the dispose() method.  You can also call tidy() on tensorflow to dispose of all tensors. 

## Working with models

###  Using Raw TFJS Pre-Trained Models
These types of models have not been wrapped in to a nice JavaScript class and as such you must take care to provide data correctly to the model and format the result after the model has completed.

### Layers & Graph Models
There are 2 types of model which can be used with TensorFlow.js.  Both can be used, but you must load them using their respective load function.  If you are unsure of what the type of model is, then open the model.json file and look for the property of "format".

##### Example of loading a layers model
```javascript

const MODEL_PATH = 'path of model.json goes here';

let model = undefined;

async function loadModel() {
   model = await tf.loadLayersModel(MODEL_PATH);
   model.summary();
}

loadModel();
```

#### Layers Model
Layers are models with their building blocks included.  These are easier to read but suffer by being non-optimized.

#### Graph Model
These are highly optimized, so are faster, but are much harder to read (if you need to look inside them)

### What is included with a model

* model.json - stores the details and specification of the model
* shard1ofN.bin - a number of bin files (maximum size of 4MB) which hold the parameters of the model.
