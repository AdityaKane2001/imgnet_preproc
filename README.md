# imgnet_preproc

A repo to download and convert ImageNet-1k dataset to TFRecords. 

### Objective

The objective of this set of scripts is to give a set of utility scripts which can be used to create TFRecords from the ImageNet-1k dataset. Generally, people new to the dataset spend a lot of time understanding its structure and writing code for this task. So I have made this repo to make it as easy to use as possible.   

### Points to remember

1. You need to untar the tar files to a directory. Also, the scripts expect data directories to have a specific structure and names.
2. When running these scripts on ImageNet-1k dataset it is recommended to use [nohup](https://linuxize.com/post/linux-nohup-command/) or [screen](https://linuxize.com/post/how-to-use-linux-screen/) to avoid any mishap due to loss of connection. 
3. IMPORTANT: Delete n02105855/n02105855_2933.JPEG before starting, else the process will crash halfway through. 
4. This is not not intended to be used with `gs://` filepaths. I intend to add this functionality in the future.   
5. Please take a look at this [doc page](https://cloud.google.com/tpu/docs/imagenet-setup) from Google Cloud to setup a CLoud VM for this.


### Usage: 

```
python3 make_tfrecs.py \
    --odir <output_directory.> \
    --data_dir <Input data directory.> \
    --file_prefix <File prefix to add to all files.> \
    --synset_filepath <Path to JSON file containing synsets. Default file is used if unspecified.> \
    --batch_size <Batch size for the dataset. One shard contains these many examples.> \
    --log_freq <`Writing shard..` will be printed after these many shards.> \
    --shuffle <To be specified if dataset should be shuffled before making TFRecords.> \
    --validation_set <To be specified if dataset has the file structure of ImageNet validation set.>
```


### Description of scripts:

- `make_tfrecs.py` : Driver script
- `tfrecs_utils.py` : Utilities for making tfrecords.
- `image_utils.py` : Utilities for image manipulation.
- `valid_labels.txt` : Labels for validation set of ImageNet-1k.
- `synset_to_human.json` : Synset to human readable labels mapping.
