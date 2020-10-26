# Depth from Video in the Wild: Unsupervised Monocular Depth Learning from Unknown Cameras

[Original](https://github.com/google-research/google-research/tree/master/depth_from_video_in_the_wild)

This code is modified to apply for my own video.

## Train example

[Data Preparation](https://github.com/go125/PrepareDataForDFV)
[Checkpoint Preparation](https://github.com/dalgu90/resnet-18-tensorflow)

```script
nohup python -m depth_from_video_in_the_wild.train \
--data_dir /home/ubuntu/data/kitti_result_all_20200715 \
--checkpoint_dir=/home/ubuntu/data/kitti_experiment_checkpoint_20200716 \
--imagenet_ckpt=/home/ubuntu/data/ResNet18/model.ckpt \
--train_steps=1000000 &

```

## Finetuning with the video taken in Saitama

```script
nohup python -m depth_from_video_in_the_wild.train \
--data_dir /home/ubuntu/Sayama/out \
--checkpoint_dir=/home/ubuntu/data/kitti_experiment_checkpoint_20200716 \
--imagenet_ckpt=/home/ubuntu/data/ResNet18/model.ckpt \
--train_steps=1000000 &

```

## Evaluation


Please use [this code](https://github.com/go125/struct2depth_eval).

