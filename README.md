
# TestCheckpointFromDFV

This code is almost same as [struct2depth](https://github.com/tensorflow/models/tree/master/research/struct2depth) code.

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

```shell
python inference.py \
    --logtostderr \
    --file_extension png \
    --depth \
    --egomotion true \
    --input_list_file /home/ubuntu/data/raw_data_KITTI/test_files_eigen.txt \
    --output_dir /home/ubuntu/data/dfv_KITTI_depth_result_20200414/ \
    --model_ckpt /home/ubuntu/data/cityscapes_kitti_learned_intrinsics/model-1000977
```

You can get model from [here](https://github.com/google-research/google-research/tree/master/depth_from_video_in_the_wild).

