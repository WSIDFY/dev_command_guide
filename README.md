# _Dev_commend_guide_

#### [ 추천 확장 ]
- `office matrial icon theme` : 파일 및 폴더 아이콘
- `Better Comments` : 주석에 종류별 색 입히기

#### [Tip]
> 저장할만한 덩어리의 수저사항이 생겼다면 바로바로 commit해서 남겨두기

## [ 작업플로우 정리 ]
> 로컬 A브랜치에서 작업 후 로컬 B브랜치랑 병합 진행하고 테스트 및 이상 없으면 원격 B브랜치에 푸쉬

1. <b>A브랜치로 이동</b><br>
  `git switch A`

2. <b> 변경사항 스테이징 및 커밋</b><br>
  `git add .`<br>
  `git commit -m "작업한 내용에 대한 메시지"`

3. <b>로컬의 B브랜치로 이동 및 원격최신 상태와 동기화</b><br>
  `git switch B`<br>
  `git pull origin B` (이미 연결 되어있으면 git pull만 진행)

4. <b>A 내용을 B(로컬)에 merge</b><br>
  `git merge A` (B브랜치에서 실행해야함)<br>
  (이때 충돌나면 해결 후에 `git add .` > `git commit`을 해줘야 병합이 완료됨)

5. <b>원격 B브랜치에 반영</b><br>
  `git push origin B`

---
### [ 깃 명령어 정리 ]

* <b>(연결된 레포지토리 해제)</b><br>
`git remote remove <원격_이름>`

* <b>(원격 레포지토리와 연결)</b><br>
`git remote add <원격_이름> <원격_저장소_URL>`<br>
(ex. `git remote add origin https://github.com/사용자이름/저장소이름.git`)

* <b>(연결된 레포지토리 확인)</b><br>
`git remote -v`

* <b>(기존 브랜치 해제)</b><br>
`git branch --unset-upstream`

* <b>(원격 저장소 브랜치 확인)</b><br>
`git fetch`

* <b>(브랜치 연결) - 기존에 커밋된 내용이 있어야 브랜치 연결 가능</b><br>
`git branch -u origin/<브랜치_이름>`

* <b>(연결된 원격 브랜치 확인)</b><br>
`git branch -vv`

* <b>(변경사항 브랜치에 올리기)</b><br>
  - case1. 모든 변경사항 추가<br>
  `git add .`

  - case2. 특정 파일만 추가<br>
  `git add <파일명>`

* <b>(커밋 생성)</b><br>
`git commit -m "커밋 메시지 입력"`

* <b>(깃 푸쉬)</b><br>
  - case1. 이미 연결(upstream)이 설정된 경우
    `git push`
  - case2. 연결 설정과 동시에 푸시할 경우<br>
    `git push -u origin <브랜치_이름>`
  - case3. 강제로 푸시해야 할 경우 (주의 필요)<br>
    `git push origin <브랜치_이름> -f`

* <b>(깃 풀)</b><br>
> 원격 저장소의 내용을 로컬로 덮어쓰기

  1. 원격의 최신 상태 가져오기<br>
    `git fetch --all`

  2. 원격 브랜치 내용을 로컬로 강제 리셋<br>
    `git reset --hard origin/(브랜치명)`

* <b>(수정 및 add된 파일 확인)</b><br>
`git status`

* <b>(존재하는 모든 로컬 브랜치 확인)</b><br>
`git branch -a`

* <b>(git switch로 브랜치 생성)</b><br>
`git switch -c development (develop브랜치 생성 및 전환)`

* <b>(로컬 브랜치 삭제)</b><br>
`git branch -d foldering (-D는 강한 삭제)`

* <b>(추적되지 않는 원격 브랜치를 보고있을 때 비워내기)</b><br>
  `git fetch --prune`

* <b>(로컬 브랜치 전환)</b><br>
`git switch (브랜치 명)`

* <b>(원격 브랜치를 기준으로 새 브랜치 만들고 이동)</b><br>
`git switch -c feature/(새 브랜치) origin/(원격 브랜치 명)`

* <b>(커밋별 내용 및 코드 확인)</b><br>
`git log --oneline --graph --all`

* <b>(현재 작업진행도 임시저장)</b> - stack구조<br>
`git stash` (M - modify: 동일한 파일 구성 내에서 변경 코드만 추적해서 저장)<br>
`git stash -u` (U - update : 추가로 생성된 파일까지 추적해서 저장)

* <b>(stash로 저장한 진행상황 불러오기)</b> - 제일 최신순으로 적용<br>
`git stash pop`

### [ 가상 환경 구축 ]
---
* <b>(가상환경 만들기 - 공통)</b><br>
`python -m venv myvenv`

* <b>(가상환경 실행하기 -  cmd)</b><br>
`myvenv\Scripts\activate`

* <b>(가상환경 실행하기 - git bash)</b><br>
`source .venu/Scripts/activate` (폴더명이 .venu)

* <b>(가상환경에서 나오기 - 공통)</b><br>
`deactivate`

* <b>(가상환경 구동 중인지 확인)</b><br>
`which python` <br>
(이때 출력되는 경로 중간에 myvenv/Scripts/python가 포함된다면 가상환경 상태)

### [ streamlit 실행 ]
---
* <b>(파일 실행)</b><br>
`streamlit run app.py`

* <b>(특정 파일만 실행)</b> - pages폴더의 test.py실행<br>
`cd pages` (해당 폴더로 이동)<br>
`streamlit run .test.py` (테스트 파일 실행)

### [ VS code단축키 모음 ]
---
* <b>(코드 잡고 통째로 옮기기)</b><br>
`원하는 열에 커서 두고 alt + 방향키(위/아래)`

* <b>(폴더 전체에서 동일 변수명 한 번에 변경)</b><br>
`변수명 선택 + F12`

* <b>(함수 혹은 클래스가 위치하는 파일로 바로 이동)</b><br>
`ctrl + 함수/클래스명 클릭`

* <b>(여러 열에 동시입력)</b><br>
`alt + 입력할 행 선택, 타이핑`

* <b>(다중 행 들여쓰기)</b><br>
`행 선택하고 ctrl + [ or ]`

* <b>(다중 주석처리)</b><br>
`주석처리할 행 선택하고 ctrl + /`
