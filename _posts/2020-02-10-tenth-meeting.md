---
title: 2020 동계모각코 10회차 - 목표
date: 2020-02-10 18:15:00 +0900
tags:
    - blog

---

목표 : Baekjoon Online Judge 2문제 풀기

 - 백준 15953(상금헌터)

문제
 2017년에 이어, 2018년에도 카카오 코드 페스티벌이 개최된다!

 카카오 코드 페스티벌에서 빠질 수 없는 것은 바로 상금이다. 2017년에 개최된 제1회 코드 페스티벌에서는, 본선 진출자 100명 중 21명에게 아래와 같은 기준으로 상금을 부여하였다.

 순위	상금	인원
 1등	500만원	1명
 2등	300만원	2명
 3등	200만원	3명
 4등	50만원	4명
 5등	30만원	5명
 6등	10만원	6명
 2018년에 개최될 제2회 코드 페스티벌에서는 상금의 규모가 확대되어, 본선 진출자 64명 중 31명에게 아래와 같은 기준으로 상금을 부여할 예정이다.

 순위	상금	인원
 1등	512만원	1명
 2등	256만원	2명
 3등	128만원	4명
 4등	64만원	8명
 5등	32만원	16명


 제이지는 자신이 코드 페스티벌에 출전하여 받을 수 있을 상금이 얼마인지 궁금해졌다. 그는 자신이 두 번의 코드 페스티벌 본선 대회에서 얻을 수 있을 총 상금이 얼마인지 알아보기 위해, 상상력을 발휘하여 아래와 같은 가정을 하였다.

 제1회 코드 페스티벌 본선에 진출하여 a등(1 ≤ a ≤ 100)등을 하였다. 단, 진출하지 못했다면 a = 0으로 둔다.

 제2회 코드 페스티벌 본선에 진출하여 b등(1 ≤ b ≤ 64)등을 할 것이다. 단, 진출하지 못했다면 b = 0으로 둔다.

 제이지는 이러한 가정에 따라, 자신이 받을 수 있는 총 상금이 얼마인지를 알고 싶어한다.

 입력
 첫 번째 줄에 제이지가 상상력을 발휘하여 가정한 횟수 T(1 ≤ T ≤ 1,000)가 주어진다.

 다음 T개 줄에는 한 줄에 하나씩 제이지가 해본 가정에 대한 정보가 주어진다. 각 줄에는 두 개의 음이 아닌 정수 a(0 ≤ a ≤ 100)와 b(0 ≤ b ≤ 64)가 공백 하나를 사이로 두고 주어진다.

 출력
 각 가정이 성립할 때 제이지가 받을 상금을 원 단위의 정수로 한 줄에 하나씩 출력한다. 입력이 들어오는 순서대로 출력해야 한다.


 - 백준 15954(인형들)

문제
 카카오프렌즈 스토어에서는 N종류의 인형을 팔고 있다. N개의 인형들 중에서는 잘 팔리는 인형과 그렇지 않은 인형들이 섞여 있어서 잘 팔리는 인형은 상대적으로 사람들이 많이 볼 수 있는 곳에 배치하고, 잘 팔리지 않는 인형은 상대적으로 사람들이 적게 볼 수 있는 곳에 배치한다. 그러므로 배치된 곳이 가까운 두 인형은 상대적으로 판매량이 비슷하다고 할 수 있다.

좋은 배치를 정하기 위해서 어느 날, 여러 명의 사람들을 대상으로 인형의 선호도를 조사하였다. 조사 결과 각 인형에 대해서 선호하는 사람의 수를 모두 구하였고, 그에 따라 인형의 배치를 정하려고 한다.

카카오프렌즈 스토어를 관리하는 브라이언은 어떠한 특정한 곳에 인형들을 배치하고자 하는데, 그곳에 인형들을 선택하는 방법은 다음과 같다:

먼저 비슷한 인형이 가깝게 위치하도록 서로 다른 N개의 인형을 종류당 한 개씩 일렬로 배치한다.
그 후, 선호하는 사람의 수의 표준편차가 최소가 되는, K개 이상의 연속된 위치에 있는 인형들을 선택하여 그들을 같은 곳에 배치한다.
위의 방법으로 인형들을 선택했을 때, 선택된 인형들의 선호하는 사람의 수의 표준편차를 구하여라.

N개의 수 a1, a2, …, aN이 주어져 있을 때, 통계학에서 (산술) 평균은 (a1 + a2 + … + aN) / N 으로 정의한다. 이를 m으로 정의하자. 또한, 분산은 ((a1 - m)2 + (a2 - m)2 + … + (aN - m)2) / N으로 정의하고, 표준 편차는 분산의 음이 아닌 제곱근으로 정의한다.

입력
첫 번째 줄에 N과 K가 주어진다. N은 1 이상 500 이하의 정수이고, K는 1 이상 N 이하의 정수이다.

두 번째 줄에는 N개의 정수가 입력되며, 이는 인형이 일렬로 나열된 순서대로 인형을 선호하는 사람의 수이다. 각 수는 모두 106 이하의 음이 아닌 정수이다.

출력
선택된 인형들을 선호하는 사람의 수의 표준 편차를 출력한다. 출력한 결과와 실제 답을 비교하였을 때의 상대/절대 오차가 10-6 이하인 경우에만 정답으로 인정한다.
