# 1. cygwin 이용하여 다운로드한 binutils 빌드 시 에러 발생.
-> 그리하여 cygwin을 이용하여 바이너리만 받고

-> http://ftp.gnu.org/gnu/binutils 에서 바이너리와 같은 버전의 소스코드를 /usr/src/에 다운로드하여 다시 빌드하니 정상적으로 완료.

---

# 2. gcc 빌드 완료 후 gcc -m64 -otest64 test.txt는 잘되지만 gcc -m32 -otest32 test.txt는 안됨.(64비트 운영체제여서 그런가)
-> http://jsandroidapp.cafe24.com/xe/index.php?mid=development&page=1&document_srl=8197 의 글을 따라해도 됩니다.

-> 직접 해본 뒤 한승훈 저자님에게 직접 물어본 결과 gcc 생성 후 /usr/cross/bin/x86_64-pc-linux-gcc -dumpspecs | grep -A1 multilib_options 명령어를 통해 m64/m32 가 출력되면 됩니다.

---

# 3. cygport gcc.cygport prep 명령어로 GCC 압축파일 해제 에러.
-> cp gcc-10.2.0-1.src 디렉토리 내에 tar.xz 파일을 /usr/src/ 디렉토리 밑으로 복사한다.

---

# 4. 서적에 나온대로만 하면 오류가 발생한다.
-> binutils 빌드가 안된다던가

-> 명령어가 안 먹는다.

---

# 5. 우분투 20.04-1 버전에서 gcc -m32 -o test32 test.c 테스트 할 시 bits/libc-header-start.h 파일이 없다고 뜨는 에러.
-> sudo apt-get install gcc-multilib g++-multilib 명령으로 패키지 설치하면 완료.

-> https://my-repo.tistory.com/12 참고.
