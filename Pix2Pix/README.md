# Pix2Pix

Code for paper: [Conditional Image Synthesis With Auxiliary Classifier GANs](https://openreview.net/forum?id=BkDDM04Ke)

Heavily based on code (affinelayer/pix2pix-tensorflow)[https://github.com/affinelayer/pix2pix-tensorflow]


## Results

![sample](https://github.com/watsonyanghx/GAN_Lib_Tensorflow/blob/master/ACGAN/img/samples_98999.png)


## How to run:

``` python
# train
# cd to `Pix2Pix` folder and run command bellow
---- webpage, 2A ----
CUDA_VISIBLE_DEVICES=1 python Pix2Pix/train.py \
  --batch_size=1 \
  --mode='train' \
  --conv_type='conv2d' \
  --channel_multiplier=0 \
  --initial_lr=0.0002 \
  --end_lr=0.0001 \
  --beta1=0. \
  --beta2=0.9 \
  --loss_type='HINGE' \
  --n_dis=5 \
  --input_dir=/home/yhx/webpageSaliency/train_data/pix2pix_data_2A/train \
  --output_dir=../output_train \
  --max_epochs=300 \
  --which_direction=AtoB \
  --save_freq=2360 \
  --ngf=128 \
  --ndf=128 \
  --scale_size=572 \
  --l1_weight=20.0 \
  --gan_weight=1.0 \
  --multiple_A

# infer
CUDA_VISIBLE_DEVICES=1 python Pix2Pix/train.py \
  --batch_size=1 \
  --mode='test' \
  --conv_type='conv2d' \
  --input_dir=/home/yhx/webpageSaliency/train_data/pix2pix_data_2A/val \
  --output_dir=/home/yhx/webpageSaliency/train_data/pix2pix_data_2A/output_test_512 \
  --which_direction=AtoB \
  --ngf=128 \
  --ndf=128 \
  --scale_size=572 \
  --checkpoint_dir=../output_train \
  --multiple_A


---- VGG ----
CUDA_VISIBLE_DEVICES=0 python Pix2Pix/train.py \
  --batch_size=1 \
  --mode='train' \
  --conv_type='conv2d' \
  --channel_multiplier=0 \
  --initial_lr=0.0002 \
  --end_lr=0.0001 \
  --beta1=0. \
  --beta2=0.9 \
  --loss_type='HINGE' \
  --n_dis=5 \
  --input_dir=/home/yhx/webpageSaliency/train_data/pix2pix_data/train \
  --output_dir=../output_train_vgg \
  --max_epochs=200 \
  --which_direction=AtoB \
  --save_freq=2360 \
  --ngf=64 \
  --ndf=64 \
  --scale_size=572 \
  --l1_weight=20.0 \
  --gan_weight=1.0 \
  --net_type='VGG'

# infer
CUDA_VISIBLE_DEVICES=1 python Pix2Pix/train.py \
  --batch_size=1 \
  --mode='test' \
  --conv_type='conv2d' \
  --input_dir=/home/yhx/webpageSaliency/train_data/pix2pix_data/test \
  --output_dir=../output_test_512 \
  --which_direction=AtoB \
  --ngf=128 \
  --ndf=128 \
  --scale_size=572 \
  --checkpoint_dir=../output_train_vgg \
  --net_type='VGG'


----- depth_to_space -----
CUDA_VISIBLE_DEVICES=0 python Pix2Pix/train.py \
  --batch_size=1 \
  --mode='train' \
  --conv_type='conv2d' \
  --channel_multiplier=0 \
  --initial_lr=0.0002 \
  --end_lr=0.0001 \
  --beta1=0. \
  --beta2=0.9 \
  --loss_type='HINGE' \
  --n_dis=5 \
  --input_dir=/home/yhx/webpageSaliency/train_data/pix2pix_data/train \
  --output_dir=../output_train \
  --max_epochs=200 \
  --which_direction=AtoB \
  --save_freq=2360 \
  --ngf=64 \
  --ndf=64 \
  --scale_size=572 \
  --l1_weight=20.0 \
  --gan_weight=1.0

# infer
CUDA_VISIBLE_DEVICES=0 python Pix2Pix/train.py \
  --batch_size=1 \
  --mode='test' \
  --conv_type='conv2d' \
  --input_dir=/home/yhx/webpageSaliency/train_data/pix2pix_data/test \
  --output_dir=../output_test_512 \
  --which_direction=AtoB \
  --scale_size=572 \
  --checkpoint_dir=/home/yhx/webpageSaliency/code/depth_to_space




---- facades 400, cityscapes 2795 ----
CUDA_VISIBLE_DEVICES=0 python Pix2Pix/train.py \
  --batch_size=1 \
  --mode='train' \
  --conv_type='conv2d' \
  --channel_multiplier=0 \
  --initial_lr=0.0002 \
  --end_lr=0.0001 \
  --beta1=0. \
  --beta2=0.9 \
  --loss_type='HINGE' \
  --n_dis=5 \
  --input_dir=/home/yhx/webpageSaliency/tmp/facades/train \
  --output_dir=/home/yhx/webpageSaliency/tmp/facades/output_train_256 \
  --max_epochs=200 \
  --which_direction=BtoA \
  --save_freq=8000 \
  --ngf=128 \
  --ndf=128 \
  --scale_size=286 \
  --l1_weight=10.0 \
  --gan_weight=1.0


CUDA_VISIBLE_DEVICES=1 python Pix2Pix/train.py \
  --batch_size=1 \
  --mode='test' \
  --conv_type='conv2d' \
  --input_dir=/home/yhx/webpageSaliency/tmp/facades/val \
  --output_dir=/home/yhx/webpageSaliency/tmp/facades/output_val_256 \
  --which_direction=BtoA \
  --scale_size=286 \
  --checkpoint_dir=/home/yhx/webpageSaliency/tmp/facades/output_train_256


```

