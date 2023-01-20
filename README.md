# demo-rosa-sagemaker-data
Data for ROSA / Sagemaker demo

Disclaimer: Yes, storing large data blobs is not for `git`

Intended Usage:

For model training. A model or series of models should be trained to predict below classes when an unseen or real fingerprint image is submitted.

The data should be extracted and grouped into class name subfolders to infer labels with [tf.keras.utils.image_dataset_from_directory](https://www.tensorflow.org/api_docs/python/tf/keras/utils/image_dataset_from_directoryhttps://www.tensorflow.org/api_docs/python/tf/keras/utils/image_dataset_from_directory).
Three use cases for grouping this data come from the filenames `1__M_Left_little_finger_Obl.png`:
1. Gender: Male (M), Female (F)
2. Hand: Left, Right
3. Finger: index, middle, ring, little, thumb

The directory structure(s) should result similar to the examples below:

```commandline
gender/
...male/
......a_image_1.png
......a_image_2.png
...female/
......b_image_1.png
......b_image_2.png
```

```commandline
hand/
...left/
......a_image_1.png
......a_image_2.png
...right/
......b_image_1.png
......b_image_2.png
```

```commandline
finger/
...index/
......a_image_1.png
......a_image_2.png
...middle/
......b_image_1.png
......b_image_2.png
...(etc.)/
```

Extract

```
SCRATCH=scratch

mkdir ${SCRATCH}/train
tar -Jxf left.tar.xz -C "${SCRATCH}"/train/
tar -Jxf right.tar.xz -C "${SCRATCH}"/train/
tar -Jxf real.tar.xz -C "${SCRATCH}"
```


Compress (mac)

```
tar -Jc --uname default --gname root --no-xattrs --no-acls -f left.tar.xz left/
tar -Jc --uname default --gname root --no-xattrs --no-acls -f right.tar.xz right/
tar -Jc --uname default --gname root --no-xattrs --no-acls -f real.tar.xz real/
```
