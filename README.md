# TrashClassificationModel by Pytorch

쓰레기 이미지 분류 Pytorch 모델

## Datasets
* total **25 classes, 13000 images**
* collect data via AutoCrawler (https://github.com/YoongiKim/AutoCrawler)

## Train
* Backbone : resnext50_32x4d
* num of epochs = 8
* optimization function = Adam
* learning rate = 5.5e-5
* you can change the backbone model in 'TrashNet' class
```
    class TrashNet(nn.Module):
        def __init__(self)
        ...
        self.backbone = models.resnext50_32x4d(pretrained=True)
        ...
```

## Validation
* k-fold cross validation (k = 8)
* using KFold module from sklearn


## Evaluation

|        Model         | Accuracy@1 | Parameters(M) | G-FLOPs |
|----------------------|------------|---------------|---------|
|       ResNet18       |   93.98    |      11.69    |  1.82   |
|       ResNet34       |   93.47    |      21.8     |  3.68   |
|       ResNet50       |   96.26    |      25.56    |  4.12   |
|    resnext50_32x4d   | **96.80**  |      25.0     |  4.2    |
|    wide_resnet50_2   |   96.80    |      68.9     |   *     |

## Convert pytorch model to CoreML model
* Install coremltools module
```
!pip install -U coremltools
```
* We use Apple's coremltools & PyTorch's JIT tracer
* ref : https://developer.apple.com/videos/play/tech-talks/10154/
