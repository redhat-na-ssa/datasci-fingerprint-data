# demo-rosa-sagemaker-data
Data for ROSA / Sagemaker demo

Disclaimer: Yes, storing large data blobs is not for `git`

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

Compress (linux)

```
tar -Jc --no-xattrs --no-acls -f left.tar.xz left/
tar -Jc --no-xattrs --no-acls -f right.tar.xz right/
tar -Jc --no-xattrs --no-acls -f real.tar.xz real/
```
