---
title: 2020 동계모각코 3회차 - 후기
date: 2020-01-14 14:10:00 +0900
tags:
    - blog

---

### 저는 이번 시간에 아두이노의 가변저항과 초음파 센서를 활용한 서보모터 활용에 대해 공부해 보았습니다.


![복습](/TC/3/1.PNG)

위에 보시는 이미지가 b10k라는 모델명을 가진 가변저항입니다.

가변저항이란, 값이 고정되어 있는 기존의 저항들과는 다르게 저항값을 변경할 수 있는 저항을 뜻합니다.

저는 이 가변저항을 이용하여 led의 밝기를 조절하도록 해보았습니다.

![복습](/TC/3/1.jpg)

![복습](/TC/3/2.jpg)

위의 두 이미지를 자세히 살펴보면, led의 밝기가 다르다는 것을 알수 있습니다. 이는 가변저항의 위에 달린 손잡이같이 생긴 부분을 돌리면서 저항값을 다르게 해주었을 때 나타나는 결과입니다.

![복습](/TC/3/b10k_code.PNG)

예제로 사용한 소스코드는 위와 같습니다.

가변저항의 입력핀을 0번으로 설정하고, led 핀을 13번으로 설정합니다.

analogRead() 함수는 지정한 아날로그 핀에서 값을 입력받아오는 함수입니다. 아까 가변저항 입력값의 핀을 0번으로 설정해주었으므로 0번핀의 값을 읽어오게 됩니다.


다음으로 공부한 내용은 초음파 센서를 활용한 서보모터 활용 부분입니다.

![복습](/TC/3/2.PNG)

초음파 센서는 위와같이 생겼습니다. 초음파를 활용하여 거리를 재는 센서입니다.

소스코드를 먼저 살펴보겠습니다.

![복습](/TC/3/lcd_servo.PNG)
![복습](/TC/3/lcd_servo2.PNG)

출력장치가 없이 사용했을 때는 결과값을 잘 모르기 때문에 lcd 모니터를 활용하여 결과값이 바뀔 때 "open" 또는 "close"를 lcd에 출력하도록 하였습니다.

소스코드를 살펴보면, 7~12번 핀은 lcd를 사용하기 위해 사용되었습니다.

그리고 3번 핀은 초음파 센서의 송신부와 연결하고, 4번 핀은 초음파 센서의 수신부와 연결하였습니다.

servo.attach(2) 함수는 서보모터를 몇번 핀으로 컨트롤 할 지 설정하는 함수입니다. 여기서는 2번 핀과 연결하였습니다.

lcd.begin(16,2) 는 lcd를 사용하기 위해 쓰는 함수로, 여기서 16,2는 lcd의 크기를 말합니다. 한 화면에 가로 16, 세로 2의 총 32개의 문자를 표시할 수 있는 lcd를 사용하였습니다.

lcd.print() 함수는 lcd에 출력할 내용을 설정합니다.

pulseIn() 함수는 아두이노 핀으로 입력되는 펄스의 시간을 측정하는 함수입니다. 매개변수인 vale가 HIGH 이면 해당 핀의 입력이 LOW에서 HIGH로 변하는 순간부터 시간을 측정하여 다시 LOW로 바뀌는 시점까지의 시간을 마이크로초 단위로 반환합니다.

lcd.setCursor() 함수는 lcd의 어느부분부터 출력할지 설정하는 함수입니다.

정리하면, 초음파 센서를 활용하여 물체가 20보다는 멀고 50보다는 가까워질 경우, "출입"을 serial에 띄우고 lcd에 "open"을 출력합니다. 그 이외의 경우, serial에 "폐쇄" 를 출력하고, lcd에 "close"를 출력합니다.

![복습](/TC/3/3.jpg)

![복습](/TC/3/4.jpg)

![복습](/TC/3/5.jpg)