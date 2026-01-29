[작업플로우 정리 ]
>>> 로컬 WSIDFY브랜치에서 작업 후 로컬 dev브랜치랑 병합 진행하고 테스트 및 이상 없으면 원격 dev브랜치에 푸쉬

1. WSIDFY브랜치로 이동
git switch WSIDFY
2. 변경사항 스테이징 및 커밋
git add .
git commit -m "작업한 내용에 대한 메시지"
3. 로컬의 dev브랜치로 이동 및 원격최신 상태와 동기화
git switch dev
git pull origin dev (이미 연결 되어있으면 git pull만 진행)
4. WSIDFY 내용을 dev(로컬)에 merge
git merge WSIDFY (dev브랜치에서 실행해야함)
(이때 충돌나면 해결 후에 git add . > git commit을 해줘야 병합이 완료됨)
5. 원격 dev브랜치에 반영
git push origin dev


[깃 명령어 정리] ====================================
(연결된 레포지토리 해제)
git remote remove <원격_이름>

(원격 레포지토리와 연결)
git remote add <원격_이름> <원격_저장소_URL>
(ex. git remote add origin https://github.com/사용자이름/저장소이름.git)

(연결된 레포지토리 확인)
git remote -v

(기존 브랜치 해제)
git branch --unset-upstream

(원격 저장소 브랜치 확인)
git fetch

(브랜치 연결) - 기존에 커밋된 내용이 있어야 브랜치 연결 가능
git branch -u origin/<브랜치_이름>

(연결된 원격 브랜치 확인)
git branch -vv

(변경사항 브랜치에 올리기)
# 모든 변경사항 추가
git add . 
# 특정 파일만 추가
git add <파일명>

(커밋 생성)
git commit -m "커밋 메시지 입력"

(깃 푸쉬)
# 이미 연결(upstream)이 설정된 경우
git push
# 연결 설정과 동시에 푸시할 경우
git push -u origin <브랜치_이름>
# 강제로 푸시해야 할 경우 (주의 필요)
git push origin <브랜치_이름> -f

(깃 풀)
# 원격 저장소의 내용을 로컬로 덮어쓰기
1. 원격의 최신 상태 가져오기
git fetch --all

2. 원격 브랜치 내용을 로컬로 강제 리셋
git reset --hard origin/(브랜치명)

(수정 및 add된 파일 확인)
git status

(존재하는 모든 로컬 브랜치 확인)
git branch -a

(git switch로 브랜치 생성)
git switch -c development (develop브랜치 생성 및 전환)

(로컬 브랜치 삭제)
git branch -d foldering (-D는 강한 삭제)

(추적되지 않는 원격 브랜치를 보고있을 때 비워내기)
git fetch --prune

(로컬 브랜치 전환)
git switch (브랜치 명)

(원격 브랜치를 기준으로 새 브랜치 만들고 이동)
git switch -c feature/(새 브랜치) origin/(원격 브랜치 명)

+ (커밋별 내용 및 코드 확인)
git log --oneline --graph --all

(현재 작업진행도 임시저장) - stack구조
git stash (M - modify: 동일한 파일 구성 내에서 변경 코드만 추적해서 저장)
git stash -u (U - update : 추가로 생성된 파일까지 추적해서 저장)

(stash로 저장한 진행상황 불러오기) - 제일 최신순으로 적용
git stash pop

[가상 환경 구축 ] ====================================
(가상환경 만들기 - 공통)
python -m venv myvenv

(가상환경 실행하기 -  cmd)
myvenv\Scripts\activate

(가상환경 실행하기 - git bash)
source .venu/Scripts/activate (폴더명이 .venu)

(가상환경에서 나오기 - 공통)
deactivate

(가상환경 구동 중인지 확인)
which python 
> 이때 출력되는 경로 중간에 myvenv/Scripts/python가 포함된다면 가상환경 상태

[streamlit 실행 ] ====================================
(파일 실행)
streamlit run app.py

(특정 파일만 실행) - pages폴더의 test.py실행
cd pages (해당 폴더로 이동)
streamlit run .test.py (테스트 파일 실행)

[ VS code단축키 모음 ] ================================
(코드 잡고 통째로 옮기기)
원하는 열에 커서 두고 alt + 방향키(위/아래)

(폴더 전체에서 동일 변수명 한 번에 변경)
변수명 선택 + F12

(함수 혹은 클래스가 위치하는 파일로 바로 이동)
ctrl + 함수/클래스명 클릭

(여러 열에 동시입력)
alt + 입력할 행 선택, 타이핑

(다중 행 들여쓰기)
행 선택하고 ctrl + [ or ]

(다중 주석처리)
주석처리할 행 선택하고 ctrl + /
