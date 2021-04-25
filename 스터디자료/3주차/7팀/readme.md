3주차) 초음파 센서 이용하기
===========================

### 초음파 센서 연결하기

#### 초음파 센서
<img src="https://user-images.githubusercontent.com/81242086/115994807-7e63ef00-a613-11eb-8a0b-97e765421b97.png"  width="450" height="450">
<img src="https://user-images.githubusercontent.com/81242086/115994811-82900c80-a613-11eb-8f5d-2886160bad56.png"  width="450" height="450">

초음파 센서는 초음파를 보내 반사되는 시간을 측정하는 센서이다, 측정한 시간과 초음파 속력의 곱으로 거리를 측정할 수 있다!

*주의 왕복시간을 측정하여 (거리)=(속력)x(시간)/2임!*

trig: 초음파 송신 -> input

echo: 초음파 수신 ->output

<img src="https://user-images.githubusercontent.com/81242086/115995100-e109ba80-a614-11eb-9daf-c1cbad33ecd1.png"  width="450" height="450">

Vcc-5V

trig-디지털 7핀

echo-디지털 8핀

GND-GND로 연결해 주었다


#### 코딩하기
<img src="https://user-images.githubusercontent.com/81242086/115995115-eff06d00-a614-11eb-8391-d4e7238e1689.png"  width="450" height="600">

HIGH: 전원공급

LOW: 전원공급 X




echo가 초음파를 수신할 때 HIGH가 되어

pulseIn 함수 사용를 사용하여 시간을 측정해 준다

시간의 단위가 μs(마이크로세컨즈) 1s=1000m/s=1000000us

초음파 속력:340m/s으로 

시간, 길이 단위를 s,cm로 맞추어 준 뒤 

길이를 출력해 준다 



#### 결과물!
 [장애물과의 거리 측정](https://youtu.be/2Yi_zM6x5Xw)
 
 줄자를 이용하여 거리가 정확히 측정되는지 확인하였다 
 
 다행히 정확히 측정중이었당

### 후방 감지 센서 만들기 

#### 부저 추가하기
<img src="https://user-images.githubusercontent.com/81242086/115995108-e6ff9b80-a614-11eb-950d-7c3a1a168106.png"  width="450" height="450">

장애물과의 거리에 따라 경고음을 내주기 위해서 부저를 추가 해 준다!

부저에는 +,-가 있는데 친절히 표시되어 있었당

부저의 +극은 3번 핀에 

-극은 모두 브레드보드의 -에 모아 한 번에 연결 해 주었다 


#### 코딩하기

<img src="https://user-images.githubusercontent.com/81242086/115995122-f5e64e00-a614-11eb-95a5-ee294c9714ae.png"  width="500" height="700">

책상 길이의 한계로 50cm부터 경고음을 울리게 하였다

10cm 마다 경고음의 주파수와 반복횟수를 높여주었다



#### 결과물
 [후방 감지 센서](https://youtu.be/MaxpSZvtVmk)
 
 이것 역시 줄자를 이용해 정확히 10cm 마다 소리가 달라지는지 확인하였다
 
 중간고사 끝나고 하는 아두이노 너무 재밌었다! 
 
 
