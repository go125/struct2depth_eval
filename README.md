
# TestCheckpointFromDFV

This github is from "struct2depth" code.

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
