<img width="612" alt="image" src="https://user-images.githubusercontent.com/102582915/181883910-d184bb2f-c83c-4286-a5a6-4cb81f18ffbe.png">
*File updated --> 07.30*

# **Index**
* Steps to follow
* How does it work? 
* Source 
_______
# Steps ( For mor details , checkout tutorial folder and ipynb file ) 

1. git clone this repo 
2. prepare data set 
3. change directory to custom data folder, run write_filelist.py , then ( base, novel, val ) json files will be made. 

Overal tree structure of dataset you should prepare
<img width="250" alt="스크린샷 2022-07-30 오후 1 33 31" src="https://user-images.githubusercontent.com/102582915/181872498-74e132b0-f609-4237-b1a4-5438e3706c52.png">

4. < train > 
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

5. < save train results(features) >
6. < convert train result file >
7. < test with saved features > 
8. results are saved in txt file 

# How does it work? 

FSL is a type of Meta Learning ( k-way n-shot -> few shot )
Meta Learning focuses on learning the difference and similarity between data, not the features of the data.

Generally, many methods are well-known. For example, the siamese network. 

https://towardsdatascience.com/what-are-siamese-neural-networks-in-deep-learning-bb092f749dcb![image](https://user-images.githubusercontent.com/102582915/181879965-2d82434a-dc47-4dc1-99a9-2d813ea6c88f.png)
*image from "towardsdatascience.com"*

through meta-learning process, data is embedded, which is now ready to be classified in a more compact way. 

* Relation net 

Relation net is a type of MAML, which does not use (shallow) fixed distance metric. 
It uses flexible approximater, a deep non-linear embedding. 
Through network matching , the embedded result and the model learns the loss in a end-to-end point. 

As you can see in the image file the embedded data becomes linear seperable(right).
Very neat and clever way to embed, compared to the shallow distance metric embedding(left).   

<img width="404" alt="image" src="https://user-images.githubusercontent.com/102582915/181880256-c317f4e1-c636-483c-afa3-917f6dc659e5.png">

further details such as research papers are in the link below README file. 


# Performance 
for 20 images per class(2) and 3270 times of iteration , it took 98 seconds to train. And the result accuracy is appoximately 80%. 
Appliable for Real-time training and classification.

<img width="444" alt="스크린샷 2022-07-30 오후 3 41 06" src="https://user-images.githubusercontent.com/102582915/181878246-a3a881d0-6304-46dc-b939-562e18681ea9.png">

<img width="833" alt="스크린샷 2022-07-30 오후 3 45 49" src="https://user-images.githubusercontent.com/102582915/181878453-1cd774b8-21c0-47b2-930e-2016222e90a1.png">

My results scored higher accuracy compared to the results of the CUB,miniImageNet datasets.
But it is somewhat anticipated result because, my custom dataset had less class and more images. ( less k , more n ) 
The problem becomes more easy when there are less class, and more data.

<img width="869" alt="스크린샷 2022-07-30 오후 4 31 03" src="https://user-images.githubusercontent.com/102582915/181880084-548911a5-7d7a-4bf6-9b1a-c1cca078bfe3.png">


# + adding some relish 
with images created by GAN (image augmentation - predicting future sequence ), you can get more accuracy.  

<img width="898" alt="스크린샷 2022-07-30 오후 3 38 04" src="https://user-images.githubusercontent.com/102582915/181878146-b0b80106-d4da-4e3d-938f-d465537fbe5a.png">

<img width="803" alt="스크린샷 2022-07-30 오후 3 46 13" src="https://user-images.githubusercontent.com/102582915/181878433-946b8352-0bd2-4791-a9d8-e23bd622fc3e.png">


# Source and Research papers 
### This code is modified from wyharveychen's CloserLookFewshot 
- https://github.com/wyharveychen/CloserLookFewShot
- ICLR19' 

### A closer look at few shot classification 
- https://arxiv.org/pdf/1904.04232.pdf
- [ Wei-Yu Chen, Carnegie Mellon University ], [ Yu-Chiang Frank Wang, National Taiwan University ], [ Yen-Cheng Liu & Zsolt Kira, Georgia Tech ] ,
[ Jia-Bin Huang, Virginia Tech ] 
- booktitle={International Conference on Learning Representations},
- year={2019}

### Learning to Compare: Relation Network for Few-Shot Learning
- https://arxiv.org/pdf/1711.06025.pdf
- [ Flood Sung, Yongxin Yang, Li Zhang, Tao Xiang, Philip H.S. Torr, Timothy M. Hospedales, Queen Mary University of London ,University of Oxford , The University of Edinburgh ] 
