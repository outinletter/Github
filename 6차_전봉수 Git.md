- git init : git 생성하기
- it config --global user.name "유저 이름" : 깃 사용자 이름 설정
- git config --global user.email "이메일 주소" : 깃 사용자 이메일 설정
- git config --global core.editor "vim" : 커밋 편집에디터를 vim으로 변경하기
- git clone git_path : 코드가져오기
- git checkout branch_name : 브랜치 선택하기
- git checkout -t remote_path/branch_name : 원격 브랜치 선택하기
- git branch branch_name : 브랜치 생성하기
- git branch -r : 원격 브랜치 목록보기
- git branch -a : 로컬 브랜치 목록보기
- git branch -m branch_name change_branch_name : 브랜치 이름 바꾸기
- git branch -d branch_name : 브랜치 삭제하기
- git push remote_name — delete branch_name : 원격 브랜치 삭제하기 ( git push origin — delete gh-pages )
- git add file_path : 수정한 코드 선택하기 ( git add * )
- git commit -m “commit_description” : 선택한 코드 설명 적기 ( git commit -m “내용”)
- git push romote_name branch_name : add하고 commit한 코드 git server에 보내기 (git push origin master)
- git pull : git서버에서 최신 코드 받아와 merge 하기
- git fetch : git서버에서 최신 코드 받아오기
- git reset — hard HEAD^ : commit한 이전 코드 취소하기
- git reset — soft HEAD^ : 코드는 살리고 commit만 취소하기
- git reset — merge : merge 취소하기
- git reset — hard HEAD && git pull : git 코드 강제로 모두 받아오기
- git stash / git stash save “description” : 작업코드 임시저장하고 브랜치 바꾸기
- git stash pop : 마지막으로 임시저장한 작업코드 가져오기
- git branch — set-upstream-to=remote_path/branch_name : git pull no tracking info 에러해결
- git fetch : 원격 저장소의 브랜치 변화 정보만 가져오기
- git commit -am "\*메세지 내용\*" : 스테이징과 커밋을 메세지와 함께 올리기
- git commit --amend : 방금 커밋한 메세지 수정하기
- git checkout \*브랜치이름\* : '브랜치이름'으로 브랜치 이동
- git log \*브랜치1\* ..\*브랜치2\* : 브랜치1과 브랜치2사이의 차이점 보기
- git merge \*병합할브랜치이름\* : 브랜치 병합
- git log : 커밋 기록 보기
- git log --stat : 커밋 기록을 커밋에 관련괸 파일과 함께 보기
- git log --oneline : 로그를 한줄로 표기
- git log --oneline --branches : 각 브랜치의 커밋을 확인
- git checkout --\*파일이름\* : 작업트리에서 수정한 파일 되돌리기
- git reset HEAD \*파일이름\* : 스테이징 취소
- git reset HEAD^ : 최신 커밋 취소
- git reset \*커밋해시\* : 특정 커밋으로 되돌리기
- **git stash : 지금 하던 작업을 임시로 저장하기**
- git stash list : stash 목록 확인하기
- **git stash apply : git stash로 저장했던 작업 가져오기**
- **git stash drop : stash 제거하기**
- git stash clear : 임시로 저장했던 stash 모두 제거
- **git stash show -p | git apply -R : 실수로 잘못 stash 한거 되돌리기**
- git remote add origin \*원격저장소주소\* : 원격 저장소에 연결
- **git remote -v : 원격 저장소에 잘 연결되었는지 확인**
- git push -u origin master : 지역 저장소의 브랜치를 원격 저장소의 마스터 브랜치와 연결 (한번만 하면됨)
- git pull origin master : 원격 저장소의 내용을 지역 저장소의 마스터브랜치로 가져오기
- git fetch : 원격 저장소의 브랜치 변화 정보만 가져오기**



| 분류                          | 명령어                                              | 내용 설명                                                    |
| ----------------------------- | --------------------------------------------------- | ------------------------------------------------------------ |
| <새로운 저장소 생성>          | **$ git init**                                      | .git 하위 디렉토리 생성 (폴더를 만든 후, 그 안에서 명령 실행 => 새로운 git저장소 생성) |
| <저장소 복제/다운로드(clone)> | **$ git clone <https:.. URL>**                      | 기존 소스 코드 다운로드/복제                                 |
|                               | **$ git clone** **/로컬/저장소/경로**               | 로컬 저장소 복제                                             |
|                               | **$ git clone 사용자명@호스트:/원격/저장소/경로**   | 원격 서버 저장소 복제                                        |
| <추가 및 확정(commit)>        | **$ git add <파일명>** **$ git add \***             | 커밋에 단일 파일의 변경 사항을 포함 (인덱스에 추가된 상태)   |
|                               | **$ git add -A**                                    | 커밋에 파일의 변경 사항을 한번에 모두 포함                   |
|                               | **$ git commit -m "커밋 메시지"**                   | 커밋 생성 (실제 변경사항 확정)                               |
|                               | **$ git status**                                    | 파일 상태 확인                                               |
| <가지(branch)치기 작업>       | **$ git branch**                                    | 브랜치 목록                                                  |
|                               | **$ git branch <브랜치이름>**                       | 새 브랜치 생성 (local로 만듦)                                |
|                               | **$ git checkout -b <브랜치이름>**                  | 브랜치 생성 & 이동                                           |
|                               | **$ git checkout master**                           | master branch로 되돌아 옴                                    |
|                               | **$ git branch -d <브랜치이름>**                    | 브랜치 삭제                                                  |
|                               | **$ git push origin <브랜치이름>**                  | 만든 브랜치를 원격 서버에 전송                               |
|                               | **$ git push -u < remote > <브랜치이름>**           | 새 브랜치를 원격 저장소로 push                               |
|                               | **$ git pull < remote > <브랜치이름>**              | 원격에 저장된 git 프로젝트의 현재 상태를 다운받고 + 현재 위치한 브랜치로 병합 |
| <변경 사항 발행(push)>        | **$ git push origin master**                        | 변경사항 원격 서버에 업로드                                  |
|                               | **$ git push < remote > <브랜치이름>**              | 커밋을 원격 서버에 업로드                                    |
|                               | **$ git push -u < remote > <브랜치이름>**           | 커밋을 원격 서버에 업로드                                    |
|                               | **$ git remote add origin <등록된 원격 서버 주소>** | 클라우드 주소 등록 및 발행 (git에게 새로운 원격 서버 주소 알림) |
|                               | **$ git remote remove <등록된 클라우드 주소>**      | 클라우드 주소 삭제                                           |
| <갱신 및 병합(merge)>         | **$ git pull**                                      | 원격 저장소의 변경 내용이 현재 디렉토리에 가져와지고(fetch) 병합(merge)됨 |
|                               | **$ git merge <다른 브랜치이름>**                   | 현재 브랜치에 다른 브랜치의 수정사항 병합                    |
|                               | **$ git add <파일명>**                              | 각 파일을 병합할 수 있음                                     |
|                               | **$ git diff <브랜치이름><다른 브랜치이름>**        | 변경 내용 merge 전에 바뀐 내용을 비교할 수 있음              |
| <태그tag 작업>                | **$ git log**                                       | 현재 위치한 브랜치 커밋 내용 확인 및 식별자 부여됨           |
| <로컬 변경사항 return 작업>   | **$ git checkout -- <파일명>**                      | 로컬의 변경 사항을 변경 전으로 되돌림                        |
|                               | **$ git fetch origin**                              | 원격에 저장된 git프로젝트의 현 상태를 다운로드               |