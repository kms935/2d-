# Color Space

색의 3속성인 색상(hue), 명도(lightness), 채도(chroma)를 3차원 공간의 각각의 축으로 형성된 색 공간

Under standing color space

https://youtu.be/KKX08oOTMkk

## 색 공간의 종류

![rgb](https://upload.wikimedia.org/wikipedia/commons/thumb/1/11/RGBCube_b.svg/200px-RGBCube_b.svg.png)  RGB 색 공간 모형

RGB 색 공간은 색을 혼합하면 명도가 올라가는 가산 혼합 방식으로 색을 표현한다. RGB 색 공간은 삼원색에 해당하는 세 가지 채널의 밝기를 기준으로 색을 지정한다. RGB 색 공간은 웹 색상 표현의 기본 원리이다.

![hsv](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f1/HSV_cone.jpg/200px-HSV_cone.jpg)  HSV 색 공간 모형

HSV 색 공간은 색상(Hue), 채도(Saturation), 명도(value)를 기준으로 색을 구성하는 방식이다. 감산 혼합이나 가산 혼합보다 색상의 지정이 직관적이기 때문에 시각 예술에서 자주 쓰인다.

![cie](https://i.stack.imgur.com/laTZU.jpg) 

CIE는 국제 조명 위원회이며, CIE 색 공간이란 컬러 매칭 실험을 통하여 생성된 R, G, B 데이터를 바탕으로 만들어진 CIEXYZ 색 공간과 CIELAB 색 공간, 그리고 CIELUV 색 공간이 대표적인 색 공간이다.

color gamut를 비교할 수 있다.


# What is Gamma/Linear workflow?

**Linear Workflow**의 목표는 Character Creator가 적절한 정보로 광원을 계산할 수 있도록 텍스처에 선형 색상 공간을 사용하는 것입니다.

현실 세계에서 우리가 인식하는 색상은 모두 선형 색상 공간에 있다고 가정 해 보겠습니다. 모니터가 현실 세계를 모방하려면 선형 방식으로 표시해야합니다.
모니터 하드웨어 및 이미지 최적화 요구 사항의 제한으로 인해 이미지는 감마 보정으로 처리되고 저장됩니다.

### 감마

오래된 CRT 모니터 기술의 한계로 인해 이미지는 감마 2.2 색상 보정을 통해서만 표시 할 수 있습니다.
현대 모니터는 선형 이미지를 직접 표시 할 수 있지만 감마 2.2는 표준 관습이되었습니다.

카메라가 이미지를 찍으면 sRGB Gamma 0.45 처리를 통해 모니터 호환성 및 파일 최적화를 위해 8 비트 이미지가 저장됩니다.
32 비트 이미지는 Gamma 1.0 처리를 통해 선형 공간 데이터를 저장하는 데 사용할 수 있습니다.

* 실제 세계 → 감마 1
* sRGB 이미지 (8 비트) → 감마 0.45
* 플로트 이미지 (32 비트) → 감마 1
* 모니터 → 감마 2.2

![gamma](http://i.imgur.com/yest359.png)

### 시스템 감마

시스템 감마는 선형 이미지를 가져와 0.45의 감마 보정으로 저장 한 다음 감마 보정 2.2로 모니터를 통해 표시되어 감마 1.0의 출력이됩니다.
감마 보정 0.45로 이미지를 처리하면 밝아집니다. 모니터의 감마 2.2를 통과하면 어두워 지지만 결과는 올바른 밝기 수준의 감마 1.0으로 균형을 이룹니다.

* sRGB 이미지 감마 0.45 + 모니터 감마 2.2 = 최종 디스플레이 감마 1  

![ㅎ므ㅡㅁ](http://i.imgur.com/i2eZj9U.png)

* 왼쪽 : 선형 이미지 (sRGB 사용 꺼짐)
* 오른쪽 : sRGB 이미지 (sRGB 사용 켜짐)

![ㅇㄹ](http://i.imgur.com/04K1eYz.png)

https://forum.reallusion.com/308094/1-PBR-Linear-Workflow


# What is LUT?(look-up table)

![lut](https://i.stack.imgur.com/o2d3y.png)
![lut2](https://media.macphun.com/img/uploads/macphun/blog/1419/LUT_Header_Blog.jpg?q=75&w=1710&h=906&resize=cover)

Look-Up Table(LUT)는 색상, 채도, 명도를 수학적으로 정확하게 조정하여 촬영된 원본 이미지의 RGB값을 새로운 RGB값으로 만들어주는 방법이다.

## LUT의 종류

1) Technical LUTs

테크니컬 LUT는 이미지를 하나의 색공간(color space 또는 gamut)에서 다른 색공간으로 옮기기 위해 만들어졌다.  해당 LUT의 최종 목표는 두 가지 다른 시청 환경에서 똑같은 결과물을 만들어내는 것이다. 예를 들면, TV에서 보는 것과 잉크젯 프린터로 출력해서 보는 결과를 똑같이 맞춰주는 것이다.   

2) Creative LUTs

크리에이티브 LUT는 다른 소프트웨어에서도 늘 한결같이 LUT가 가진 하나의 룩을 표현할 수 있게 해준다.

3) Camera LUTs

카메라 LUT의 좋은 예가 ARRI Alexa의 Rec709 LUT다.  이 LUT는 ARRI의 flat한 LOG-C에 적용하기 위해 디자인 되어 있다.  이런 종류의 LUT는 technical LUT와 creative LUT를 합친 결과물이라고 할 수 있다.

하지만 카메라의 노출값의 영향을 받기 때문에 해당 카메라로 촬영한 모든 사진에 일괄적으로 정확하게 적용할 수는 없다.


# What is Logspace?


