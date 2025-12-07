# MiniC Compiler

이 프로젝트는 사용자가 정의한 간단한 C-like 언어(MiniC)를  
x86-64 Linux 어셈블리로 변환하는 컴파일러입니다.

> **중요: 본 프로젝트는 Linux(SysV ABI) 환경에서만 정상 동작합니다.**  
> Windows/Mac에서는 실행되지 않으며, WSL 또는 순수 Linux 환경에서 실행해야 합니다.

---

## 의존성(Dependencies)

다음 패키지들이 필요합니다. (Ubuntu / WSL 기준)

```bash
sudo apt update
sudo apt install gcc make flex bison
🔧 빌드(Build)
프로젝트 루트에서:

bash
코드 복사
make clean
make
빌드 후 실행 파일이 생성됩니다:

bash
코드 복사
./minic_x86
실행 방법(Run)
MiniC 소스 파일을 어셈블리로 변환:

bash
코드 복사
./minic_x86 test/add2.minic
어셈블리(out.s)를 실행 가능한 바이너리로 빌드:

bash
코드 복사
gcc -no-pie out.s -o prog
./prog
echo $?
프로젝트 문서
프로젝트의 설계 문서, 문법(EBNF), 구조, 테스트 프로그램 설명, 실행 결과 등
모든 상세 문서는 다음 파일에 있습니다:

설명서.md

리눅스 환경 필수 안내
이 컴파일러는 다음 특징 때문에 Linux 환경 전용입니다:

Linux SysV x86-64 ABI 기반으로 함수 호출 규약 구현

.globl, 스택 프레임, rdi/rsi 등 Linux 규칙 사용

GCC(Linux)로만 실행 파일 생성 가능

반드시 WSL(Linux), Ubuntu, 또는 다른 Linux 환경에서 실행해야 합니다.

Windows MinGW 환경에서는 out.s가 실행되지 않습니다.
