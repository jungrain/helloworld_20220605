# 리눅스 명령어 조사 (top, ps, jobs, kill)

---

## 1. top

- 시스템의 상태를 전반적으로 가장 빠르게 파악 가능한 명령어 이다.
- 옵션 없이 입력하면 interval 간격(기본 3초)으로 화면을 갱신하며 정보를 보여준다.
- top 실행 후 명령어

|명령어|기능|
|:---|:---|
|shift + p | CPU 사용률 내림차순|
|shit + m | 메모리 사용률 내림차순|
|shift + t | 프로세스가 돌아가고 있는 시간 순|
|k | kill. k 입력 후 PID 번호 작성. signal은 9|
|f | sort field 선택 화면 -> q 누르면 RES순으로 정렬|
|a | 메모리 사용량에 따라 정렬|
|b | Batch 모드로 작동|
|1 | CPU Core별로 사용량 보여줌|

- ps와 top의 차이점
1) ps는 ps한 시점에 proc에서 검색한 cpu 사용량
2) top은 proc에서 일정 주기로 합산해 cpu 사용율 출력
