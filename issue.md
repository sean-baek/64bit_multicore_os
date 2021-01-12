# 1. cygwin 이용하여 다운로드한 binutils 빌드 시 에러 발생.
-> 그리하여 cygwin을 이용하여 바이너리만 받고
-> http://ftp.gnu.org/gnu/binutils 에서 바이너리와 같은 버전의 소스코드를 /usr/src/에 다운로드하여 다시 빌드하니 정상적으로 완료.

# 2. gcc 빌드 완료 후 gcc -m64 -otest64 test.txt는 잘되지만 gcc -m32 -otest32 test.txt는 안됨.(64비트 운영체제여서 그런가)

