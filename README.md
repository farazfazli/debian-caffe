# debian-caffe
Run Caffe on Debian with an ARM board.

Running on modified Jessie http://forum.pine64.org/showthread.php?tid=497

1. sudo apt-get install libprotobuf-dev libleveldb-dev libsnappy-dev libhdf5-serial-dev protobuf-compiler 
2. OpenCV from source (http://www.pyimagesearch.com/2015/10/26/how-to-install-opencv-3-on-raspbian-jessie/)
3. leveldb from source 
  ```
  git clone https://github.com/google/leveldb.git && cd leveldb && make all -j8 && sudo cp -r include/* /usr/include && sudo cp -r out-shared/* /usr/lib/
  ```
4. Modify Makefile.config to be CPU only (unless your board has an embedded GPU, like the Jetson) and include hdf5.h (/usr/local/include/hdf5/serial) manually
5. (optional) create a swap file following https://digitizor.com/create-swap-file-ubuntu-linux/
5. make all -j4 && make pycaffe -j4 && make distribute
