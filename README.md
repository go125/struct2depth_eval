
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
--checkpoint_dir=/home/ubuntu/data/kitti_experiment_checkpoint_20201026 \
--imagenet_ckpt=/home/ubuntu/data/ResNet18/model.ckpt \
--train_steps=1000000 &

```

## Finetuning with the video taken in Saitama

```script
nohup python -m depth_from_video_in_the_wild.train \
--data_dir /home/ubuntu/Sayama/out \
--checkpoint_dir=/home/ubuntu/data/kitti_experiment_checkpoint_20201026 \
--imagenet_ckpt=/home/ubuntu/data/ResNet18/model.ckpt \
--train_steps=1000000 &

```

## Evaluation

### Before fine tuning


### KITTI

```shell
python inference_dfv.py \
    --logtostderr \
    --file_extension png \
    --depth \
    --egomotion false \
    --input_list_file /home/ubuntu/data/raw_data_KITTI/test_files_eigen_gray.txt \
    --output_dir /home/ubuntu/data/result_20201026_14394/ \
    --model_ckpt /home/ubuntu/data/kitti_experiment_checkpoint_20201026/model-14394
```

```shell
python kitti_eval/eval_depth.py --kitti_dir=/home/ubuntu/data/raw_data_KITTI/ --pred_file=/home/ubuntu/data/result_20201026_14394/result.npy
```

abs_rel,     sq_rel,        rms,    log_rms,     d1_all,         a1,         a2,         a3,     scalor 

0.1829,     1.3158,     6.3322,     0.2586,     0.0000,     0.7241,     0.9077,     0.9670 ,   10.7764 

```shell
python inference_dfv.py \
    --logtostderr \
    --file_extension png \
    --depth \
    --egomotion false \
    --input_list_file /home/ubuntu/data/raw_data_KITTI/test_files_eigen_gray.txt \
    --output_dir /home/ubuntu/data/result_20201026_71970/ \
    --model_ckpt /home/ubuntu/data/kitti_experiment_checkpoint_20201026/model-71970
```

```shell
python kitti_eval/eval_depth.py --kitti_dir=/home/ubuntu/data/raw_data_KITTI/ --pred_file=/home/ubuntu/data/result_20201026_71970/result.npy
```

abs_rel,     sq_rel,        rms,    log_rms,     d1_all,         a1,         a2,         a3,     scalor 

0.1409,     1.0408,     5.5013,     0.2189,     0.0000,     0.8137,     0.9391,     0.9767 ,   11.1339 

### Sayama

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

### After fine tuning

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
