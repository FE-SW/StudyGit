# Git 영역 
![1_zpvd5fjZAFGsVAEsvMGKxA](https://github.com/FE-SW/StudyGit/assets/54196723/dd0e18e0-8285-4166-8737-f3be9ae2ef25)

<b>Working Directory:</b><br/>
작업 디렉토리는 프로젝트의 실제 파일들이 위치하는 곳이다. 이곳에 있는 파일들은 아직 버전 관리에 포함되지 않은 상태이거나, 수정 중인 파일일 수 있다. 여기서 사용자는 파일을 생성, 수정, 삭제 등의 작업을 하며 코드를 편집한다.

<b>Staging Area:</b><br/>
스테이징 영역은 Git에서 커밋을 준비하기 위한 곳이다. "git add" 명령어를 통해 작업 디렉토리에서 변경된 파일들을 스테이징 영역에 추가함으로써, 다음 커밋에 포함될 변경 사항들을 선별적으로 정할 수 있다. 이는 마치 커밋을 위한 임시 저장 공간 같은 역할을 한다.

<b>Repository:</b><br/>
레포지토리는 프로젝트의 모든 파일, 버전 정보, 변경 이력 등을 저장하는 곳이다. 로컬 레포지토리는 개인 컴퓨터에 파일 시스템의 일부로 존재하며, 원격 레포지토리는 GitHub, GitLa 같은 서비스에 호스팅될 수 있다. "git commit" 명령어는 스테이징 영역의 변경 사항을 로컬 레포지토리에 저장한다.

# 커밋참조
Git의 핵심 요소 중 하나는 코드베이스의 변화를 "커밋" 단위로 추적하는 것이다. 커밋은 프로젝트 히스토리의 기본 구성 요소로, 파일에 대한 변경 사항의 집합, 그리고 그 변경에 대한 설명이 포함된 메시지를 담고 있다. 이렇게 각 커밋은 코드 변경의 타임스탬프와 작성자 정보를 가지며, 이전 상태로부터의 구별 가능한 스냅샷을 형성한다. 따라서 Git의 히스토리는 이러한 커밋들의 연속으로 이루어져 있으며, 개발자들은 이를 통해 프로젝트의 변화를 세밀하게 추적하고 관리할 수 있다.

<b>[FETCH_HEAD]:</b>
* FETCH_HEAD는 최근에 실행된 git fetch 명령의 결과를 가리킨다. 이것은 로컬 레포지토리에 있는 특수한 참조로, 원격 레포지토리에서 가져온 브랜치의 최신 커밋을 담고 있다. 이 참조는 원격 변경 사항을 로컬에 병합하기 전에 이를 검토하는 데 주로 사용된다.

<b>[ORIGIN/HEAD]:</b>
* ORIGIN/HEAD는 원격 저장소의 기본 브랜치(대부분의 경우 'main' 또는 'master' 브랜치)를 가리키는 참조이다. 이것은 원격 저장소에 마지막으로 푸시된 커밋을 나타내며, git fetch를 실행하면 로컬의 ORIGIN/HEAD가 업데이트된다.

<b>[HEAD]:</b>
* HEAD는 현재 작업 중인 로컬 브랜치의 최신 커밋을 가리키는 포인터이다. 브랜치를 전환하거나 새로운 커밋을 추가할 때 HEAD는 자동으로 최신 커밋을 가리키도록 이동

<b>[ORIG_HEAD]:</b>
* ORIG_HEAD는 Git에서 중요한 작업을 수행하기 전의 HEAD의 상태를 백업하기 위해 자동으로 생성되는 특별한 참조이다. 예를 들어, 리베이스나 병합과 같이 HEAD를 급격하게 변경할 수 있는 명령을 실행할 때, 현재의 HEAD가 ORIG_HEAD에 저장되므로, 만약 문제가 발생했을 때 사용자가 이전 상태로 쉽게 되돌릴 수 있게 해준다.("현재의 HEAD"라는 표현은 리베이스나 병합과 같은 명령을 실행하기 바로 전의 HEAD를 가리킨다.)
  
<b>[MERGE_HEAD]:</b>
* MERGE_HEAD는 현재 진행 중인 병합 작업에서 병합하려는 커밋(들)을 가리키는 참조이다. git merge 명령을 실행하면, 병합하려는 대상 브랜치의 최근 커밋이 MERGE_HEAD에 기록된다. 이렇게 함으로써, Git은 현재 브랜치(HEAD)와 병합할 커밋(MERGE_HEAD) 사이의 차이를 알고, 적절한 병합 작업을 수행할 수 있다.

간단하게 요약하자면, FETCH_HEAD는 최근에 가져온 변경 사항을, ORIGIN/HEAD는 원격 저장소의 기본 브랜치의 상태를, HEAD는 현재 체크아웃된 로컬 브랜치의 상태를, ORIG_HEAD는 중요한 변경 이전의 HEAD의 상태를, 그리고 MERGE_HEAD는 병합할 커밋들의 정보를 나타낸다.

#### 심볼
HEAD: 현재 체크아웃된 커밋을 나타내는 포인터
```javascript
A---B---C---D (HEAD)
```

~: 특정 조상 커밋을 참조하기 위한 구문
```javascript
A---B---C---D (HEAD~1)---E (HEAD)
```
* HEAD ~ 1: HEAD에서 한 커밋 이전을 참조 -> D커밋
* HEAD ~ 2: C커밋
* HEAD ~ 3: B커밋
* HEAD^1: HEAD의 첫 번째 부모를 참조 -> E 커밋의 첫 번째 부모인 D커밋
* HEAD^2: HEAD의 두 번째 부모를 참조하려고 시도 -> E 커밋은 병합 커밋이 아니므로 두 번째 부모가 없습니다. 따라서 에러를 반환

^: 병합 커밋의 특정 부모를 참조하기 위한 구문
```javascript
  A---B-------E (HEAD)
       \     /
        C---D
```
* HEAD ~ 1: HEAD에서 한 커밋 이전을 참조 이 경우, HEAD~1은 항상 "첫 번째 부모"를 따른다 -> B커밋
* HEAD ~ 2: A커밋
* HEAD ~ 3: A가 루트 커밋이므로, HEAD~3는 존재하지x
* HEAD^1: HEAD의 첫 번째 부모를 참조 ->. 병합 커밋인 E의 경우, 첫 번째 부모는 B커밋
* HEAD^2: D커밋
* HEAD^3: "HEAD의 세 번째 부모를 참조"하는 것을 의미 -> E 커밋은 두 부모만 가지고 있으므로, HEAD^3은 존재하지x


HEAD로부터의 상대적 위치를 나타내는데, ~는 몇 단계의 조상을 나타내는 반면, ^는 병합된 부모들 중 특정 부모를 지정함

# 명령어 모음

## git commit
git commit은 사용자가 스테이징 영역에 추가한 변경 사항들을 로컬 저장소에 기록한다. 이 명령어는 변경 사항을 확정하고, 확정한 변경 사항에 대한 메시지를 작성하여 프로젝트의 히스토리에 기록한다. 이 과정은 코드베이스에 대한 변경 이력을 생성하고 공유함으로써 다른 개발자들과 협업을 용이하게 해준다.

* -m, --message: 커밋 메시지를 명령어에 직접 포함시켜 커밋한다.
* --amend: 가장 최신 커밋을 수정한다. 이를 사용하여 커밋 메시지를 변경하거나, 스테이징된 새 파일을 이전 커밋에 추가할 수 있다.
* -a, --all: 수정된 파일들을 자동으로 스테이징 영역에 추가하고 커밋한다. 새로 생성된 파일은 포함되지 않는다.
* --allow-empty: 변경 사항이 없는 상태에서도 커밋을 허용한다. 보통 특정 상황에서만 필요한 특수한 경우에 사용된다.
* -C, --reuse-message: 이전 커밋의 메시지를 재사용하여 새 커밋을 생성한다. 사용 예: git commit -C HEAD


## git log
git log 명령어는 Git에서 커밋 히스토리를 확인할 수 있는 명령어이다. 이 명령은 사용자가 현재 브랜치의 커밋 로그를 시간 순서대로 볼 수 있게 해주며, 작성자, 날짜, 커밋 메시지로 구성된다.

* --oneline: 각 커밋을 한 줄로 간략하게 표시한다. 커밋 해시의 일부와 커밋 메시지만 보여준다.
* --graph: 브랜치와 병합 히스토리를 ASCII 그래픽으로 표시한다.
* --decorate: 커밋 로그 정보에 브랜치명이나 태그와 같은 참조를 보여준다.
* --author=<name>: 특정 작성자의 커밋만 보여준다.
* --before="YYYY-MM-DD" 또는 --after="YYYY-MM-DD": 특정 날짜 이전이나 이후의 커밋만 표시합니다.
* -p 또는 --patch: 각 커밋에서 이루어진 변경 사항을 패치 형식으로 표시한다.
* --stat: 각 커밋의 통계 정보, 예를 들어 변경된 파일, 추가된 줄, 삭제된 줄 등을 표시한다.
* --follow <file>: 특정 파일의 변경 내역을 모두 표시한다, 파일 이름 변경을 추적한다.
* -n 또는 --max-count=<number>: 최근 n개의 커밋만 표시한다.

## git reset
![images_byeol4001_post_a54ec347-b10e-4f4a-b2b6-cfb92a86c4ee_image](https://github.com/FE-SW/StudyGit/assets/54196723/534991d2-9475-4ddd-9785-53ed965d1e0e)
git reset 명령어는 현재 HEAD를 특정 상태로 되돌리는 데 사용되며, 스테이징 영역과 작업 디렉토리의 내용을 선택적으로 변경할 수 있다. 이를 통해 잘못된 커밋을 취소하거나 이전의 특정 커밋 상태로 코드베이스를 되돌릴 수 있어, 코드의 히스토리를 정리하는 데 유용하다.
git reset commitId 로 명령어를 실행한다.이는 로컬저장소 현재 브랜치에만 해당하며 다른 브랜치에는 영향을 주지 않는다.

![5131](https://github.com/FE-SW/StudyGit/assets/54196723/a00dfa10-a5ec-4421-b897-86caa10761f5)

* --soft: 지정된 커밋으로 HEAD를 이동시키지만, 스테이징 영역과 작업 디렉토리는 변경하지 않는다. 커밋되지 않은 변경 사항을 다시 커밋할 준비가 되어 스테이징 상태로 남아있는다.
* --mixed (기본 옵션): 지정된 커밋으로 HEAD를 이동시키고 스테이징 영역을 리셋하지만 작업 디렉토리의 파일은 그대로 둔다. 이를 통해 어떤 파일을 다시 스테이징할지 선택할 수 있다.
* --hard: 지정된 커밋으로 HEAD, 스테이징 영역, 그리고 작업 디렉토리를 모두 리셋한다. 이 옵션은 모든 현재의 변경 사항을 삭제하고 지정된 커밋 상태로 완전히 되돌린다.(사용할떄 조심해서 사용)
* --merge: 리셋하려는 커밋이 현재 HEAD에서 출발하는 변경 사항을 포함하는 경우에만 작업 디렉토리의 파일을 리셋한다.
* --keep: --merge와 유사하지만, 리셋하려는 커밋이 현재 HEAD에서 출발하는 변경 사항을 포함하지 않는 경우에 리셋 작업을 중단한다.

### merge,keep 차이점

```javascript
  A---B---C (HEAD)
```

#### [--merge]:
만약 여기서 git reset --merge B를 실행한다면, C에서 작업 디렉토리까지의 변경 사항(아직 커밋하지 않은 변경 사항)이 B 커밋의 내용과 충돌하지 않는 경우, HEAD는 B로 리셋되고 작업 디렉토리의 변경 사항은 그대로 유지된다.
그러나, C에서 작업 디렉토리까지의 변경 사항이 B와 충돌하는 경우, git은 변경 사항을 병합하려고 시도한다.

이 옵션은 작업 디렉토리나 인덱스에 변경 사항이 있을 때, 그 변경 사항을 보존하려고 시도하면서 HEAD를 이전 커밋으로 리셋한다. 즉, 변경 사항을 잃지 않으려고 노력한다.

* 변경 사항이 리셋하려는 커밋과 충돌하지 않으면, 그 변경 사항은 보존되고 HEAD는 지정된 커밋으로 리셋된다.
* 변경 사항이 리셋하려는 커밋과 충돌하면, Git은 해당 변경 사항을 병합하려고 시도한다.

#### [--keep]:
--keep 옵션을 사용하여 git reset --keep B를 실행하면, 현재 HEAD(C)에서 출발하는 변경 사항이 B에 존재하지 않는다면(즉, B에서 현재 작업 디렉토리까지의 변경 사항이 "안전하다"고 판단되면), HEAD는 B로 리셋되고 작업 디렉토리는 그대로 유지된다.
그러나, 만약 리셋하려는 커밋(B)이 현재 HEAD(C)에서 출발하는 변경 사항을 포함하고 있고, 충돌이 발생한다면, 리셋 작업은 중단되고 현재 상태는 그대로 유지된다. 이는 작업을 잃어버릴 위험 없이 리셋을 안전하게 수행하려는 의도에서 온다.

이 옵션은 --merge와 유사하지만, 조금 더 보수적인 접근 방식을 취한다. --keep은 리셋하려는 커밋으로부터 현재 변경 사항이 "안전하게" 분리될 수 있을 때만 리셋을 허용한다.

* 변경 사항이 리셋하려는 커밋과 충돌하지 않으면, Git은 HEAD를 지정된 커밋으로 리셋하고 변경 사항을 보존한다.
* 만약 리셋하려는 커밋이 현재의 변경 사항과 충돌하거나 그 변경 사항이 리셋하려는 커밋에 이미 포함되어 있는 경우(즉, 변경 사항이 "안전하지 않다"고 판단될 경우), Git은 리셋 작업을 중단하고 오류 메시지를 반환한다. 이렇게 하면 실수로 중요한 변경 사항을 잃어버릴 위험이 줄어든다.

"안전하다"는 용어는 이러한 컨텍스트에서, 작업 중인 변경 사항이 리셋 작업으로 인해 잃어버려지거나 오버라이트되지 않는 상황을 말한다.간단히 말해서, --merge는 변경 사항이 있는 경우 병합을 시도하고, --keep은 안전하지 않다고 판단되는 변경 사항이 있을 때 리셋을 중단한다.


### 예시
```javascript  
A---B---C (HEAD)
```
여기서 D 커밋이 현재의 HEAD이자 master 브랜치의 최신 커밋이다.

<b>1. git reset --soft B를 실행</b>
```javascript
A---B (HEAD, master)
    \
     C---D
```
여기서 커밋 C와 D는 로그에서 더 이상 보이지 않지만, 변경 사항은 스테이지된 상태(인덱스에)로 남아 있다.

<b>2.git reset --mixed B 또는 옵션 없이 git reset B를 실행</b>
```javascript
A---B (HEAD, master)
    \
     C---D
```
이 경우에도 커밋 C와 D는 로그에서 더 이상 보이지 않지만, 변경 사항은 스테이지되지 않은 상태로 작업 디렉토리에 남아 있다.

<b>3.git reset --hard B를 실행</b>
```javascript
A---B (HEAD, master)
```
이 경우, 커밋 C와 D는 완전히 사라지고, 관련 변경 사항도 작업 디렉토리에서 삭제된다. C와 D의 트랙은 로그에서 완전히 사라지며, 이를 복구하려면 복잡한 데이터 복구 절차를 거쳐야 한다.
따라서 git reset --hard 조합은 최대한 신중하게 사용하여야 된다.


## git revert
![images-byeol4001-post-1f72d7f0-3ce8-4866-9a4d-26934660b26a-image](https://github.com/FE-SW/StudyGit/assets/54196723/07ee48f8-1d93-4be7-8a98-399f8134d350)
git revert는 특정 커밋의 변경사항을 되돌리는 새로운 커밋을 생성한다. 이 과정은 안전하게 이전 변경사항을 "취소"하고, 그 히스토리를 유지하는 데 사용됩니다. git revert는 실수로 잘못된 코드를 커밋했거나, 나중에 코드 변경이 문제를 일으켰을 때 이를 깔끔하게 되돌리고 싶을 때 유용하다.

예를 들어, 아래와 같은 커밋 히스토리가 있다고 가정해보면,

```javascript
A---B---C---D (HEAD, master)
```
여기서 C 커밋이 문제가 있다고 판단되어 되돌리고 싶다고 가정해보면. 이 경우, git revert C를 실행한다. 그러면 Git은 C에서 이루어진 변경사항을 "되돌리는" 새로운 커밋 E를 만들어 낸다. 그 결과 커밋 히스토리는 다음과 같이 바뀐다:

```javascript
A---B---C---D---E (HEAD, master)
```
여기서 E 커밋은 C의 변경사항을 되돌린 상태이다. 이 방식의 장점은 C의 변경 사항이 기록에서 사라지는 것이 아니라, 변경 사항을 되돌린 새로운 커밋 E가 추가된다는 것이다. 이는 코드베이스의 히스토리가 보존되며, 언제든지 C 커밋으로 돌아갈 수 있다는 것을 의미한다.

### reset,revert 차이점
git reset과 git revert는 모두 변경사항을 되돌리는 데 사용되지만, 사용 방식과 결과에 몇 가지 중요한 차이점이 있다.

| 구분         | git reset                                                  | git revert                                                     |
|--------------|------------------------------------------------------------|----------------------------------------------------------------|
| 용도         | 지정한 커밋으로 현재 HEAD를 이동한다.                    | 이전 커밋의 변경을 취소하는 새 커밋을 생성한다.                |
| 히스토리     | 커밋 이력을 재작성하며, 리셋한 커밋 이후의 히스토리를 삭제한다. | 기존 히스토리를 유지하며, '되돌림' 커밋이 추가된다.            |
| 안전성       | 비파괴적인 명령이 아니므로, 사용에 주의가 필요하다. 특히 공개된 공용 브랜치에서는 사용을 피해야 한다. | 비파괴적인 명령으로, 공개된 공용 브랜치에서도 안전하게 사용할 수 있다. |
| 사용 시나리오 | 주로 로컬 브랜치에서 실수한 커밋을 되돌리거나, 커밋 이력을 정리할 때 사용된다. | 공개된 공용 브랜치에서 이전 변경사항을 안전하게 되돌릴 때 사용된다.     |

* git reset은 주로 로컬 변경 사항을 되돌릴 때 사용되며, 커밋 히스토리를 변경하게 된다. 잘못 사용된 경우, 이전 커밋으로 돌아가기 어렵거나 불가능할 수 있다.
* git revert는 공용 브랜치에서 안전하게 사용될 수 있으며, 히스토리를 변경하지 않고 새로운 '되돌림' 커밋을 생성한다. 이러한 이유로, 되돌리고 싶은 변경 사항이 공개된 저장소에 있을 때는 git revert를 사용하는 것이 좋다.

## git branch
git branch 명령어는 브랜치와 관련된 다양한 작업을 수행하는 데 사용된다. 이 명령어를 사용하면 새 브랜치를 생성하거나 삭제하고, 현재 프로젝트에서 사용 중인 브랜치 목록을 볼 수 있으며, 다양한 추가 작업을 수행할 수 있다.

* -a, --all: 로컬 및 원격 브랜치를 모두 나열한다.
* -d, --delete: 지정된 브랜치를 삭제한다. 브랜치가 현재 체크아웃된 상태가 아니거나, 이미 병합된 경우에만 삭제가 가능하다.
* -D: 강제로 브랜치를 삭제한다. 병합되지 않은 변경사항이 있더라도 지정된 브랜치를 삭제한다.
* -m, --move: 브랜치의 이름을 변경한다.
* -M: 브랜치의 이름을 강제로 변경한다. 기존의 브랜치 이름이 있더라도 강제로 덮어쓴다.
* -r, --remotes: 원격 브랜치만 나열한다.
* --contains <commit>: 지정된 커밋을 포함하는 브랜치를 나열한다.
* --merged: 현재 브랜치에 이미 병합된 브랜치를 나열한다.
* --no-merged: 현재 브랜치에 아직 병합되지 않은 브랜치를 나열한다.
* -v, --verbose: 각 브랜치의 마지막 커밋도 함께 나열한다.
* -q, --quiet: 진행 상황 또는 다른 정보 출력을 최소화한다.
* -f, --force: 브랜치 생성 시 기존 브랜치를 덮어쓴다.
* -u, --set-upstream-to <upstream>: 지정된 브랜치에 대한 업스트림(원격 추적) 브랜치를 설정한다.

## git switch
git checkout 명령어는 다른 브랜치로 전환하거나 작업 디렉토리에서 특정 파일이나 커밋을 체크아웃하는 데 사용된다. 이를 통해 과거의 특정 커밋으로 돌아갈 수 있고, 다른 브랜치로 컨텍스트를 전환할 수 있으며, 작업 트리에서 변경된 파일을 원래 상태로 되돌릴 수 있다

* -b: 새 브랜치를 생성하고 그 브랜치로 체크아웃한다. 사용 예: git checkout -b [new-branch-name]
* -B: 브랜치가 이미 존재하는 경우에 그 브랜치를 리셋하거나, 존재하지 않는 경우에 새 브랜치를 생성한다. 사용 예: git checkout -B [branch-name] [start-point]
* -t, --track: 새로운 브랜치를 생성하고 원격 추적 브랜치로 설정한다. 사용 예: git checkout --track [remote]/[branch]
* -l: 새로 생성된 브랜치와 연결된 참조 로그(reflog)를 만든다. 사용 예: git checkout -l [new-branch-name]
* -f, --force: 변경 사항을 강제로 체크아웃하고, 현재 변경 사항을 무시한다. 사용 예: git checkout -f
* -m, --merge: 작업 중인 변경 사항을 병합하면서 다른 브랜치로 체크아웃한다.(체크아웃 하는 브런치에 병합) 사용 예: git checkout -m [branch-name]
* -q, --quiet: 체크아웃 중에 진행 상황이나 메시지를 출력하지 않게 설정
* --detach: 지정된 커밋을 'DETACHED HEAD' 상태로 체크아웃한다, 즉 어떤 브랜치에도 속하지 않는 상태로 커밋을 체크아웃한다. 사용 예: git checkout --detach [commit]
* --orphan: 새로운 고아 브랜치를 생성한다. 이 브랜치는 현재 커밋과 연결되지 않는다. 사용 예: git checkout --orphan [new-branch]

#### 참고
Git 2.23 이상 버전에서는, git checkout의 기능이 두 개의 분리된 명령어로 분리되었다.(git switch와 git restore) git switch는 브랜치 전환에 사용되고, git restore는 파일을 특정 커밋이나 상태로 되돌리는 데 사용된다. 이 변경은 git checkout의 사용 사례가 너무 다양하여 명령어의 목적이 모호해지는 것을 방지하기 위한 것이다.
