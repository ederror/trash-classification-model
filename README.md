# TrashClassificationModel by Pytorch
**CSE4186 - Sogang Univ.**

As interest in the ever-growing waste problem has increased, people's interest in proper separation of waste has also increased.
The goal of this project is to create an iOS application that can be used when people do not know how to separate and dispose of certain garbage.
This model is an image classification model that has been trained on a few objects that people are trying to figure out how to sort.
Through transfer learning based on a model such as resnet, it was effectively trained with a small amount of data.

## Datasets
* total **25 classes, 13000 images**
* collect data via AutoCrawler (https://github.com/YoongiKim/AutoCrawler)
* Train/Val/Test set ratio: 80/10/10

## Train
* Backbone : resnext50_32x4d
* you can change the backbone model in 'OurModel' class definition.
```
    class OurModel(nn.Module):
        def __init__(self)
        ...
        self.backbone = models.resnext50_32x4d(pretrained=True)
        ...
```

## Evaluation

|        Model         | Accuracy@1 | Parameters(M) | G-FLOPs |
|----------------------|------------|---------------|---------|
|       ResNet18       |   96.26    |      11.69    |  1.82   |
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

## For more information
http://cscp2.sogang.ac.kr/CSE4186/index.php/%EC%9E%AC%ED%99%9C%EC%9A%A9_%EB%8F%95%EB%8A%94_%EC%82%AC%EB%AC%BC%EC%9D%B8%EC%A7%80_iOS_%EC%95%B1
