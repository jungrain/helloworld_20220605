# 리눅스 명령어 조사 (top, ps, jobs, kill)

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

```bash
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

-`jotb` 명령어 사용법
```bash
jobs [옵션] [job ID]

jobs -x command [args]
```

- jobs 옵션
|옵션 |설명|
|:---|:---|
|-l | 프로세스 그룹 ID를 state 필드 앞에 출력|
|-n | 프로세스 그룹 중에 대표 프로세스 ID를 출력|
|-p | 각 프로세스 ID에 대해 한 행씩 출력|
|command | 지정한 명령어를 실행|

- `jobs' 로 알 수 있는 세션의 상태 값

|상태|설명|
|:---|:---|
|Running |작업이 일시 중단되지 않았고 종료하지 않고 계속 진행 중임|
|Done |작업이 완료되어 0을 반환하고 종료 했음을 의미|
|Done(code) |작업이 정삭적으로 완료되었으며, 0이 아닌 코드를 반환 했음을 의미|
|Stopped |작업이 일시 중단|
|Stopped(SIGTSTP) SIGTSTP |신호가 작업을 일시 중단|
|Stopped(SIGSTOP) SIGSTOP |신호가 작업을 일시 중단|
|Stopped(SIGTTIN) SIGTTIN |신호가 작업을 일시 중단|
|Stopped(SIGTTOU) SIGTTOU |신호가 작업을 일시 중단|

> 출처 :  [jobs - 현재 세션의 작업 상태를 출력](https://shaeod.tistory.com/968 "주요 내용 출처") 

---

## 4. kill

- 프로세스에 시그널을 보내는 명령어이다.
- kill 시그널 리스트 

```
$ kill -l
 1) SIGHUP	 2) SIGINT	 3) SIGQUIT	 4) SIGILL	 5) SIGTRAP
 6) SIGABRT	 7) SIGBUS	 8) SIGFPE	 9) SIGKILL	10) SIGUSR1
11) SIGSEGV	12) SIGUSR2	13) SIGPIPE	14) SIGALRM	15) SIGTERM
16) SIGSTKFLT	17) SIGCHLD	18) SIGCONT	19) SIGSTOP	20) SIGTSTP
21) SIGTTIN	22) SIGTTOU	23) SIGURG	24) SIGXCPU	25) SIGXFSZ
26) SIGVTALRM	27) SIGPROF	28) SIGWINCH	29) SIGIO	30) SIGPWR
31) SIGSYS	34) SIGRTMIN	35) SIGRTMIN+1	36) SIGRTMIN+2	37) SIGRTMIN+3
38) SIGRTMIN+4	39) SIGRTMIN+5	40) SIGRTMIN+6	41) SIGRTMIN+7	42) SIGRTMIN+8
43) SIGRTMIN+9	44) SIGRTMIN+10	45) SIGRTMIN+11	46) SIGRTMIN+12	47) SIGRTMIN+13
48) SIGRTMIN+14	49) SIGRTMIN+15	50) SIGRTMAX-14	51) SIGRTMAX-13	52) SIGRTMAX-12
53) SIGRTMAX-11	54) SIGRTMAX-10	55) SIGRTMAX-9	56) SIGRTMAX-8	57) SIGRTMAX-7
58) SIGRTMAX-6	59) SIGRTMAX-5	60) SIGRTMAX-4	61) SIGRTMAX-3	62) SIGRTMAX-2
63) SIGRTMAX-1	64) SIGRTMAX

```

- 주요 시그널


|시그널|	영어|	설명|
|:---|:---|:---|
|1) SIGHUP	|Hang Up	|세션이 종료될 때 시스템이 내리는 시그널|
|2) SIGINT|	Interrupt	|Ctrl + C, 종료 요청 시그널|
|9) SIGKILL|	Kill	|강제 종료 시그널|
|11) SIGSEGV|	Segment Violation|	메모리 침범이 일어날 때 시스템이 보내는 시그널|
|15) SIGTERM	|Terminate	|기본 값, 종료 요청 시그널|
|20) SIGTSTP	|Temporary Stop	Ctrl + Z| 일시 중지 요청 시그널|

- 프로세스에 시그널 보내는 방법

```bash
$ kill [option] PID

# 1234(PID) 프로세스 종료 
$ kill -9 1234
$ kill -SIGKILL 1234
```
> 출처 :  [리눅스 kill 명령어](https://frogand.tistory.com/69 "주요 내용 출처")
---

# vim 에디터에서 매크로 사용법

- 매크로란 특정한 움직임 또는 입력을 키에 저장함으로써 단순하면서 반복되는 동작을 쉽고 빠르게 해주는 것을 말한다.
- vim에서 매크로는 명령어 모드에서 `q + 알파벳`을 눌러 특정 알파벳에 매크로를 저장할 수 있다.
- **매크로 순서**

1. `q + a(알파벳)`    ( _a키에 recording 시작_)
2. 반복을 위한 내가 원하는 동작
3. `q `         ( _recoding 종료_)
4. `@a`         ( _1회 실행_) **or** `@@`         (_방금 실행한 매크로 실행_)  **or** `10@a`      (_매크로 10회 실행_)

> 출처 :  [vim의 꽃 macro(매크로) 사용법!](http://aboutmadlife.blogspot.com/2014/09/linux-vi-macro.html "주요 내용 출처")
