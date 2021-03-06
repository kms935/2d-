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


# What is Logspace? and what is main difference with sRGB, why and when we use?

실사 기능을 작업 할 때 일반적으로 디지털 촬영의 제품으로 만들어진 일련의 원시 이미지를 의미하는 샷이 제공됩니다. 이 샷은 촬영 카메라에 따라 원시 형식으로 제공되며 로그 또는 선형 공간이 될 수 있습니다. 이는 특히 포토샵에서 페인팅 할 때 금방 혼란 스러울 수 있으므로 이러한 색상 공간의 차이점과 화가의 관점에서 접근하는 방법을 살펴 보겠습니다.

선형 대 sRGB

선형 색상 공간에서 저장된 숫자와 숫자가 나타내는 값 간의 관계는 선형 1 : 1 비율입니다. 즉, 예를 들어 숫자를 두 배로 늘리면 강도가 두 배가됩니다. 정말 쉽게 들리지만 문제는 빛에 대한 인간의 눈 감도가 높은 강도보다 낮은 강도에서 훨씬 더 미세하다는 것입니다. 특히 값을 표현하기 위해 8 비트를 사용하는 경우 (총 256 개의 음영을 의미 함), 너무 많은 밝은 음영이 발생하고 어두운 음영이 충분하지 않게됩니다

![1](https://cdnb.artstation.com/p/media_assets/images/images/000/394/819/medium/image00.jpg?1552184196)

따라서 선형 공간은 컴퓨터 처리에 사용하기에 완벽한 의미가 있지만 우리 눈은 동일한 간격 사이에서 거의 동일한 양의 밝기 변화를 볼 것으로 기대하기 때문에 사람이 보는 데 적합하지 않습니다. 예를 들어, 우리의 뇌는 32 번 음영이 16보다 2 배 더 밝고 48 번 음영 (32 + 16과 같음)이 32보다 2 배 더 밝을 것으로 예상합니다.
이 문제를 해결하기 위해 대부분의 최신 모니터는 감마 곡선을 사용하여 색상을 비선형으로 만드는 표준 인 sRGB라는 변환을 적용합니다. 곡선은 하단이 더 얕아서 더 어두운 값을 표시하고 상단이 더 가파르 기 때문에 더 적은 라이트 값을 가질 수 있습니다.

![2](https://cdna.artstation.com/p/media_assets/images/images/000/394/820/medium/image02.jpg?1552184260)

이제 우리는 linear와 sRGB가 무엇을 의미하는지 간략히 살펴 보았으므로 다음과 같은 문제에 직면 해 있습니다. 우리는 이미지가 컴퓨터 친화적이지만 인간 친화적 인 sRGB에 저장되는 선형 공간에서 처리되기를 원합니다. 그러나 우리는 이미 8 비트 선형에 어두운 음영이 충분하지 않다는 것을 확인했기 때문에 선형으로 변환 할 때 문제가 발생할 수 있습니다. 따라서 우리가 찾은 해결책은 8 비트에서 16/32 비트로 범위를 넓혀 작업 할 수있는 훨씬 더 어두운 음영을 갖는 것입니다. 이러한 종류의 이미지를 HDR (High Dynamic Range)이라고하며 일반적으로 32 비트 OpenEXR (.exr)로 저장됩니다.

그래서 문제가 해결 되었나요? 아닙니다. 32 비트로 작업하는 것이 옵션 이었다면 이 기사가 필요하지 않았을 것입니다. 아아, 대부분의 Photoshop 도구는 8 비트 또는 16 비트 모드에서만 제대로 작동하며 일반 8/16 비트 sRGB 작업 영역 내에서 32 비트 선형 이미지를 다시 보려고 할 때 발생하는 두 가지 문제가 있습니다.

1. 소프트웨어가 이러한 모든 정보를 표시하는 방법을 알 수없는 경우 관리되지 않는 32 비트 선형 이미지는 매우 높은 대비를 나타내며, 이는 매우 어두운 중간 톤과 과다 노출 된 하이라이트를 의미합니다. 이 문제의 일부는 역 감마 곡선을 적용하여 해결할 수 있습니다.

2. 32 비트 HDR 이미지를 8 비트 LDR에 해당하는 이미지로 변환하는 것은 파괴적인 프로세스입니다. 처음에 저장하려고했던 모든 추가 정보가 손실되기 때문입니다. 이것은 일반적으로 '값 클리핑'이라고하므로 컴포 지터가 그림에 충분한 범위가 없거나 '잘렸다'고 말할 때 일반적으로 강조 표시 및 / 또는 그림자에 충분한 세부 정보가 없음을 의미합니다. 참고 : 이것은 8 비트 작업 공간에서 그림을 시작하고 만든 다음 comp로 전달할 때도 발생합니다.

![3](https://cdnb.artstation.com/p/media_assets/images/images/000/185/191/medium/comparison2.jpg?1516129275) 왼쪽 이미지는 관리되지 않는 선형 32 비트 이미지를 나타냅니다. 오른쪽 이미지는 적절한 관리 뷰입니다

**로그**

로그를 색상 공간 "아카이버"로 생각할 수 있습니다 (파일에 대해 zip 또는 rar가 수행하는 것과 동일한 방식). 선형 공간은 동일한 단계로 값을 증가시키는 반면 로그 색상 공간은 이미지의 흰색 및 검은 색 영역의 값을 압축하여 정보를 저장하는 데 필요한 공간을 최소화하기 때문입니다 

![4](https://cdnb.artstation.com/p/media_assets/images/images/000/394/821/medium/image01.jpg?1552184324)

https://tiberius-viris.artstation.com/blog/3ZBO/color-space-management-srgb-linear-and-log

![참고](https://assets.rocketstock.com/uploads/2017/05/logvscorrected1.gif)

Linear -> Log

https://www.rocketstock.com/blog/tips-for-log-color-space-compositing/
