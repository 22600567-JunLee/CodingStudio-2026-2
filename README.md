# C 프로그래밍 · GitHub 실습

GitHub와 VS Code로 C 코드를 가져와서, 고치고, 컴파일하고, 다시 올리는 과정을 위한 **안내 페이지**입니다.
실습은 아래 **실습 저장소**를 Fork해서 진행합니다. 앞으로 나올 과제도 같은 방법으로 진행합니다.

## 실습 저장소

**두 저장소 모두** Fork → Clone → 컴파일·실행 → Push 까지 해 주세요. W14_1을 먼저 끝내고, 같은 순서로 W14_2를 한 번 더 합니다.

| 저장소 | 링크 | 데이터 파일 | printf를 넣을 위치 |
| --- | --- | --- | --- |
| W14_1 (다윗관) | https://github.com/kkim-hgu/CodingStudioW14_1 | `members.txt` | `count = loadMembers(members);` 바로 아래 |
| W14_2 (객실 예약) | https://github.com/kkim-hgu/CodingStudioW14_2 | `rooms.txt` | `count = loadCards(cards);` 바로 아래 |

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

실습 저장소 폴더를 VS Code로 연 상태에서, VS Code 터미널에 입력합니다.

```bash
gcc main.c -o main
```

Windows (PowerShell): 한글이 깨지지 않게 `chcp 65001`을 먼저 입력합니다 (터미널을 새로 열 때마다 한 번).

```powershell
chcp 65001
```

```powershell
.\main.exe
```

Mac

```bash
./main
```

## 할 일 (W14_1, W14_2 각각)

1. 실습 저장소를 **Fork** 해서 내 계정으로 복사합니다 (오른쪽 위 `Fork` 버튼).
2. **내 Fork**를 VS Code로 **Clone** 합니다 (Source Control → Clone Repository).
3. `main.c`에서 파일을 읽는 줄(위 표의 위치) 바로 아래에 `printf("Edited by 내이름\n");` 한 줄을 추가하고 저장합니다 (Ctrl/Cmd + S).
4. 위의 명령어로 컴파일하고 실행합니다. 첫 줄(`40명이 저장된 파일을 읽었습니다.` 또는 `14개의 객실 정보를 읽었습니다.`) 다음에 내 printf가 보이면 성공입니다. 메뉴에서 `1`은 목록, `0`은 종료입니다.
5. VS Code Source Control에서 `main.c`만 `+` → 메시지 입력 → **Commit** → **Sync Changes** 로 올립니다.
6. 내 GitHub 저장소 페이지에서 커밋이 올라갔는지 확인합니다.

## 자주 막히는 곳

| 증상 | 해결 |
| --- | --- |
| `gcc`을(를) 인식할 수 없다고 나옴 | Path 경로 확인 → VS Code와 터미널을 완전히 껐다 켜기 |
| Mac: `xcrun: error: invalid active developer path` | `xcode-select --install` 다시 실행 |
| Source Control에 "Install Git" 버튼만 보임 | Git 설치 후 VS Code 재시작 |
| Commit 때 "Please tell me who you are" | 위 3번 `git config` 두 줄 다시 입력 |
| Push 때 403 / Permission denied | 원본이 아니라 **내 Fork**를 Clone했는지 확인 |
| W14_2를 Clone하려는데 W14_1 창이 열려 있음 | File → New Window로 새 창을 열고 거기서 Clone |
| 수정했는데 실행 결과가 그대로 | 저장(Ctrl/Cmd + S) 후 다시 컴파일 |
| Windows: 한글 메뉴가 깨져 보임 | 실행 전에 `chcp 65001` 입력 (터미널마다 한 번) |
| 실행하자마자 프로그램이 꺼짐 | 데이터 파일(`members.txt` / `rooms.txt`)이 있는 저장소 폴더에서 실행 |
| 이상한 컴파일·경로 에러 | 폴더 경로에서 한글·공백 빼기 (예: `C:\dev`) |

## 참고

- 실행 파일은 올리지 않습니다. Windows의 `main.exe`는 자동으로 빠지지만, Mac의 `main`은 Source Control 목록에 보이니 `+` 하지 마세요. `main.c`만 올리면 됩니다.
