# Learning Transformation Synchronization
Implementation of our approach on Learning Transformation Synchronization.


## DATA FORMAT:
For space and legacy issues, this folder do not contain any data from any dataset.

Here we demonstrate the data format after our data processing procedure:

An example file hierarchy we use to store processed depth images of each dataset looks like
  > "processed_dataset/scannet/scene0000_01/0.mat", which corresponds to 
    the 1st scan for scene id "scene0000_01" of "scannet" dataset.
  each mat file contains three attributes ['vertex', 'validIdx_rowmajor', 'pose']. 
  `vertex`: np.ndarray of shape (n, 3)
  `validIdx_rowmajor`: np.ndarray of shape (n, 1)
  `pose`: np.ndarray of shape (4, 4) representing the ground truth absolute pose of this scan.

## RELATIVE POSE ESTIMATION:
1. The source code of relative pose estimation is stored in "src/relative_pose_estimation"
 We use Fast Global Registration and Super4PCS to
    obtain pairwise relative pose estimation.

2. By default, results will be stored in "relative_pose".


## CLASSIFICATION:
1. We first generate images for each estimated pairwise relative pose, the code is stored in "src/generate_images"
2. We then train our classifiers using the generated images, the code is stored in "src/training_classifiers"
3. The results will be stored in "classification/".


## Optimizing Parameters of Weighting Module:
1. Given a trained classifier, we collect features for each estimated pairwise relative pose, 
  please refer to "src/training_classifier/main.py".
2. To further optimize parameters of the weighting module, please refer to src/differentiable_sync/train.py.
  (Use python train.py -h to see the instructions of how to run this code).


