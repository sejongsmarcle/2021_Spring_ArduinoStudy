## 4주차 미션
4주차..였던..미션..죄송합니다..선배님들..

종강을 하고나서야 4주차를 진행합니다...

다시한번 죄송하고 또 죄송하고..사랑합니다♥
### 서브모터
모터면 그냥 모터지 서브모터는 뭘까.라는 생각으로 4주차를 시작했다.

일단 모터란 전력을 공급받아 회전하는 장치를 뜻한다.

서보모터는 돌아가는 각도가 0도부터 180도 사이로만 회전한다.

다른 센서들처럼 케이블이 연결되어있는데

노란색 : 신호를 전달받는 케이블 

빨간색 : 전원을 공급받는 케이블

갈색 : 그라운드에 연결하여 접지를 하는 케이블


### 참참참!😝
서브모터를 이용하여 참참참 로봇을 만들어보았다!

아싸인 나에게 참참참은 사치..홀로 즐길 수 있는 참참참..

가슴이 옹졸해진다..😢

#### 회로연결
회로연결은 아래 사진처럼!
![KakaoTalk_20210622_005711627](https://user-images.githubusercontent.com/81364249/122792205-e7ef3980-d2f4-11eb-9f1b-c097b2b3a76b.jpg)

#### 코드

      #include <Servo.h>
      
      Servo charm;
      
      int num_tones=3;
      int tones=392;
      int tempo=100;


      void setup() {
        charm.attach(9);
        charm.write(90);
        pinMode(10,INPUT_PULLUP);
        pinMode(2,OUTPUT);
      }
      void direction(){
        int x;

        x=random(3);
        if (x==0){
          charm.write(20);
        }
        else if(x==1){
          charm.write(90);
        }
        else if(x==2){
          charm.write(120);
        }
      }

      void loop() {
        if (digitalRead(10)==LOW){
          for (int i=0;i<num_tones;i++){
             tone(2,tones,tempo);
             delay(1000);
          }
    
        direction();
        delay(3000);
        charm.write(90);
        }
      }
지금 혼자 이걸로 재밌게 노는중..
현재 전적 13연패
### 4주차 끝!
바로 5주차  갑니당><
