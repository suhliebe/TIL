# 영상의 명암비 조절

명암비란 영상에서 밝은 영역과 어두운 영역 사이에 드러나는 밝기 차이의 강도를 의미한다.

영상의 밝기 조절은 정수 값을 더하거나 빼는 연산이라면, 명암비 조절은 곱셉 연산으로 구현한다.

![](https://github.com/bongwon-suh/TIL/blob/master/img/1001/04.png?raw=true)



입력 영상 픽셀 값에 상수 s를 곱한 결과가 255보다 클 수 있으므로 포화 연산도 같이 수행해야 한다.

상수 s가 1보다 큰 경우에는 명암비가 높아지고, s가 1보다 작은 경우 명암비가 낮아진다.

그러나 이 수식을 이용하면 결과 영상이 어두워지거나, 밝기가 너무 쉽게 포화되는 단점이 있다

명암비를 효과적으로 높이기 위해서는 밝은 픽셀은 더욱 밝게, 어두운 픽셀은 더욱 어둡게 변경해야되고 

이때 픽셀 값이 어둡다는 기준을 어떻게 설정할 것인지가 영상의 품질 차이를 가져오게 된다.

예로는 그레이스케일 중간값은 129을 기준으로 명암비를 조절하는 방법이 있고 수식으로 정리하면,

![](https://github.com/bongwon-suh/TIL/blob/master/img/1001/05.png?raw=true)



이 수식에서 α는 -1보다 같거나 큰 실수이고, (128,128) 좌표를 항상 지나가게 되고 α 값에 의해 기울기가 변경되는 직선의 방정식이다.

-1<=α<=0 이면 기울기가 0부터 1사이의 직선의 방정식, 명암비를 감소시키는 변환 함수

α > 0이면 기울기가 1보다 큰 직선의 방정식,  명암비를 증가시크는 변환 함수

또, 255보다 커지는 경우가 발생 할 수 있으므로 포화 연산도 해야한다.

![](https://github.com/bongwon-suh/TIL/blob/master/img/1001/06.png?raw=true)