# FSL_Relationnet_custom_data

*File not updated yet --> 08.01*
*파일 아직 업로드 안했습니다* 


# **Index**
* Source 
* Steps to follow
* How does it work? 

_______

# Source 
Image classification with relation_net with your custom data 
 
## This code is modified from wyharveychen's CloserLookFewshot 
### https://github.com/wyharveychen/CloserLookFewShot

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


Tree structure of this repository ( img 첨부 ) 

# Steps 

* 1. git clone this repo 
* 2. prepare data set 

it should be like this 

directory 
- class 1
-- img 1
-- img 2
-- img 3 
- class 2
-- img 1
-- img 2
-- img 3 
- class 3 
-- img 1
-- img 2
-- img 3 
- write_filelist.py 

* 3. change directory to custom data folder, run write_filelist.py , then ( base, novel, val ) json files will be made. 

* 4. < train > 
change directory to upper directory, run train.py 
you should pass args this way, and make changes in your way ( sample code will be attached ) 
time will be measured using package "time" 

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

!python save_features.py --dataset "custom"\
--mtehod relationnet\
--model Conv4\
--test_n_way n\
--train_n_way n\
--n_shot n\
--save_iter n

# line 74 checkpoint directory 수정 필요 Check ipynb file!!!

* 6. < test with saved features > 
!python ./test.py \
--dataset custom \
--method relationnet \
--train_n_way 2 \
--test_n_way 2 \


* 7. results are saved in directory below
!xdg-open ./record/results.txt

# How does it work? 
설명 첨부할 것 ! 

# 
