
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

### For Depth from Videos in the wild

#### kitti_learned_intrinsics (gray,Trained on sekilab AWS)

```shell
python inference_dfv.py \
    --logtostderr \
    --file_extension png \
    --depth \
    --egomotion false \
    --input_list_file /home/ubuntu/data/raw_data_KITTI/test_files_eigen_gray.txt \
    --output_dir /home/ubuntu/data/result_20200717_259092/ \
    --model_ckpt /home/ubuntu/data/kitti_experiment_checkpoint_20200716/model-259092
```


#### cityscapes_kitti_learned_intrinsics (Local)

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

#### cityscapes_kitti_learned_intrinsics (Local, YouTube_trained)

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
