
# struct2depth_eval

This code is modified from [struct2depth](https://github.com/tensorflow/models/tree/master/research/struct2depth) code to use [depth_from_video_in_the_wild](https://github.com/google-research/google-research/tree/master/depth_from_video_in_the_wild).

After use this code, you can calculate Abs Rel Error using [this code](https://github.com/go125/SfmLearner_eval).


# Example input

## Train example

- [Data Preparation](https://github.com/go125/PrepareDataForDFV)
- [ImageNet Checkpoint Preparation](https://github.com/dalgu90/resnet-18-tensorflow)

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

### kitti_learned_intrinsics (gray,Trained on sekilab AWS)

```shell
python inference_dfv.py \
    --logtostderr \
    --file_extension png \
    --depth \
    --egomotion false \
    --input_list_file /home/ubuntu/data/raw_data_KITTI/test_files_eigen_gray.txt \
    --output_dir /home/ubuntu/data/result_20200717_14394/ \
    --model_ckpt /home/ubuntu/data/kitti_experiment_checkpoint_20200716/model-14394
```

### kitti_learned_intrinsics (gray,Trained on sekilab AWS, Stereo Camera in Saitama)

#### Before fine tuning

```shell
python inference_dfv.py \
    --logtostderr \
    --file_extension png \
    --depth \
    --egomotion false \
    --input_dir /home/ubuntu/Sayama/tmpdir/2020_08_04/video1top_png/image_02/data/ \
    --output_dir /home/ubuntu/Sayama/result_video1top_273486/ \
    --model_ckpt /home/ubuntu/data/kitti_experiment_checkpoint_20200716/model-273486
```

#### After fine tuning

```shell
python inference_dfv.py \
    --logtostderr \
    --file_extension png \
    --depth \
    --egomotion false \
    --input_dir /home/ubuntu/Sayama/tmpdir/2020_08_04/video1top_png/image_02/data/ \
    --output_dir /home/ubuntu/Sayama/result_video1top_279296/ \
    --model_ckpt /home/ubuntu/data/kitti_experiment_checkpoint_20200716/model-279296
```


### cityscapes_kitti_learned_intrinsics (Local)

```shell
python inference_dfv.py \
    --logtostderr \
    --file_extension jpg \
    --depth \
    --egomotion false \
    --input_dir ../result_img/ \
    --output_dir ../depth/ \
    --model_ckpt ../cityscapes_kitti_learned_intrinsics/model-1000977
```

You can get model from [here](https://github.com/google-research/google-research/tree/master/depth_from_video_in_the_wild).

### cityscapes_kitti_learned_intrinsics (Local, YouTube_trained)

```shell
python inference_dfv.py \
    --logtostderr \
    --file_extension jpg \
    --depth \
    --egomotion false \
    --input_dir ../result_img/ \
    --output_dir ../depth/ \
    --model_ckpt ../cityscapes_kitti_learned_intrinsics_AWS/model-1003806
```
