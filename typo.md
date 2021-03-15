1. 7장에서 01.Kernel32/makefile 부분 dependency가 dependancy로 표기된 부분이 많음
2. p232 ~ 233. kInitializeKernel64Address() 함수인데 다음 줄에서는 InitializeKernel64Address() 함수라고 되어 어있으며, 코드에서는 kInitializeKernel64Area라고 되어 있음
3. p240 BIOS 서비스를 통해 A20 게이트를 활성화하는 코드 : jc .A20GATERROR -> jc .A20GATEERROR로 되어야함

