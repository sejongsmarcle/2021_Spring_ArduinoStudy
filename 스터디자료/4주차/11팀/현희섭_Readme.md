## 오랜만에 만져보는 아두이노

![image](https://user-images.githubusercontent.com/81272875/117983932-59d97800-b372-11eb-9ade-22bee6bb036a.png)

시험이 끝나고 오랜만에 아두이노를 만졌다.   

사실 저번주에 했어야 했는데 시험이 끝났는데 갑자기 과제가 몰려와서 바쁘기도 했고 깜빡해서 하지 못했다. ㅠ

## 이번 주제는 서보모터!

![image](https://user-images.githubusercontent.com/81272875/117984096-7f668180-b372-11eb-87ec-6f4b535f4a95.png)

서보모터는 고등학교 1,2학년 때 많이 다뤘던 소품이다.  

고등학교 3학년때도 많이 다루고 싶었지만 코로나로 인해 활동을 거의 하지 못해서 다루지 못했다.  

그래서 다 까먹어 버렸다..

## 서보모터 분석

![image](https://user-images.githubusercontent.com/81272875/117984168-91482480-b372-11eb-8bd8-11a51ae201c7.png)

서보모터는 총 3개의 핀이 있다.

갈색 , 빨간색 , 주황색 핀이 있는데 갈색은 GND, 빨간색은 5V, 주황색 핀은 번호에다가 꽂아주면 된다. 보통은 9번에 하는 것 같다.  

![image](https://user-images.githubusercontent.com/81272875/117984793-192e2e80-b373-11eb-99fa-b9521f2035ef.png)  
서보모터를 사용하기 위해서는 #include <Servo.h>를 쳐주어야 한다.

![image](https://user-images.githubusercontent.com/81272875/117984829-221f0000-b373-11eb-931e-771bb42547a5.png)  
또한 Servo myservo(이름); 으로 선언해주어야 한다.

![image](https://user-images.githubusercontent.com/81272875/117984872-2e0ac200-b373-11eb-8dbd-3c0ce8b74a0f.png)  
myservo(이름).attach(번호);로 해주고 번호를 연결하면 서보모터를 사용할 수 있게 된다.

![image](https://user-images.githubusercontent.com/81272875/117984913-37942a00-b373-11eb-8c52-ee920ee81072.png)  
myservo(이름).write(각도); 를 통해서 각도만큼 서보모터를 돌릴 수 있다.

## 서보모터 사용하기

https://user-images.githubusercontent.com/81272875/117985144-68745f00-b373-11eb-8a83-cca487dc77af.mp4

![image](https://user-images.githubusercontent.com/81272875/117985279-8641c400-b373-11eb-92ed-0ad91f10bdc2.png)  
나는 반복문을 통해서 0도 부터 180도까지 돌아가게 하고

![image](https://user-images.githubusercontent.com/81272875/117985316-8e016880-b373-11eb-8adb-c26941bce2e2.png)  
180도 부터 0도까지 다시 돌아가게 코딩을 짰다.

이것만 하면 좀 그러니까 led를 같이 추가 했다.



![image](https://user-images.githubusercontent.com/81272875/117985861-0bc57400-b374-11eb-8bf7-3e58349eff68.png)  
빨간색 led가 켜질때는 기차가 길을 지날때 도로를 막는것 처럼 

![image](https://user-images.githubusercontent.com/81272875/117985821-00724880-b374-11eb-9e81-5fa5af4e8f7a.png)  
초록색 led가 켜질때는 반대로 여는것 처럼 생각을 해서 반대의 각도를 적용해서 구현했다.

https://user-images.githubusercontent.com/81272875/117985621-d4ef5e00-b373-11eb-9f5e-1518f5462f4e.mp4

## 코딩

![image](https://user-images.githubusercontent.com/81272875/117986212-5e069500-b374-11eb-9d39-de414ba9f7db.png)  
![image](https://user-images.githubusercontent.com/81272875/117986245-66f76680-b374-11eb-97c0-559c31499da4.png)

코딩은 이러하게 짰다.

## 후기

서보모터는 잘 사용하면 더 재미있는 센서이기 때문에 더 다양한 분야에 적용해 보고 싶었다.  
다른 것보다 생각보다 쉬웠던 것 같다. 앞으로는 더 열심히 노력해야겠다.
