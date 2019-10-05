[[Paper]](https://bmvc2019.org/wp-content/uploads/papers/0403-paper.pdf)
[[Video]](https://github.com/kniinuma/UnmaskingTheDevil/blob/master/BMVC2019_spotlight_small.mp4?raw=true)

# Unmasking the Devil in the Details: What Works for Deep Facial Action Coding?

## Abstract

The performance of automated facial expression coding has improving steadily as evidenced
by results of the latest Facial Expression Recognition and Analysis (FERA 2017)
Challenge. Advances in deep learning techniques have been key to this success. Yet the
contribution of critical design choices remains largely unknown. Using the FERA 2017
database, we systematically evaluated design choices in pre-training, feature alignment,
model size selection, and optimizer details. Our findings vary from the counter-intuitive
(e.g., generic pre-training outperformed face-specific models) to best practices in tuning
optimizers. Informed by what we found, we developed an architecture that exceeded
state-of-the-art on FERA 2017. We achieved a 3.5% increase in F1 score for occurrence
detection and a 5.8% increase in ICC for intensity estimation.
<br>

## Systematical evaluation

<img align="center" width="640" src="https://user-images.githubusercontent.com/25273927/66246568-0a858d00-e6e3-11e9-8190-3aabadec37ea.png">
<img align="center" width="560" src="https://user-images.githubusercontent.com/25273927/66247210-3f481300-e6e8-11e9-8272-0594b9fd4cdc.png">
<br><br>

### Normalization

The performance with Procrustes analysis is slightly better than the one with Resizing, but the difference is small, only 1%.

<img align="center" width="480" src="https://user-images.githubusercontent.com/25273927/66246613-4fa9bf00-e6e3-11e9-8e03-c59de00243a1.png">
<br><br>

### Pre-trained architecture

Generic pre-trained models (VGG-ImageNet) show better performance than face-specific ones (VGG-Face).

<img align="center" width="480" src="https://user-images.githubusercontent.com/25273927/66246616-52a4af80-e6e3-11e9-800e-6149e226a7a8.png">
<br><br>

### Training set size

The training set size have minor influence on the performance. We down-sampled the majority class and up-sampled the minority class to build a stratified training set. We used this procedure for each pose and each AU. For example, in the case of AU occurrence detection, a 5,000 training set size indicate that 5,000 frames with AU present and 5,000 frames where the AU is not present were randomly selected for each pose and for each AU, resulting in 90,000 images in total (=5,000 images x 2 classes x 9 poses). 

<img align="center" width="480" src="https://user-images.githubusercontent.com/25273927/66246617-53d5dc80-e6e3-11e9-8d0d-dd7f5d5d3461.png">
<br><br>

### Optimizer and learning rate

Optimal learning rate is largely different between Adam and SGD optimizers. However, the performance differences between Adam and SGD are negligible if one uses the optimal learning rates for each optimizer, respectively.

<img align="center" width="480" src="https://user-images.githubusercontent.com/25273927/66246611-4fa9bf00-e6e3-11e9-951c-d56783113971.png">
<br><br>

## Comparision with existing methods

<img align="center" width="640" src="https://user-images.githubusercontent.com/25273927/66247149-e7111100-e6e7-11e9-9981-06d1b5e67bed.png">


## Citation

```markdown
@inproceedings{unmaskingthedevil2019,
  title={Unmasking the Devil in the Details: What Works for Deep Facial Action Coding?},
  author={Niinuma, Koichiro and Onal Ertugrul, Itir and Jeni, L{\'a}szl{\'o} A and Cohn, Jeffrey F},
  booktitle={British Machine Vision Conference},
  year={2019}
}
```

