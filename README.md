# imgnet_preproc

A repo to download and convert ImageNet-1k dataset too TFRecords. 

### Usage: 

```
python3 make_tfrecs.py \
    --odir <output_directory.> \
    --data_dir <Input data directory.> \
    --file_prefix <File prefix to add to all files.> \
    --synset_filepath <Path to JSON file containing synsets. Default file is used if unspecified.> \
    --batch_size <Batch size for the dataset. One shard contains these many examples.> \
    --log_freq <`Writing shard..` will be printed after these many shards.> \
    --shuffle <Shuffle dataset before making TFRecords.> \
    --validation_set <To be specified if dataset has the file structure of ImageNet validation set.>
```

### Description of scripts:

- `make_tfrecs.py` : Driver script
- `tfrecs_utils.py` : Utilities for making tfrecords.
- `image_utils.py` : Utilities for image manipulation.
- `valid_labels.txt` : Labels for validation set of ImageNet-1k.
- `synset_to_human.json` : Synset to human readable labels mapping.
