## Performance 

| [**YOLOv7**](https://github.com/WongKinYiu/yolov7/releases/download/v0.1/yolov7.pt)
| [**YOLOv7-x**](https://github.com/WongKinYiu/yolov7/releases/download/v0.1/yolov7x.pt)
| [**YOLOv7-tiny**](https://github.com/WongKinYiu/yolov7/releases/download/v0.1/yolov7-tiny.pt)
=======
| **Model** | **Image Size** | **Epoch** | **Batch Size** | **Optimizer** |
| :-- | :-: | :-: | :-: | :-: |
| [**YOLOv7**](https://github.com/WongKinYiu/yolov7/releases/download/v0.1/yolov7.pt) | 640 | 100 <br>150 <br>200 | 16 | Adam |
| [**YOLOv7-X**](https://github.com/WongKinYiu/yolov7/releases/download/v0.1/yolov7x.pt) | 640 | 100 <br>150 <br>200 | 8 | Adam |
| [**YOLOv7-tiny**](https://github.com/WongKinYiu/yolov7/releases/download/v0.1/yolov7-tiny.pt) | 640 | 100 <br>150 <br>200 | 32 | Adam |


## Training

**YOLOv7 epoch (100, 150 200)** 

<p>nama foler ('v100', 'v150', 'v200')</p>
<p>nama folder ('v100', 'v150', 'v200')</p>

```shell
python train.py --cfg /cfg/training/yolov7.yaml --weights /weights/yolov7.pt --data /datasets/data.yaml --batch-size 8 --epochs [nilai epoch] --adam --name '[nama folder]'
```

**YOLOv7x epoch (100, 150 200)** 

<<<<<<< HEAD
<p>nama foler ('x100', 'x150', 'x200')</p>
=======
<p>nama folder ('x100', 'x150', 'x200')</p>
>>>>>>> 19733c16f7f18f8474774d044165d68e7d87f726

```shell
python train.py --cfg /cfg/training/yolov7x.yaml --weights /weights/yolov7x.pt --data /datasets/data.yaml --batch-size 16 --epochs [nilai epoch] --adam --name '[nama folder]'
```

**YOLOv7-tiny epoch (100, 150 200)** 

<<<<<<< HEAD
<p>nama foler ('x100', 'x150', 'x200')</p>
=======
<p>nama folder ('t100', 't150', 't200')</p>
>>>>>>> 19733c16f7f18f8474774d044165d68e7d87f726

```shell
python train.py --cfg /cfg/training/yolov7-tiny.yaml --weights /weights/yolov7-tiny.pt --data /datasets/data.yaml --batch-size 32 --epochs [nilai epoch] --adam --name '[nama folder]'
```

<<<<<<< HEAD
=======
## Deteksi
**Camera Laptop**
```shell
python detect.py --weights '[lokasi weights]' --source 0 --img 640
```

**File gambar**
```shell
python detect.py --source '[lokasi file]' --weights '[lokasi weights]' --img 640
```

>>>>>>> 19733c16f7f18f8474774d044165d68e7d87f726
## Export
**Pytorch to ONNX with NMS (and inference)** 
```shell
python export.py --weights yolov7-tiny.pt --grid --end2end --simplify \
        --topk-all 100 --iou-thres 0.65 --conf-thres 0.35 --img-size 640 640 --max-wh 640
```

**Pytorch to TensorRT with NMS (and inference)** 
```shell
wget https://github.com/WongKinYiu/yolov7/releases/download/v0.1/yolov7-tiny.pt
python export.py --weights ./yolov7-tiny.pt --grid --end2end --simplify --topk-all 100 --iou-thres 0.65 --conf-thres 0.35 --img-size 640 640
git clone https://github.com/Linaom1214/tensorrt-python.git
python ./tensorrt-python/export.py -o yolov7-tiny.onnx -e yolov7-tiny-nms.trt -p fp16
```

**Pytorch to TensorRT another way**
```shell
wget https://github.com/WongKinYiu/yolov7/releases/download/v0.1/yolov7-tiny.pt
python export.py --weights yolov7-tiny.pt --grid --include-nms
git clone https://github.com/Linaom1214/tensorrt-python.git
python ./tensorrt-python/export.py -o yolov7-tiny.onnx -e yolov7-tiny-nms.trt -p fp16

# Or use trtexec to convert ONNX to TensorRT engine
/usr/src/tensorrt/bin/trtexec --onnx=yolov7-tiny.onnx --saveEngine=yolov7-tiny-nms.trt --fp16
```

Tested with: Python 3.7.13, Pytorch 1.12.0+cu113
