## 초음파센서와 연결해보기

![KakaoTalk_20210412_001150985_04](https://user-images.githubusercontent.com/81272875/114310063-6163f200-9b24-11eb-84dd-a9a4d91fc119.jpg)

초음파 센서와 아두이노를 연결해보았다.

오랜만에 해서 4핀이 어디어디에 해당하는지 기억이 나지 않아서 

인터넷을 참고해서 연결을 했다. 

그 후에 초음파 센서만 달기는 좀 그래서 거리에 따라 LED를 켜보기로 했다!!

## LED도 같이 연결 하기

![KakaoTalk_20210412_001150985](https://user-images.githubusercontent.com/81272875/114310707-a2f59c80-9b26-11eb-8048-f1d4e0787f11.jpg)

빨간색 켜보기 거리 (100cm 이상일때)

![KakaoTalk_20210412_001150985_01](https://user-images.githubusercontent.com/81272875/114310711-a7ba5080-9b26-11eb-9659-01502cf1ca88.jpg)

노란색 켜보기 (50cm 부터 100cm 미만)


초록색도 켰는데 사진을 안찍었나 봐요... ( 50cm 미만)

## 코드에서 오류 발생!!??

![잘못](https://user-images.githubusercontent.com/81272875/114310938-9aea2c80-9b27-11eb-9d5e-3dd70a929a98.png)

코드 업로드는 잘되는데 LED가 켜지질 않는다...

그래서 하나하나 잘 살펴 보니까 거리가 문제였다!

거리를 50 <= distance < 100의 형태가 아니라

50 <= distance && distance < 100의 형태로 적어야 했다!!

![수정](https://user-images.githubusercontent.com/81272875/114310982-d7b62380-9b27-11eb-99f3-75c9a5916157.png)

위의 코드는 수정 후의 코드로 정확하게 작동했다!!


## 코드


![red](https://user-images.githubusercontent.com/81272875/114310800-15ff1300-9b27-11eb-8121-7d4b2484fcc3.png)

빨간색 키는 코드

![yellow](https://user-images.githubusercontent.com/81272875/114310816-21523e80-9b27-11eb-8dbe-6e12d1342825.png)

노란색 키는 코드

![green](https://user-images.githubusercontent.com/81272875/114310821-28794c80-9b27-11eb-8bba-a1c080b397ca.png)

초록색 키는 코드

## 후기

해보면서 재미있었고 코로나 땜에 집에서만 박혀 있느라 무기력하고 힘들었는데 활동을 하면서 그나마 고등학교때 처럼 기력이 좀 든것 같다.

앞으로는 더 열심히 해야겠다.

그리고 미리 다 촬영을 해놓고 글을 안올렸다...

앞으로는 미리미리 해 놓아야 겠다.


