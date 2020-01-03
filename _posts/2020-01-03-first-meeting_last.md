---
title: 2020 동계모각코 1회차 - 후기
date: 2020-01-03 14:00:00 +0900
tags:
    - blog

---



### 저는 이번 시간에 아두이노의 서보모터와 블루투스 모듈에 대해 공부해 보았습니다.

![복습](/TC/1/servo1.PNG)

위에 보시는 이미지가 SG90이라는 모델명을 가지고 있는 서보모터입니다. 이 서보모터는 굉장히 저렴하지만, 0~180도까지밖에 회전이 안되는 큰 단점을 가지고 있습니다.

서보모터의 주황색 핀은 데이터 핀이고 빨간색은 (+)전압을 가지는 VCC를 나타내며, 갈색(검은색)은 (-)전압을 가지는 GND를 나타냅니다.


![복습](/TC/1/servo.PNG)

위 코드는 서보모터를 실습하기 위해 아두이노 프로그램에서 작성한 c++ 코드입니다.

servo라이브러리를 include하여 라이브러리 내부에 있는 Servo의 객체를 만들어 코드를 진행하였습니다.

위 코드에서 뜬금없이 Serial은 아두이노에서 가장 자주사용되는 기능 중 하나로, Serial 모니터를 통해 결과값을 확인할 수 있는 입출력을 담당합니다.

Serial.available()은 데이터를 입력받을 수 있도록 해주는 함수입니다. Serial을 통해 수신한 데이터가 있을 때 true를 리턴합니다.

Serial.read() 함수는 Serial을 통해 입력된 데이터를 가져오는 함수입니다.

저희 코드에서는 char 타입의 변수 in_data에 Serial.read()로 입력받은 데이터를 저장하였습니다.

void setup() 함수를 살펴보면, servo를 7번 포트에 할당하고 Serial.begin()으로 Serial을 시작합니다.

void loop() 함수에서는 Serial의 데이터를 입력 받아 그 데이터가 1일 경우, value에 30을 더해줍니다.

여기서 value 값은 서보모터를 움직이기 위한 값으로, 서보모터는 0~180도까지밖에 동작하지 않으므로 value의 최대 값은 180입니다. 고로, value가 210일 경우 value를 0으로 초기화합니다.

즉, Serial에 1이 입력될때마다 servo.write(value)를 통해 서보모터의 각도를 30도씩 변화시킵니다.


***

![복습](/TC/1/bluetooth.PNG)

다음으로 공부한 부분은 HC-06이라는 모델명을 가진 블루투스 모듈을 활용하여 모바일과 블루투스 통신에 대해 공부해보았습니다.

HC-06은 4개의 핀을 사용합니다. RXD 핀은 데이터를 수신할 떄, TXD 핀은 데이터를 송신할 때, GND는 (-)전압을, VCC는 3.6~6V 사이의 전압을 넣으면 되므로 5V 단자에 연결하면 됩니다.

![복습](/TC/1/0.jpg)

위 사진이 제가 공부할 때 찍은 사진입니다.

LED 앞쪽에 있는 저항들은 LED를 보호하기 위한 저항입니다. LED의 필요전압은 2V인데 대부분의 아두이노 우노 보드의 공급전압은 5V이므로 LED에 과부하가 걸리게 되어 망가지게 될 우려가 있어 저항을 달아 과부하가 걸리지 않도록 하였습니다.

![복습](/TC/1/bluetooth1.PNG)
![복습](/TC/1/bluetooth2.PNG)

위 코드는 블루투스 모듈을 활용한 코드입니다.

SoftwareSerial 라이브러리를 먼저 include하여 SoftwareSerial의 객체 BTSerial(2,3)을 생성하여 공부를 진행하였습니다. 여기서 2와 3은 포트번호인데, 각각 TXD 핀과 RXD 핀이 가리키는 번호입니다.

void setup() 함수를 살펴보면, BTSerial.begin(9600) 으 Serial 통신을 초기화하고 전송속도를 설정하는 함수입니다.

그리고 전역변수로 미리 설정해두었던 Green, Yellow, Red를 pinMode로 포트와 엮어줍니다.

void loop() 함수를 살펴보면,

BTSerial.available() 함수를 통해 통신이 가능한 상태일 때, bt라는 char 형 변수에 BTSerial.read() 통해 들어온 값을 bt에 저장합니다. bt의 값이 a,b,c,d,e,f,g에 따라 해당하는 문장을 실행합니다.

digitalWrite(Green,HIGH) 함수는 Green 포트에 있는 LED를 키라는 뜻이고,
digitalWrite(Green, LOW) 함수는 Green 포트에 있는 LED를 끄라는 뜻입니다.

그리고 'g'가 입력으로 들어왔을 때 BTSerial.end() 함수로 Serial 통신을 종료합니다.

![복습](/TC/1/5.jpg)
BTSerial.read() 값이 'a' 일 때, digitalWrite() 함수를 통해 녹색 LED를 켭니다.

![복습](/TC/1/4.jpg)
BTSerial.read() 값이 'b' 일 때, digitalWrite() 함수를 통해 노랑 LED를 켭니다.

![복습](/TC/1/3.jpg)
BTSerial.read() 값이 'c' 일 때, digitalWrite() 함수를 통해 빨강 LED를 켭니다.

![복습](/TC/1/2.jpg)
BTSerial.read() 값이 'd' 일 때, digitalWrite() 함수를 통해 녹색 LED를 끕니다.

![복습](/TC/1/1.jpg)
BTSerial.read() 값이 'e' 일 때, digitalWrite() 함수를 통해 노랑 LED를 끕니다.

![복습](/TC/1/bluetooth3.jpg)
위 사진은 모바일에서 실행한 bluetooth controller 어플리케이션 실행을 캡쳐한 사진입니다.

앱스토어에서 아무 bluetooth controller를 다운받아 진행하였고, 잘 동작되는 것을 확인할 수 있었습니다.

아두이노에 대해 더 공부할 수 있는 유익한 시간이었습니다.
