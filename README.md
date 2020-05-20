
# struct2depth_eval

This code is modified from [struct2depth](https://github.com/tensorflow/models/tree/master/research/struct2depth) code for model evaluation.

After use this code, you can calculate Abs Rel Error using [this code](https://github.com/go125/SfmLearner_eval).

# How to run evalutation

```shell
python inference.py \
    --logtostderr \
    --file_extension png \
    --depth \
    --egomotion true \
    --input_list_file $RAW_DATA_KITTI/test_files_eigen.txt \
    --output_dir $OUTPUT_DIR \
    --model_ckpt $MODEL_NAME
```

## Example input

### For struct2depth

```shell
python inference.py \
    --logtostderr \
    --file_extension png \
    --depth \
    --egomotion true \
    --input_list_file /home/ubuntu/data/raw_data_KITTI/test_files_eigen.txt \
    --output_dir /home/ubuntu/data/dfv_KITTI_depth_result_20200430/ \
    --model_ckpt /home/ubuntu/data/struct2depth_model_kitti/model-199160
```

You can get model from [here](https://drive.google.com/file/d/1mjb4ioDRH8ViGbui52stSUDwhkGrDXy8/view).

### For Depth from Videos in the wild

#### kitti_learned_intrinsics (Trained on sekilab AWS)

```shell
python inference_dfv.py \
    --logtostderr \
    --file_extension png \
    --depth \
    --egomotion false \
    --input_list_file /home/ubuntu/data/raw_data_KITTI/test_files_eigen.txt \
    --output_dir /home/ubuntu/data/result_20200518_16764/ \
    --model_ckpt /home/ubuntu/data/result20200518/model-16764
```

#### kitti_learned_intrinsics

```shell
python inference_dfv.py \
    --logtostderr \
    --file_extension png \
    --depth \
    --egomotion false \
    --input_list_file /home/ubuntu/data/raw_data_KITTI/test_files_eigen.txt \
    --output_dir /home/ubuntu/data/dfv_KITTI_depth_result_20200501/ \
    --model_ckpt /home/ubuntu/data/kitti_learned_intrinsics/model-248900
```

#### cityscapes_kitti_learned_intrinsics

```shell
python inference_dfv.py \
    --logtostderr \
    --file_extension png \
    --depth \
    --egomotion false \
    --input_list_file /home/ubuntu/data/raw_data_KITTI/test_files_eigen.txt \
    --output_dir /home/ubuntu/data/dfv_KITTI_depth_result_20200501_2/ \
    --model_ckpt /home/ubuntu/data/cityscapes_kitti_learned_intrinsics/model-1000977
```

You can get model from [here](https://github.com/google-research/google-research/tree/master/depth_from_video_in_the_wild).


## DataGen test (20200508)

Under Construction

### Prepare data

```
python gen_data_kitti.py
```

### Training

```
python train.py \
  --logtostderr \
  --checkpoint_dir /home/ubuntu/data/struct2depth_checkpoint \
  --data_dir  /home/ubuntu/data/struct2depth/KITTI_processed \
  --architecture resnet \
  
```
