# C 프로그래밍 · GitHub 실습

GitHub와 VS Code로 C 코드를 가져와서, 고치고, 컴파일하고, 다시 올리는 과정을 한 번 해보는 저장소입니다.

## 할 일

1. 이 저장소를 **Fork** 해서 내 계정으로 복사합니다 (오른쪽 위 `Fork` 버튼).
2. **내 Fork**를 VS Code로 **Clone** 합니다 (Source Control → Clone Repository).
3. `hello.c`에 내 이름을 출력하는 `printf` 한 줄을 추가하고 저장합니다.
4. 터미널에서 컴파일하고 실행합니다.

   ```bash
   gcc hello.c -o hello
   ```

   - Windows (PowerShell): `.\hello.exe`
   - Mac: `./hello`

5. VS Code Source Control에서 `hello.c`만 `+` → 메시지 입력 → **Commit** → **Sync Changes** 로 올립니다.
6. 내 GitHub 저장소 페이지에서 커밋이 올라갔는지 확인합니다.

## 실행 결과 예시

```
Hello, C!
My name is Gildong
```

## 참고

- 실행 파일(`hello`, `hello.exe`)은 `.gitignore`에 들어 있어서 올라가지 않습니다. 코드(`.c`)만 올리면 됩니다.
- 출력 문구는 영어로 써 주세요. 한글은 Windows 터미널에서 깨질 수 있습니다.
- 폴더 경로에 한글이나 공백이 없는 곳(예: `C:\dev`)에서 작업하는 것을 추천합니다.
