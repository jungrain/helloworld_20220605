# 리눅스 명령어 조사 (top, ps, jobs, kill)

---

## 1. top

- `top` 명령어는 table of processes 의 약자로  CPU 와 메모리 이용에 관한 정보를 표시하는 수많은 유닉스 계열 운영 체제에서 볼 수 있는 작업 관리자 프로그램이다.
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


***


## 2. ps

- `ps`는 process status 의 줄인말 이다.

- 현재 실행중인 프로세스의 목록을 보는 명령어 이다.  _윈도우의 작업관리자 같은 것_

- 옵션 표

|옵션|기능|
|:---|:---|
|`-E` | 실행중인 모든 프로세스의 정보를 출력한다.|
|`-F`| 프로세스에 대한 자세한 정보룰 출력한다.( PPID 확인 가능 )|
|`-U`| 사용자이름  : 특정 사용자에 대한 모든 프로세스의 정보를 출력|
|`-P PID`| PID로 지정한 프로세스의 정보를 출력|
|`U`| 프로세스 소유자의 이름, CPU 사용량, 메모리 사용량 등 상세 정보를 출력|
|`A`| 터미널에서 실행한 프로세스의 정보를 출력|
|`X`| 실행 중인 모든 프로세스의 정보를 출력|


- ps 사용법

```
$ ps [option]

System V : $ ps -ef
BSD : $ ps aux
```

- *ps로 알 수 있는 정보들!*

|항목 |의미|
|:---|:---|
|USER   |  BSD계열에서 나타나는 항목으로 프로세스 소유자의 이름|
|UID   |  SYSTEM V계열에서 나타나는 항목으로 프로세스 소유자의 이름|
| PID  |   프로세스의 식별변호 |
|PPID  |   부모 프로세스 ID|
| %CPU  |   CPU 사용 비율의 추정치(BSD)|
|%MEM  |   메모리의 사용 비율의 추정치 (BSD)|
|VSZ  |   K단위 또는 페이지 단위의 가상메모리 사용량|
|RSS |    실제 메모리 사용량 (Resident Set Size)|
|TTY  |   프로세스와 연결된 터미널 |
|S, STAT |    현재 프로세스의 상태 코드 (S: Sys V, STAT: BSD)|
|TIME   |  총 CPU 사용 시간|
|COMMAND  |   프로세스의 실행 명령행|
|STIME   |  프로세스가 시작된 시간 혹은 날짜|
|C, CP  |   짧은 기간 동안의 CPU 사용률 (C: Sys V, CP: BSD)|
|F   |  프로세스의 플래그 |
|PRI |    실제 실행 우선순위|
|NI  |   nice 우선순위 번호 |


-ps 명령어 사용 예시

![List-Processes-in-Standard-Format](https://user-images.githubusercontent.com/106908417/172047215-445fcd3a-14d3-4ca3-9e95-fbe4b8d9b74c.png)

> 출처 :  [ps 프로세스 명령어 완벽정리](https://jhnyang.tistory.com/268/ "주요 내용 출처") ,
>  [리눅스의 필수!! ps 명령어 총정리](https://newstars.cloud/468 "주요 내용 출처") ,
> [30 Useful ‘ps Command’ Examples for Linux Process Monitoring](https://www.tecmint.com/ps-command-examples-for-linux-process-monitoring/ "사진 출처")


***


## 3. jobs

- 리눅스 명령어 `jobs`는 작업이 중지된 상태, 백그라운드로 진행 중인 작업 상태, 변경 되었지만 보고되지 않은 상태 등을 표시하는 명령어다.
