초음파 센서 다뤄보기

int echo = 9; //echo핀 9번핀에 연결
int trig = 10; //trig핀 10번핀에 연결

void setup() {
  Serial.begin(9600);
  pinMode(echo, INPUT);
  pinMode(trig, OUTPUT);
}

void loop() {

  digitalWrite(trig, HIGH);//high는 전원 공급 상태
  delay(2);
  digitalWrite(trig, LOW);//low는 전원 공급이 안되는 상태

  float duration = pulseIn(echo, HIGH);//시간 구하기 위해 pulsein함수 이용
  
  float distance = duration / 1000000 * 100 * 340 / 2;// 거리 = 속력(초음파 속력: 340m/s)*시간 , 듀레이션 값이 마이크로 세컨즈니까 /백만을 해줘야하고 100을 곱해줘야함, 왕복이기 때문에 2로도 나눠줘야함.

  Serial.print(distance);
  Serial.println(" cm");
}

![image](https://user-images.githubusercontent.com/81521991/114290076-d8af6c80-9ab7-11eb-9d12-c5eb1f06692c.png)

![image](https://user-images.githubusercontent.com/81521991/114290065-c46b6f80-9ab7-11eb-9649-8ee4f6985c97.png)


자동차 후방 감지기! (초음파센서, 피에조부저 이용)

int trig = 10;
int echo = 9;
int buzzer = 10;

void setup() {
  Serial.begin(9600);
	
	pinMode(trig, OUTPUT);
  pinMode(echo, INPUT);
}

void loop() {
	
  digitalWrite(trig, HIGH);
	delay(2);
  digitalWrite(trig, LOW);
	
	float duration, distance;
	
	duration = pulseIn(echo, HIGH);
  distance = duration * 0.034 / 2;

	if (distance >= 100 || distance <= 0){
    tone(buzzer, 100, 10);
    Serial.println("장애물이 없습니다.");

    }
  else if(distance <= 60 && distance >= 51){
    tone(buzzer, 500, 50);
    Serial.println("60cm내에 장애물이있습니다.");
  }
  else if(distance <= 50 && distance >= 41){
    tone(buzzer, 1000, 100);
    Serial.println("50cm내에 장애물이있습니다.");
  }
  else if(distance <= 40 && distance >= 31){
    tone(buzzer, 1500, 200);
    Serial.println("40cm내에 장애물이있습니다.");
  }
  else if(distance <= 30 && distance >= 21){
    tone(buzzer, 2000, 400);
    Serial.println("30cm내에 장애물이있습니다.");
  }
  else if(distance <= 20 && distance >= 11){
    tone(buzzer, 2500, 600);
    Serial.println("20cm내에 장애물이있습니다.");
  }
  else if (distance <= 10 && distance >= 1){
    tone(buzzer, 3000, 1000);
    Serial.println("조심하세요!!");
  }
  
  delay(500);
}

![image](https://user-images.githubusercontent.com/81521991/114290273-735c7b00-9ab9-11eb-9700-700721b75d9b.png)

![image](https://user-images.githubusercontent.com/81521991/114290267-5d4eba80-9ab9-11eb-94c8-688c0a35dea2.png)
