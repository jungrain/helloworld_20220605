# 리눅스 명령어 조사 (top, ps, jobs, kill)

---

## 1. top

- top 명령어는 table of processes 의 약자로  CPU 와 메모리 이용에 관한 정보를 표시하는 수많은 유닉스 계열 운영 체제에서 볼 수 있는 작업 관리자 프로그램이다.
- 시스템의 상태를 전반적으로 가장 빠르게 파악 가능한 명령어 이다.
- 옵션 없이 입력하면 interval 간격(기본 3초)으로 화면을 갱신하며 정보를 보여준다.




- top 실행 전 명령어

|명령어|기능|
|:---|:---|
|`b`| 옵션 추가(batch 모드)|
|`n`|  top 실행 주기 설정(반복 횟수)|



- top 실행 후 명령어

|명령어|기능|
|:---|:---|
|`shift + p`| CPU 사용률 내림차순|
|`shit + m`| 메모리 사용률 내림차순|
|`shift + t`| 프로세스가 돌아가고 있는 시간 순|
|`k`| kill. k 입력 후 PID 번호 작성. signal은 9|
|`f`| sort field 선택 화면 -> q 누르면 RES순으로 정렬|
|`a`| 메모리 사용량에 따라 정렬|
|`b`| Batch 모드로 작동|
|`1`| CPU Core별로 사용량 보여줌|

- ps와 top의 차이점
1) ps는 ps한 시점에 proc에서 검색한 cpu 사용량
2) top은 proc에서 일정 주기로 합산해 cpu 사용율 출력

- top 명령어 출력화면 예시

![2_top 명령어 출력화면 (요약 출력 항목)](https://user-images.githubusercontent.com/106908417/172046312-29b14860-70b1-40ab-8d09-5e71a5672443.png)

- top 명령어 입력 예시
` top -b -n 1 `


-  **주의 : 옵션에 따른 문자열 입력 시 대소문자는 반드시 구분해서 입력해야 함.**

> 출처 :  [리눅스 top 정리 및 설명](https://zzsza.github.io/development/2018/07/18/linux-top/ "주요 내용 출처") , 
> [리눅스 top 명령어 출력화면 및 사용법 설명](https://koromoon.blogspot.com/2020/09/top.html "사진 출처")
