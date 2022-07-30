# FSL_Relationnet_custom_data
*Image classification with relation_net with your custom data*
*File updated --> 07.30*

*check tutorial for feasible use*

# **Index**
* Steps to follow
* How does it work? 
* Source 
_______
Overal tree structure of this repository

<img width="250" alt="스크린샷 2022-07-30 오후 1 33 31" src="https://user-images.githubusercontent.com/102582915/181872498-74e132b0-f609-4237-b1a4-5438e3706c52.png">

# Steps ( For mor details , checkout tutorial folder and ipynb file ) 
* 1. git clone this repo 
* 2. prepare data set 
* 3. change directory to custom data folder, run write_filelist.py , then ( base, novel, val ) json files will be made. 

* 4. < train > 
change directory to upper directory, run train.py 
you should pass args this way, and make changes in your way ( sample code will be attached ) 
run time will be measured using package "time" 

!python train.py --dataset "custom"\
--method relationnet\
--test_n_way 2\
--train_n_way 2\
--n_shot 10\
--num_classes 2\
--start_epoch 0\
--stop_epoch 5\
--save_freq 2

* 5. < save train results(features) >
* 6. < test with saved features > 
* 7. results are saved in txt file 

# How does it work? 




# Performance 
for 20 images per class(2) and 3270 times of iteration , it took 98 seconds to train. And the result accuracy is appoximately 80%. 
Appliable for Real-time training and classification.

<img width="444" alt="스크린샷 2022-07-30 오후 3 41 06" src="https://user-images.githubusercontent.com/102582915/181878246-a3a881d0-6304-46dc-b939-562e18681ea9.png">

<img width="833" alt="스크린샷 2022-07-30 오후 3 45 49" src="https://user-images.githubusercontent.com/102582915/181878453-1cd774b8-21c0-47b2-930e-2016222e90a1.png">

# + adding some relish 
with images created by GAN (image augmentation - predicting future sequence ), you can get more accuracy.  

<img width="898" alt="스크린샷 2022-07-30 오후 3 38 04" src="https://user-images.githubusercontent.com/102582915/181878146-b0b80106-d4da-4e3d-938f-d465537fbe5a.png">

<img width="803" alt="스크린샷 2022-07-30 오후 3 46 13" src="https://user-images.githubusercontent.com/102582915/181878433-946b8352-0bd2-4791-a9d8-e23bd622fc3e.png">




# Source 
### This code is modified from wyharveychen's CloserLookFewshot 
### https://github.com/wyharveychen/CloserLookFewShot
### ICLR19' 

## Research paper from 
### A closer look at few shot classification 
- https://arxiv.org/pdf/1904.04232.pdf
- [ Wei-Yu Chen, Carnegie Mellon University ], [ Yu-Chiang Frank Wang, National Taiwan University ], [ Yen-Cheng Liu & Zsolt Kira, Georgia Tech ] ,
[ Jia-Bin Huang, Virginia Tech ] 
- booktitle={International Conference on Learning Representations},
- year={2019}

### Learning to Compare: Relation Network for Few-Shot Learning
- https://arxiv.org/pdf/1711.06025.pdf
- [ Flood Sung, Yongxin Yang, Li Zhang, Tao Xiang, Philip H.S. Torr, Timothy M. Hospedales, Queen Mary University of London ,University of Oxford , The University of Edinburgh ] 
