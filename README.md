# MiniC Compiler

이 프로젝트는 사용자가 정의한 간단한 C-like 언어(MiniC)를  
x86-64 Linux 어셈블리로 변환하는 컴파일러입니다.

> ⚠️ **중요: 본 프로젝트는 Linux(SysV ABI) 환경에서만 정상 동작합니다.**  
> Windows/Mac에서는 실행되지 않으며, 반드시 **WSL 또는 순수 Linux 환경**에서 실행해야 합니다.

---

## 📌 의존성(Dependencies)

Ubuntu/WSL 기준 다음 패키지가 필요합니다:

```bash
sudo apt update
sudo apt install gcc make flex bison
```

---

## 🔧 빌드(Build)

프로젝트 루트에서:

```bash
make clean
make
```

빌드 후 실행 파일이 생성됩니다:

```bash
./minic_x86
```

---

## ▶️ 실행 방법(Run)

MiniC 소스 파일을 어셈블리로 변환:

```bash
./minic_x86 test/add2.minic
```

어셈블리(`out.s`)를 실행 가능한 바이너리로 빌드:

```bash
gcc -no-pie out.s -o prog
./prog
echo $?
```

---

## 📁 프로젝트 문서

프로젝트의 상세 설명(문법 정의, AST 구조, 구현 기능, 테스트 프로그램 설명 등)은  
아래 문서에 정리되어 있습니다:

👉 **설명서.md**

---

## ⚠️ 리눅스 환경 필수 안내

본 컴파일러는 다음 이유로 **Linux에서만 실행이 가능합니다**:

- Linux SysV x86-64 ABI 기반으로 함수 호출 규약 구현  
- `.globl`, 스택 프레임 구조, rdi/rsi 레지스터 규약 사용  
- GCC(Linux)로만 실행 가능한 어셈블리 생성  

따라서 **WSL, Ubuntu, Debian 등 Linux 환경에서 실행해야 합니다.**  
Windows MinGW 환경에서는 out.s 실행이 불가능합니다.

---

## License

This project is for educational use only.
