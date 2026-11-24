# C 프로그래밍 · GitHub 실습

GitHub와 VS Code로 C 코드를 가져와서, 고치고, 컴파일하고, 다시 올리는 과정을 한 번 해보는 저장소입니다.
앞으로 나올 과제도 같은 방법으로 진행합니다.

## 링크 모음

| 무엇 | 링크 | 누가 |
| --- | --- | --- |
| GitHub 가입 | https://github.com | 모두 |
| VS Code 다운로드 | https://code.visualstudio.com/download | 모두 |
| Git 다운로드 | https://git-scm.com/downloads/win | Windows만 |
| MSYS2 다운로드 (C 컴파일러용) | https://www.msys2.org | Windows만 |

## 복사해서 쓰는 명령어

각 상자 오른쪽 위의 복사 버튼을 누르면 그대로 복사됩니다.

### 1. C 컴파일러 설치

**Windows**: MSYS2 설치 후 열리는 **MSYS2 UCRT64** 창에 입력 (물어보면 Enter 또는 Y)

```bash
pacman -S mingw-w64-ucrt-x86_64-gcc
```

**Windows**: 시작 메뉴에서 "환경 변수" 검색 → 계정의 환경 변수 편집 → 사용자 변수 `Path` → 새로 만들기 → 아래 경로 붙여넣기

```
C:\msys64\ucrt64\bin
```

**Mac**: 터미널에 입력 (C 컴파일러와 Git이 한 번에 설치됩니다)

```bash
xcode-select --install
```

### 2. 설치 확인 (공통)

새 터미널을 열고 입력합니다. 버전이 나오면 성공입니다.

```bash
gcc --version
```

```bash
git --version
```

### 3. Git에 내 정보 등록 (공통, 처음 한 번만)

따옴표 안만 바꿔서 입력합니다. 이메일은 GitHub에 가입한 이메일로 써 주세요.

```bash
git config --global user.name "내 이름"
git config --global user.email "GitHub 가입 이메일"
```

### 4. 컴파일과 실행

```bash
gcc hello.c -o hello
```

Windows (PowerShell)

```powershell
.\hello.exe
```

Mac

```bash
./hello
```

## 할 일

1. 이 저장소를 **Fork** 해서 내 계정으로 복사합니다 (오른쪽 위 `Fork` 버튼).
2. **내 Fork**를 VS Code로 **Clone** 합니다 (Source Control → Clone Repository).
3. `hello.c`에 내 이름을 출력하는 `printf` 한 줄을 추가하고 저장합니다 (Ctrl/Cmd + S).
4. 위의 명령어로 컴파일하고 실행합니다.
5. VS Code Source Control에서 `hello.c`만 `+` → 메시지 입력 → **Commit** → **Sync Changes** 로 올립니다.
6. 내 GitHub 저장소 페이지에서 커밋이 올라갔는지 확인합니다.

## 실행 결과 예시

```
Hello, C!
My name is Gildong
```

## 자주 막히는 곳

| 증상 | 해결 |
| --- | --- |
| `gcc`을(를) 인식할 수 없다고 나옴 | Path 경로 확인 → VS Code와 터미널을 완전히 껐다 켜기 |
| Mac: `xcrun: error: invalid active developer path` | `xcode-select --install` 다시 실행 |
| Source Control에 "Install Git" 버튼만 보임 | Git 설치 후 VS Code 재시작 |
| Commit 때 "Please tell me who you are" | 위 3번 `git config` 두 줄 다시 입력 |
| Push 때 403 / Permission denied | 원본이 아니라 **내 Fork**를 Clone했는지 확인 |
| 수정했는데 실행 결과가 그대로 | 저장(Ctrl/Cmd + S) 후 다시 컴파일 |
| 한글 출력이 깨짐, 이상한 컴파일 에러 | 출력 문구는 영어로, 폴더 경로에서 한글·공백 빼기 (예: `C:\dev`) |

## 참고

- 실행 파일(`hello`, `hello.exe`)은 `.gitignore`에 들어 있어서 올라가지 않습니다. 코드(`.c`)만 올리면 됩니다.
