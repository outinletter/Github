# 원격 저장소(Remote repository)

원격 저장소 = 인터넷이나 네트워크 어딘가에 존재하는 저장소

## 원격 저장소 확인

원격 저장소를 clone하면 `origin` 이름으로 원격 저장소가 자동으로 등록된다.

원격 저장소의 이름을 확인한다.

```
$ git remote
```

원격 저장소의 이름과 URL을 함께 확인한다.

```
$ git remote -v
```

## 원격 저장소 추가

`$ git remote add [원격 저장소 이름] [URL]` 명령으로 아래는 예시이다.

```
$ git remote add pb https://github.com/paulboone/ticgit
```

위와 같이 등록하고 실제로 로컬 저장소에는 없지만 `pb` 원격 저장소에 있는 것을 가져오려면 아래와 같이 명령한다.

```
$ git fetch pb
```

`git fetch` 명령은 원격 저장소의 데이터를 모두 로컬로 가져오지만 자동으로 Merge하지는 않는다.

## 원격 저장소에 Push하기

`git push [원격 저장소 이름] [브랜치 이름]` 명령으로 Push할 수 있다.

`origin` 원격 저장소의 `master` 브랜치에 Push한다.

```
$ git push origin master
```

원격 저장소에 현재 로컬 브랜치와 동일한 이름의 브랜치에 Push한다. 원격 저장소의 다른 브랜치에 잘못 커밋하는 실수를 줄여줄 수 있다.

```
$ git push origin HEAD
```

## 원격 저장소 이름을 바꾸거나 삭제하기

원격 저장소의 이름을 변경할 수 있다.

```
$ git remote rename pb paul
```

원격 저장소를 삭제할 수 있다.

```
$ git remote rm paul
```

## 원격 저장소 이름 규칙

전형적인 원격 저장소의 이름이다.

- `origin`: Github 내 저장소의 이름(Fork한 경우 포함)
- `upstream`: Fork한 경우 원본 프로젝트의 저장소의 이름(디폴트 이름은 아니지만 통상적인 이름)

참고로 `master`는 브랜치 이름이다.

- `master`: `git init`으로 저장소 생성 시 디폴트 브랜치 이름

# 브랜치

## 브랜치 만들기

`git branch [브랜치 이름]` 명령으로 아래와 같이 `testing` 브랜치를 만든다.

```
$ git branch testing
```

## 브랜치 변경

`git checkout` 명령어로 작업하려는 `testing` 브랜치로 이동할 수 있다.

```
$ git checkout testing
```

**브랜치를 이동(변경)하면 작업 디렉토리의 파일 내용도 변경된다.**

`git checkout -b` 명령어로 두 번 입력하지 않고 한 번에 브랜치를 만들고 바로 이동할 수도 있다.

```
$ git checkout -b testing
```

## 로컬 브랜치를 원격 저장소에 Push하기

`git push -u origin [브랜치 이름]` 명령으로 로컬 브랜치를 원격 저장소에도 반영할 수 있다.

```
$ git push -u origin testing
```

## Merge

### 이슈 처리를 위해 브랜치 적용 시나리오

어떤 이슈 처리를 위한 `issue53` 토픽 브랜치를 만든다.

```
$ git checkout -b issue53
```

소스파일을 수정한다.

```
$ vim index.html
```

수정한 파일을 로컬 저장소로 커밋한다.

```
$ git commit -am 'fixed the broken email address'
```

`master` 브랜치로 다시 이동한다.

```
$ git checkout master
```

`issue53` 브랜치의 내용을 `master` 브랜치에 반영하여 합친다.

```
$ git merge issue53
```

브랜치가 불필요해지면 삭제한다.

```
$ git branch -d issue53
```







# Github 오픈소스에 기여하기

## Fork 및 Clone

출처: [About forks](https://help.github.com/articles/about-forks/)

Fork는 원본 프로젝트의 저장소에 아무런 영향을 미치지 않고 직접 관리할 수 있는 원본 저장소의 사본이다.

Github에서 오픈소스 프로젝트의 Fork는 아래와 같은 일을 할 수 있다.

- 원본 프로젝트 저장소에서 변경사항을 Fork로 반영해 동기화할 수 있다.
- 여러분이 Fork에서 직접 변경한 사항을 원본 프로젝트에 반영해달라고 요청할 수도 있다.

Fork를 clone하기

```
$ git clone https://github.com/YOUR_USERNAME/YOUR_FORK.git
```

## Fork와 원본 프로젝트 저장소 연결 설정

출처: [Configuring a remote for a fork](https://help.github.com/articles/configuring-a-remote-for-a-fork/)

Fork와 원본 저장소를 동기화하려면 Fork와 함께 원본 저장소를 올바르게 연결 설정해야 한다.

현재 원격 저장소는 최초 `git clone` 명령으로 여러분의 Fork만 `origin` 이름으로 연결되어 있음을 확인할 수 있다.

```
$ git remote -v
origin  https://github.com/YOUR_USERNAME/YOUR_FORK.git (fetch)
origin  https://github.com/YOUR_USERNAME/YOUR_FORK.git (push)
```

원격의 원본 저장소를 `upstream`이라는 이름으로 직접 연결 설정한다.

```
$ git remote add upstream https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git
```

이제 여러분의 Fork 저장소 `origin`과 원본 프로젝트 저장소 `upstream`이 올바르게 연결 설정되어 있음을 확인할 수 있다.

```
$ git remote -v
origin    https://github.com/YOUR_USERNAME/YOUR_FORK.git (fetch)
origin    https://github.com/YOUR_USERNAME/YOUR_FORK.git (push)
upstream  https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git (fetch)
upstream  https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git (push)
```

## Fork와 원본 프로젝트 저장소와 동기화

출처: [Syncing a fork](https://help.github.com/articles/syncing-a-fork/)

`git fetch [원격 저장소 이름]` 명령어는 로컬에는 없지만 원격 저장소에는 있는 데이터를 전부 가져온다. 그러면 원격 저장소의 모든 브랜치를 로컬에서 접근할 수 있고 언제든지 Merge하거나 살펴볼 수 있다.

원본 프로젝트 저장소의 이름은 앞서 `upstream`으로 지었기 때문에 아래와 같이 명령한다.

```
$ git fetch upstream
remote: Counting objects: 75, done.
remote: Compressing objects: 100% (53/53), done.
remote: Total 62 (delta 27), reused 44 (delta 9)
Unpacking objects: 100% (62/62), done.
From https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY
 * [new branch]      master     -> upstream/master
```

여러분의 Fork 로컬 저장소의 `master` 브랜치로 이동한다.

```
$ git checkout master
Switched to branch 'master'
```

원본 프로젝트 저장소 `upstream`의 `master` 브랜치의 내용을 Fork 로컬 저장소 `master` 브랜치에 반영하도록 한다.

```
git merge upstream/master
Updating a422352..5fdff0f
Fast-forward
 README                    |    9 -------
 README.md                 |    7 ++++++
 2 files changed, 7 insertions(+), 9 deletions(-)
 delete mode 100644 README
 create mode 100644 README.md
```

**위와 같이 동기화할 경우 저장소의 로컬 사본에만 반영된다. Github의 Fork에 반영하려면 반드시 변경사항을 Push해야 한다.**

```
$ git push origin HEAD
```

`git push origin HEAD`는 현재 체크아웃한 작업 중 브랜치가 `master`이므로 `git push origin master`와 의미가 같다.

## PR 보내기

위에서 설명한 것처럼 Github 사이트에서 오픈소스 프로젝트의 Fork를 만들고 연결 설정한다.

토픽 브랜치를 알맞은 이름(예시: `issue17`)으로 만든다.

```
$ git checkout -b issue17
```

필요한 소스 코드를 수정하고 잘 고쳤는지 확인한다.

```
$ git diff
```

커밋한다.

```
$ git commit -am "Issue17 was resolved."
```

Github에서 Fork한 원격 저장소에 토픽 브랜치를 Push한다. 다음 명령어의 의미는 `git push origin issue17`과 같다.

```
$ git push origin HEAD
```

Github에서 Fork한 저장소에 가면 원본 저장소에 Pull Request를 보낼 수 있는 버튼이 제공된다.

PR이 반영되거나 브랜치가 불필요해지면 브랜치를 삭제한다.

```
$ git branch -d issue17
```

## 다른 기여자의 PR을 가져와 테스트하기

`ID`는 PR의 #번호의 소스코드를 가져와 `BRANCHNAME`의 새로운 브랜치를 만든다.

```
$ git fetch origin pull/ID/head:BRANCHNAME
```

Fork 저장소 또는 소유권이 있는 저장소 `origin`이 아닌 다른 원래 프로젝트 주인이 있는 원격 저장소 `upstream`에서도 소스를 가져올 수 있다.

```
$ git fetch upstream pull/ID/head:BRANCHNAME
```

그리고 `BRANCHNAME`으로 브랜치를 체크아웃하여 작업한다.

```
$ git checkout BRANCHNAME
```