# 1. cygwin 이용하여 다운로드한 binutils 빌드 시 에러 발생.

-> binutils 유닛 테스트가 추가되어서 생긴 문제.

-> 1번째 방법
- cygwin을 이용하여 바이너리만 받고, http://ftp.gnu.org/gnu/binutils 에서 바이너리와 같은 버전의 소스코드를 /usr/src/에 다운로드하여 다시 빌드하니 정상적으로 완료.
- https://sean.tistory.com/5 에 정리해두었음.

-> 2번째 방법
- 한승훈 저자 님의 최신 github 글을 보면 빌드 관련 명령어 입력 시 옵션 --disable-unit-tests  추가.
- https://github.com/kkamagui/mint64os-examples

---

# 2. gcc 빌드 완료 후 gcc -m64 -otest64 test.txt는 잘되지만 gcc -m32 -otest32 test.txt는 안됨.

-> 직접 해본 뒤 한승훈 저자님에게 직접 물어본 결과 크로스 컴파일러 생성 후 터미널에 /usr/cross/bin/x86_64-pc-linux-gcc -dumpspecs | grep -A1 multilib_options 명령어를 통해 m64/m32 가 출력되면 됩니다.

-> 참고 1
- 자신의 윈도우가 64bit이면 gcc -m32 모드가 안되고, 32bit이면 gcc -m64 모드가 안된다.

-> 참고 2
- http://jsandroidapp.cafe24.com/xe/index.php?mid=development&page=1&document_srl=8197 의 글을 따라해도 됨.

---

# 3. cygport gcc.cygport prep 명령어로 GCC 압축파일 해제 에러.

-> cygport gcc.cygport prep에서 gcc 버전이 표시가 안되어 있었음.

-> 방법 1
- cp gcc-10.2.0-1.src 디렉토리 내에 tar.xz 파일을 /usr/src/ 디렉토리 밑으로 복사한다.
- https://sean.tistory.com/5 참고.

-> 방법 2
- 한승훈 저자 님의 최신 github 글 따라하기.
- https://github.com/kkamagui/mint64os-examples

---

# 4. 우분투 20.04-1 버전에서 gcc -m32 -o test32 test.c 테스트 할 시 bits/libc-header-start.h 파일이 없다고 뜨는 에러.

-> sudo apt-get install gcc-multilib g++-multilib 명령으로 패키지 설치하면 완료.

-> https://my-repo.tistory.com/12 참고.

---

# 5. 우분투 20.04-1 버전에서 책의 120p qemu 실행 시 -localtime 옵션이 되지 않음.
-> https://www.mankier.com/1/qemu 와 https://wiki.qemu.org/Features/RemovedFeatures 를 참고하니 -rtc base=localtime으로 대체되었다고 되어있음.
-> https://github.com/kkamagui/mint64os-examples issue로 등록해두었음

---

# 6. windows10 64bit eclipse에서 build all하면 cannot run program "make" : Launching failed가 뜸
-> https://yagi815.tistory.com/929 을 참고하여 mingw32-make.exe을 복사하여 make.exe로 이름을 바꾸어서 붙여넣기

---

# 7. Ubuntu의 최신 QEMU에서 정상적으로 부트 로더와 가상 OS 이미지 테스트가 실행되지 않음
-> http://jsandroidapp.cafe24.com/xe/qna/11322 을 참고하여 cmp al, 19에서 cmp al, 37로 바꾸었음

---

# 8. 책에서 7.2 part make 수행 시 링커 스크립트169번 라인 오류
-> 주석 처리하여 빌드 오류를 방지 
-> https://github.com/sean-baek/64bit_multicore_os/blob/main/01.Kernel32/elf_i386.x

---

# 9. 책에서 7.3 part FS64 OS의 makefile를 빌드하면 ./ImageMaker이 없다면서 빌드 오류
-> 04.Utility/00.ImageMaker/ImageMaker라고 수정하여 ImageMaker를 참조하게 함.

---

# 10. ImageMaker.c에서 open() 함수 파라미터 중 O_BINARY가 없기 때문에 빌드 오류
-> 총 4번의 open() 함수가 사용되는데, 모두 O_BINARY 옵션을 제거
