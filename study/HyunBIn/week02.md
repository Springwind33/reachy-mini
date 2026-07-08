# 2주차: 기본 동작 제어

## 시작하기 전에 : 시뮬레이션 환경 준비
```bash
# 1. 프로젝트 디렉토리로 이동
cd reachy_mini_project

# 2. 가상환경 활성화 (Windows)
.venv\Scripts\activate

# 3. 시뮬레이션 데몬 실행
reachy-mini-daemon --sim

# 4. 브라우저에서 확인
# http://localhost:8000 접속
```
## 시작하기 전에 : VS CODE 접속 / CMD 창에서 수정이 어려워서 사용
```bash
# 1. 파이썬 확장 기능(Extension) 설치
VS Code를 켭니다.
왼쪽 사이드바에서 **네모 4개 모양 아이콘(Extensions)**을 클릭합니다.
검색창에 Python을 입력합니다.
Microsoft에서 만든 Python 확장 프로그램을 찾아 **Install(설치)**을 누릅니다.

#2 작업 폴더 열고 파일 만들기
상단 메뉴에서 File -> Open Folder...를 눌러 코드를 저장할 폴더를 하나 선택합니다.
폴더가 열리면 왼쪽 탐색기 빈 곳을 우클릭하거나 New File 아이콘을 눌러 파일을 만듭니다.
파일 이름은 robot_test.py처럼 끝에 꼭 **.py**를 붙여서 만들어 줍니다.

#3 필요한 라이브러리 설치
로봇 제어용 라이브러리(reachy_mini)가 컴퓨터에 깔려있어야 코드가 작동합니다.
VS Code 상단 메뉴에서 Terminal -> New Terminal을 엽니다. (화면 아래에 검은 창이 뜹니다)
터미널 창에 아래 명령어(pip install reachy-mini)를 입력하고 엔터를 누릅니다.

#4 코드 복사 및 실행
만든 파일에 코드를 붙여넣고 저장(Ctrl + S)합니다.
화면 우측 상단에 있는 **세모 모양의 재생 버튼(Run Python File)**을 클릭하면 코드가 실행됩니다!
```

---
## 1. 머리 동작 제어 
### 1.1 기본 머리 동작 / y축 방향으로 -10 이동(왼쪽)

```python
from reachy_mini import ReachyMini
from reachy_mini.utils import create_head_pose

with ReachyMini() as mini:<img width="635" height="757" alt="1 3" src="https://github.com/user-attachments/assets/d32a3a77-be4e-41ef-9221-4002002f6e94" />

    # 머리를 왼쪽으로 10mm 이동 (y축 -10mm)
    pose = create_head_pose(y=-10, mm=True)
    mini.goto_target(head=pose, duration=2.0)

    # 초기 위치로 복귀
    pose = create_head_pose()  # 파라미터 없이 호출하면 기본 위치
    mini.goto_target(head=pose, duration=2.0)
```

<img width="635" height="757" alt="1 3" src="https://github.com/user-attachments/assets/02cf7662-8260-4533-8674-2823801fded7" />
