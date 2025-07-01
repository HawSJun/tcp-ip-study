# tcp-ip-study
TCP/IP 프로토콜 학습을 위한 이론 정리

## 1일차

### ubuntu(우분투)

#### 명령어
| 명령어                         | 설명                                                               |
|------------------------------|----------------------------------------------------------------------|
| `uname -a`                   | 시스템 전체 정보 확인                                                |
| `cd [폴더명]`                | 지정한 폴더로 이동                                                   |
| `ls`                         | 현재 폴더의 파일 및 디렉터리 목록 출력                               |
| `pwd`                        | 현재 작업 디렉터리의 전체 경로 출력                                  |
| `cd ..`                      | 상위(전 단계) 폴더로 이동                                            |
| `./`                         | 현재 폴더를 의미                                                     |
| `../`                        | 상위 폴더를 의미                                                     |
| `mkdir [폴더명]`             | 새로운 폴더 생성                                                     |
| `clear`                      | 터미널 화면 지우기                                                   |
| `rm -fr [폴더명]`            | 폴더 및 그 하위 내용 강제 삭제 (`-f`: 강제, `-r`: 재귀적으로)        |
| `touch [파일명]`             | 빈 파일 생성 (예: `touch text.txt`)                                  |
| `cat [파일명]`               | 파일 내용 화면에 출력 (예: `cat 파일이름`)                           |
| `cp [원본] [대상]`           | 파일 복사 (예: `cp test.txt test1.txt`)                              |
| `mv [원본] [대상위치/이름]`  | 파일 또는 폴더 이동 또는 이름 변경 (예: `mv ./test.txt ../`)         |
| `gcc main.c -o main`         | `main.c`를 컴파일하여 `main` 실행 파일로 생성 (`-o`: 출력파일 지정)  | 
| `./[실행파일명]`             | 현재 폴더 내의 실행 파일 실행 (예: `./main`)                         |
| `sudo nano /etc/nanorc`      | nano 설정 파일 열기 (관리자 권한 필요)                               |
| `sudo apt install gcc`       | GCC 컴파일러 설치 (Debian/Ubuntu 계열에서)                           | 
| `chmod`                      | 파일 권한 변경 (r : 읽기(4), w : 쓰기(2), x : 실행(1))               |                                      |


1.  #include <fcntl.h> : 파일 오픈
    - int open(const char* name, int flags)
        - `flags` : O_RDONLY, O_WRONLY, O_RDWR, O_CREAT, O_TRUNC, O_APPEND

2. #include <unistd.h> 
    - ssize_t write(int fd, const void* buf, size_t nbytes);
    - ssize_t read(inr fd, void* buf, size_t count);

- Big Endian : 작은 주소에 큰 값 저장
- Little Endian : 작은 주소에 작은 값 저장


#### IPv4 인터넷 주소의 체계
- `클래스A` : 네트워크ID(1) + 호스트ID(3), 0 ~ 127 이하(0)
- `클래스B` : 네트워크ID(2) + 호스트ID(2), 128 ~ 191 이하(10)
- `클래스C` : 네트워크ID(3) + 호스트ID(1), 192 ~ 223 이하(110)
- `클래스D` : 멀티캐스트 주소 (구분 없음), 224 ~ 239 이하(1110)
- `클래스E` : 실험/예약용 (구분 없음), 240 ~ 255 이하(1111)

#### 프로토콜 체계
- PF_INET : IPv4 인터넷 프로토콜 체계
- PF_INET6 : IPv6

#### 소켓의 타입(전송 방식)
- `TCP` (Transmission Control Protocol)
    - 연결지향형 소켓
    - 데이터를 안전하게 받을 수 있음, 신뢰성 있는 데이터 전송
    - SOCK_STREAM
- `UDP` (User Datagram Protocol)
    - 비연결지행형 소켓
    - 데이터를 안전하게 받을 수 있지안 TCP에 비해 약함, 빠르지만 신뢰성이 없음
    - SOCK_DGRAM


inet_addr : 192.168.0.1 -> 이 문자열을 16진수로 변환하는 함수(점 찍혀있는 문자를 변환?)

AF_INET(주소체계) = PF_INET(프로토콜패밀리)