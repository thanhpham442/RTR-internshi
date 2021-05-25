<img src="./images/RtR_footage.png" width="100%">

# Setup CUDA cho Ubuntu 18.04

## Cài đặt Mini Conda để quản lý các gói thư viện

Sử dụng `miniconda` để cài đặt môi trường ảo với `python 3.6.5`. 

```
conda create -n myenv python=3.6.5
```

Sau khi cài rất nhiều gói thư viện không cần thiết bị phát sinh, ta có thể remove chúng để lấy lại dung lượng với lệnh:

```
conda clean --all
```

## Cài đặt CUDA và CuDNN

Xoá CUDA PPA và package nvidia-cuda-toolkit nếu được cài đặt từ trước:

```
sudo rm /etc/apt/sources.list.d/cuda*
sudo apt remove --autoremove nvidia-cuda-toolkit
```
Gỡ driver cũ (khuyến khích):

```
sudo apt remove --autoremove nvidia-*
```

Cập nhật hệ thống:
```
sudo apt update && sudo apt full-upgrade
```

Thêm PPA và setup key server:
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-key adv --fetch-keys  http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/7fa2af80.pub
```

Và thêm các repo chứa driver:
```
sudo bash -c 'echo "deb http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64 /" > /etc/apt/sources.list.d/cuda.list'
sudo bash -c 'echo "deb http://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1804/x86_64 /" > /etc/apt/sources.list.d/cuda_learn.list'
```

Cập nhật cơ sử dữ liệu gói:
```
sudo apt update
```

Cài CUDA 11.0. Lưu ý driver tương ứng cũng sẽ được cài đặt sau bước này:
```
sudo apt install cuda-11-0
```

Cài cudnn 8.0.5:
```
sudo apt-get install libcudnn8=8.0.5.39-1+cuda11.0

sudo apt-get install libcudnn8-dev=8.0.5.39-1+cuda11.0
```

Thêm các dòng sau vào file `~/.profile`:
```
# open file
nano ~/.profile
```
```
# set PATH for cuda 11.0 installation
if [ -d "/usr/local/cuda-11.0/bin/" ]; then
    export PATH=/usr/local/cuda-11.0/bin${PATH:+:${PATH}}
    export LD_LIBRARY_PATH=/usr/local/cuda-11.0/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
fi
```

Sau bước này bạn hãy khởi động lại và kiểm tra các cài đặt.

Kiểm tra Nvidia CUDA Compiler: 
```
nvcc --version
```

Kiểm tra Cudnn: 
```
/sbin/ldconfig -N -v $(sed 's/:/ /' <<< $LD_LIBRARY_PATH) 2>/dev/null | grep libcudnn
```

Kiểm tra Nvidia Driver:
```
nvidia-smi
```
## Sử dụng Pytorch để check CUDA

Hiện tại card RTX 3060 với kiến trúc sm_86 mới nên cần bản `pytorch 1.7.1` mới có thể sử dụng được hiệu năng của GPU. Lưu ý hiện tại pytorch này sử dụng `CUDA 11.0` nên ở trên đã cài `CUDA 11.0`.

Lệnh cài [pytorch](https://pytorch.org/):
```
pip install torch==1.7.1+cu110 torchvision==0.8.2+cu110 torchaudio==0.7.2 -f https://download.pytorch.org/whl/torch_stable.html
```

Lệnh kiểm tra cuda với pytorch:

```
torch.version.cuda
torch.cuda.is_available()
torch.cuda.current_device()
torch._C._cuda_getCompiledVersion()
```

## Cài đặt TensorRT

Tham khảo cài đặt tại [Reference 1](https://github.com/vujadeyoon/TensorRT-Torch2TRT), [Reference 2](https://docs.nvidia.com/deeplearning/tensorrt/archives/tensorrt-713/install-guide/index.html#installing-tar)

Đầu tiên truy cập vào trang chủ của TensorRT và tải file nén với gói phù hợp về máy. Sau đó giải nén với lệnh:
```
tar xzvf TensorRT-7.2.3.4.Ubuntu-18.04.x86_64-gnu.cuda-11.0.cudnn8.1.tar.gz
```
Thiết lập `PATH` cho TensorRT:

```
echo -e "\n## set PATH for TensorRT"  >> ~/.bashrc

echo 'export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/quanrtr/tensorRT/TensorRT-7.2.3.4/lib' >> ~/.bashrc

source ~/.bashrc

# conda activate rtr

nano ~/.bashrc
```

Coppy file plugin TensorRT đến thư mục của CUDA 11.0. Mục đích để tí nữa cài `torch2trt` không phát sinh lỗi do thiếu plugin.

```
sudo cp -r /home/quanrtr/tensorRT/TensorRT-7.2.3.4/include/* /usr/local/cuda-11.0/targets/x86_64-linux/include/
```

```
sudo cp -r /home/quanrtr/tensorRT/TensorRT-7.2.3.4/targets/x86_64-linux-gnu/lib/* /usr/local/cuda-11.0/targets/x86_64-linux/lib/
```

Cài đặt các gói của tensorrt tại thư mục đã giải nén `Tensorrt-7.2.3.4`:
```
cd python

sudo pip install tensorrt-7.2.3.4-cp36-none-linux_x86_64.whl
```

```
cd uff

sudo pip install uff-0.6.9-py2.py3-none-any.whl
```

```
cd graphsurgeon

sudo pip install graphsurgeon-0.4.5-py2.py3-none-any.whl
```
## Error

[train detectron2 pytorch](https://github.com/facebookresearch/detectron2/issues/2743)

[cuda support RTX 3x](https://github.com/pytorch/pytorch/issues/49161#issuecomment-742934261)