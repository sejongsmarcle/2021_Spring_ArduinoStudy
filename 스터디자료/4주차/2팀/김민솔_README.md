## 4주차 서브모터
#### 늦어서 죄송합니다..

오랜만이라 그런지 아두이노가 거부하더라고요...ㅜ  
우선 서브모터 사용법을 익혀 보았습니다!  

### 서브모터 사용
https://drive.google.com/file/d/1t3vqfvaGS1fCjG_WUkeHFqsBmNrGs7x2/view

### 서브모터 활용 !
처음에는 전 주차에 배웠던 초음파 센서를 이용하여 거리에 따라 각도가 다르게 움직이는 친구를 만드려고 하였습니다  
그런데 보드에 과부하가 걸려서 실행이 안 됐습니다..  
https://drive.google.com/file/d/1o6v8uWmOH8m340n1n0KZ0-CkDdCmEbIv/view  
불빛 딱 꺼질 때 진짜 너무하더라고요  

#### 알고 보니 코드에 문제가 있던 것 같습니다 초음파 센서는 리얼타임으로 계속해서 신호를 받기 때문에 loop문이 쉬지 않고 돌아가다보니 과부하가 걸린 것 같네요..  
#### delay문을 사용하면 되지 않을까 싶습니다!

### 서브모터 활용 재시도
저번 주차에 신호등 만들었던 것이 생각이 나서 신호등이 바뀔 때마다 팔도 같이 움직이게 해주었습니다.


#### 사용 코드

      #include <Servo.h>
      Servo myservo;
      int yellow = 12;
      int green = 10;
      int red = 8;

      void setup() {
        myservo.attach(9);
        pinMode(green,OUTPUT);
        pinMode(yellow,OUTPUT);
        pinMode(red,OUTPUT);
      }

      void loop() {

        digitalWrite(green,HIGH);
        digitalWrite(yellow,LOW);
        digitalWrite(red,LOW);
        myservo.write(30);
        delay(1000);

        digitalWrite(green,LOW);
        digitalWrite(yellow,HIGH);
        digitalWrite(red,LOW);
        myservo.write(60);
        delay(1000);

        digitalWrite(green,LOW);
        digitalWrite(yellow,LOW);
        digitalWrite(red,HIGH);
        myservo.write(90);
        delay(1000);


      }
      
      
      
이렇게 코드 진행하여서 다음과 같이 만들었습니다!  
https://drive.google.com/file/d/1Rw_943yV3qAAa5eiXzJ3pAAkyhH0ymFi/view  
약간 교통 정리 하는 느낌도 드는 것 같습니다 ㅋㅎ  
4주차 미션은 이렇게 진행해보았는데 잘한지 모르겠네요..  
다음 주차 미션도 열심히 해보겠습니다!






