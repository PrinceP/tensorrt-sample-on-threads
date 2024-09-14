# Tensorrt sample for running engines on different threads

Here is a sample to run GPU and DLAs at the same time.

1. Prepare TensorRT engine of GPU and DLA with trtexec. For example

For GPU
```sh
trtexec --onnx=/usr/src/tensorrt/data/mnist/mnist.onnx --saveEngine=gpu.engine
```

For DLA
```sh
trtexec --onnx=/usr/src/tensorrt/data/mnist/mnist.onnx --useDLACore=0 --allowgPUFallback --saveEngine=dla.engine
```

2. Compile the repo

```sh
make
```

3. Test

Please put the gu.engine and da.engine generated in step l to the cloned repo.

The command runs like this
```sh
./test <thread0> <thread1> <thread2> ... <threadK> # -1: GPU, 0: DLAO, 1: DLA1
```

Ex: Run GPU+DLA0+DLA1
```sh
./test -1 0 1
```
