# What is Color? A digital color?

## 1. 속성
### -색상(Hue)
![색상환표](https://postfiles.pstatic.net/20150427_74/midesse_1430144974938VYAAJ_PNG/%B8%D5%BC%BF.png?type=w2)

우리가 볼 수 있는 수 많은 색들 중에서 대표적인 색들은 고리 모양으로 만들어 놓은 것을 '색상환'이라 한다. 빨강, 주황, 노랑, 연두, 초록, 청록, 파랑, 남색, 보라, 자주 등의 10색상환과 미국의 화가 먼셀이 교육용으로 고안한 20색상환이 있다. 

색상환에서 서로 마주보고 있는 두 색을 적절한 비율로 섞으면 무채색이 되는 두가지 색을 __보색__ 이라고 한다.

### -채도(Saturaion)
![채도](https://search.pstatic.net/common/?src=http%3A%2F%2Fblogfiles.naver.net%2F20110503_194%2Fdifferentn_1304433039304CIdWJ_JPEG%2F%25C3%25A4%25B5%25B5.JPG&type=sc960_832)

채도는 색이 강렬한 정도를 나타낸다. 유채색에만 있으며 다른 색과 섞일 수록 채도가 낮아진다. 

### -명도(Value,Brightness)
![명도](https://i.pinimg.com/564x/ba/ce/06/bace06df34addddc6895edebd22c69bb.jpg)

명도는 색의 밝고 어두운 정도를 뜻한다. 명도는 색이 다른 색에 비해서 얼마나 밝고 어두운가를 나타낸다. 

## 2. 빛의 3원색, 색의 3원색
![3원색](https://search.pstatic.net/common/?src=http%3A%2F%2Fblogfiles.naver.net%2FMjAxNzAxMTZfMjE0%2FMDAxNDg0NTcwMzQ0ODU0.VDlynlQ-Zdt8LeuI8pshxn3AIT-sFyUA-F7GcDj2o1Ig.AZIfyLS2Z8HTDdZ-Uz6zxj0NScHUswwVkAXqYY0vI0wg.JPEG.spp0805%2F%25BA%25FB%25C0%25C73%25BF%25F8%25BB%25F6%25B0%25FA%25BB%25F6%25C0%25C73%25BF%25F8%25BB%25F64.jpg&type=sc960_832)

빛의 3원색은 Red, Green, Blue.
색의 3원색은 Cyan, Magenta, Yellow, Black 이다.
### -가산혼합

빛을 가하여 색을 혼합할 때, 혼합한 색이 원래의 색보다 명도가 높아지는 혼합. 가산혼합에서는 적, 녹, 청의 3색을 여러 강도로 섞으면 어떤 색이라도 얻을 수 있다. 이 원리는 컬러 텔레비전을 비롯하여 조명 등에 이용되고 있다. 그리고 가산혼합에서의 보색인 2색을 섞었을 때 하얀색이 되는 경우를 말한다.

### -감산혼합

혼합색이 원래의 색보다 명도가 낮아지도록 색을 혼합하는 방법. 감산혼합에서는 마젠타, 노랑, 시안을 여러 강도로 섞으면 어떤 색이라도 만들 수 있다. 이 원리는 컬러사진이나 수채화 등에 이용된다. 이 혼합에서의 보색은 회색 또는 검정색이 된다.

## 3. Digital Color
디지털 신호에 의해 만들어진 색채 표현 방법으로 최소의 단위는 비트(Bit)이며, 비트수는 디지털 색수를 결정. 컴퓨터의 모니터는 빛의 3원색인 빨강, 파랑, 초록의 전자총에서 발사되어 형광에면에 부딪쳐 색을 나타낸다. 작은 점(비트)이 모여 화소(Pixel픽셀)를 나타내며 화소는 디지털 이미지의 최소 단위로 이미지의 선명도와 질선명도을 결정짓는 요소로 픽셀 수에 의해 차이가 나게 된다.
[네이버 지식백과] 디지털 컬러 [digital color] (색채용어사전, 2007., 박연선, 국립국어원)

8 bit = 2^8 = 256

16 bit = 2^16 = 65536

24 bit = 2^24 = 16777216

![8](https://i.pinimg.com/originals/2c/9c/7f/2c9c7f9dfde6deebafc444918a01d0f5.gif)
8bit 그래픽

![16bit](https://i.pinimg.com/564x/d4/af/c7/d4afc7210160b8c6d1b88020ff34b49c.jpg)
16bit 그래픽

# What is Alpha?

알파 채널(영어: alpha channel) 또는 알파 합성(영어: alpha compositing)은 α 채널과 이미지 처리 분야에 있고, 각 화소에 대해 색상 표현의 데이터로부터 분리한 보조 데이터를 일컫는다.

개인용 컴퓨터의 경우, 프린터나 디스플레이 장치를 비롯한 대부분의 표시 장치는 RGB(빨강 초록 파랑), CMYK 등 단색의 편성에 따라 색을 표현한다. 각각의 단색의 밝기, 농도를 조정함에 따라 인간이 느낄 수 있는 많은 색을 표현할 수 있다. 개인용 컴퓨터 안의 데이터에서도 이같은 형식을 취하고 있다.

몇 개의 이미지 데이터나 이미지 소프트웨어에서는 이렇게 표시되는 단색 말고도 직접 표시되지 않는 색의 데이터를 넣을 수 있다. 이것을 알파 채널이라고 부르며, 화상 마스크, 복구 화상 합성 등에 쓰인다.

영상 편집에서는 키잉에 상응한다. 투명, 반투명 효과에 이용할 수 있다. 

![알파](https://upload.wikimedia.org/wikipedia/commons/thumb/2/2a/Alpha_compositing.svg/642px-Alpha_compositing.svg.png)

(출처 : 위키백과)

![마스킹](https://helpx.adobe.com/content/dam/help/en/photoshop/using/saving-selections-alpha-channel-masks/_jcr_content/main-pars/image_0/se_13.png)

A. 배경을 보호하면서 나비를 편집하는 데 사용한 불투명 마스크 

B. 나비를 보호하면서 배경을 칠하는 데 사용한 불투명 마스크 

C. 배경과 나비 일부를 칠하는 데 사용한 반투명 마스크

이미지의 일부를 선택할 때 선택되지 않은 영역은 마스크 영역이 되어 편집되지 않는다. 따라서 마스크를 사용하면 이미지 영역에 색상 변경, 필터 또는 기타 효과를 적용하는 동안 이미지의 나머지 부분을 분리시켜 보호할 수 있다. 이미지에 색상이나 필터 효과를 단계적으로 적용하는 등의 복잡한 이미지 편집에 마스크를 사용할 수도 있다.

마스크는 알파 채널에 저장된다. 마스크와 채널은 회색 음영 이미지이므로 다른 모든 이미지와 마찬가지로 페인팅 도구, 편집 도구 및 필터를 사용하여 편집할 수 있다. 마스크에 검은색으로 페인트된 영역은 보호되고 흰색으로 페인트된 영역은 편집할 수 있다.


