# Git 영역 
<p float="left" align="center">
  <img src="https://github.com/FE-SW/StudyGit/assets/54196723/dd0e18e0-8285-4166-8737-f3be9ae2ef25" width="45%" align="middle" />
  <img src="https://github.com/FE-SW/StudyGit/assets/54196723/fdf72f55-7ca0-4a7c-b317-62441c385168" width="45%" align="middle" /> 
</p>

<b>Working Directory:</b><br/>
작업 디렉토리는 프로젝트의 실제 파일들이 위치하는 곳이다. 이곳에 있는 파일들은 아직 버전 관리에 포함되지 않은 상태이거나, 수정 중인 파일일 수 있다. 여기서 사용자는 파일을 생성, 수정, 삭제 등의 작업을 하며 코드를 편집한다.

<b>Staging Area:</b><br/>
스테이징 영역은 Git에서 커밋을 준비하기 위한 곳이다. "git add" 명령어를 통해 작업 디렉토리에서 변경된 파일들을 스테이징 영역에 추가함으로써, 다음 커밋에 포함될 변경 사항들을 선별적으로 정할 수 있다. 이는 마치 커밋을 위한 임시 저장 공간 같은 역할을 한다.

<b>Repository:</b><br/>
레포지토리는 프로젝트의 모든 파일, 버전 정보, 변경 이력 등을 저장하는 곳이다. 로컬 레포지토리는 개인 컴퓨터에 파일 시스템의 일부로 존재하며, 원격 레포지토리는 GitHub, GitLa 같은 서비스에 호스팅될 수 있다. "git commit" 명령어는 스테이징 영역의 변경 사항을 로컬 레포지토리에 저장한다.

# Git 파일상태
![R1280x0](https://github.com/FE-SW/StudyGit/assets/54196723/0dfdda37-6734-4fde-8e89-33d631d2a6e1)
git의 4가지 상태는 Git의 핵심 사이클을 이루며, 파일이 시간이 지나며 이 상태들 사이를 이동한다. 개발자는 git status 명령을 사용하여 이러한 상태를 확인할 수 있다. 이를 통해 어떤 파일이 커밋되었는지, 어떤 파일이 수정되었지만 아직 커밋되지 않았는지, 그리고 어떤 파일이 Git에 의해 전혀 관리되지 않고 있는지를 알 수 있다.

<b>Untracked (추적되지 않음):</b>
이 상태의 파일은 Git 디렉토리에 존재하지만, Git의 버전 관리 밑에 두지 않은 파일들이다. 이는 새로운 파일이 생성되었지만 아직 한 번도 git add 명령을 통해 스테이징 영역에 추가되지 않았기 때문일 수 있다.
이 파일들은 로컬로만 존재하며, Git은 이 파일들의 존재를 알지만 아직 버전 관리를 하지 않는다.

<b>Unmodified (수정되지 않음):</b>
이 상태의 파일은 이전에 이미 Git에 커밋된 적이 있는 파일들로, 마지막 커밋 이후로 아무런 변경이 없는 파일들을 말한다.
즉, 파일이 변경되지 않았으므로 Git에 다시 커밋할 필요가 없다.

<b>Modified (수정됨):</b>
이 상태의 파일은 마지막 커밋 이후에 변경이 발생했지만, 아직 로컬 데이터베이스에 커밋되기 위한 스테이징 영역에 추가되지 않은 파일들을 말한다.
git add 명령을 사용하여 이 변경을 스테이징 영역에 추가하기 전까지는 Git은 이 변경 사항을 추적하지 않는다.

<b>Staged (스테이징됨):</b>
이 상태의 파일은 현재 수정되고 스테이징 영역에 추가되어, 다음 커밋에 포함될 준비가 된 파일들을 말한다.
git commit 명령을 사용하면, 스테이징 영역의 이 변경사항이 로컬 데이터베이스에 저장된다.

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

## git status
git status 명령어는 Git 저장소에서 파일 상태를 확인하는 데 사용된다. 이 명령어는 현재 체크아웃된 브랜치, 스테이지된(커밋 대기 상태의) 변경 사항, 스테이지되지 않은 변경 사항, 머지 충돌 등의 정보를 제공한다. 이를 통해 사용자는 다음 커밋에 어떤 파일이 포함될지, 어떤 파일이 변경되었지만 아직 스테이지되지 않았는지 등을 파악할 수 있다.

* -s 또는 --short: 상태 출력을 간략하게 표시한다. 파일의 상태는 한 줄로 표시되며, 변경된 파일, 새로운 파일, 삭제된 파일 등이 각각 다른 식별자로 나타낸다.
* --branch: 현재 브랜치와 추적 중인 브랜치 사이의 차이를 보여준다. 기본 출력에 브랜치 정보가 추가된다.
* --show-stash: stash에 저장된 항목의 수를 보여준다.
* --ignored: 무시된 파일을 보여준다. 기본적으로 git status는 .gitignore 파일에 명시된 무시된 파일들을 표시하지 않는다.

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
![git-V](https://github.com/FE-SW/StudyGit/assets/54196723/ac4ff3ef-12f2-45c3-8bca-a45bf68aa15c)
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

## git checkout
![C4BCo](https://github.com/FE-SW/StudyGit/assets/54196723/d959758f-252a-41c7-b8d9-fc78a41c455b)
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

## git switch
![checkout-branch](https://github.com/FE-SW/StudyGit/assets/54196723/cb7177ea-ad57-4c18-a5e1-8f83c423f3de)
git switch는 작업 중인 브랜치를 변경하는데 사용된다. 이전에는 git checkout 명령어가 파일의 체크아웃 및 브랜치 전환에 모두 사용되었지만, git switch는 브랜치 전환에 특화된 명령어로 이 두 기능을 명확히 구분한다.

* -c, --create: 새 브랜치를 생성하고 그 브랜치로 전환합니다. 사용 예: git switch -c new-feature
* -d, --detach: 브랜치를 '분리된 HEAD' 상태로 전환합니다. 이 상태에서의 커밋은 어떤 브랜치에도 속하지 않는다. 사용 예: git switch --detach
* -f, --force: 변경 사항을 강제로 덮어쓰기하여 브랜치를 전환한다.(변경 사항이 커밋되지 않았을 때 브랜치를 전환하려고 하면 Git은 충돌을 방지하기 위해 전환을 거부한다. 하지만 -f 옵션을 사용하면, Git은 경고 없이 현재의 변경 사항을 잃어버릴 위험을 감수하고 브랜치를 전환한다.기존 이전 브랜치 변경 사항은 유지되지 않으며 master 브랜치의 내용으로 로컬 작업 디렉토리가 업데이트된다.) 사용 예: git switch -f master
* --guess: 주어진 문자열로 시작하는 브랜치 이름을 추측하여 전환한다. 사용 예: git switch --guess fea (가능한 경우 'feature' 브랜치로 전환)
* -m, --merge: 전환할 브랜치와 현재 브랜치의 변경 사항을 병합한다. 사용 예: git switch -m master
* -q, --quiet: 전환하는 동안 진행 상황 또는 메시지를 출력하지 않는다. 사용 예: git switch -q feature-branch
* -t, --track: 원격 브랜치를 추적하는 새 브랜치를 생성하고 전환한다. 사용 예: git switch -t origin/feature-branch

## git restore
git restore는 작업 디렉토리의 파일이나 인덱스를 특정 상태로 복원하는데 사용된다. 이 명령은 주로 아직 커밋되지 않은 로컬 변경 사항을 되돌리는 데 유용하다. git restore는 git checkout의 특정 사용 사례를 대체하기 위해 만들어졌으며, 사용자가 브랜치 전환과 파일 복원 작업을 더 명확하게 구분할 수 있게 해준다.이 명령어는 아직 커밋되지 않은 변경 사항을 안전하게 되돌릴 수 있는 유연성을 제공하며, 특정 파일 또는 디렉토리만 선택적으로 복원하는 것이 가능하다. 하지만, 이미 커밋된 이력을 변경하거나 삭제하는 데에는 사용되지 않는다.

* -s, --source: 복원할 소스를 지정한다.(기본값은 HEAD)(어떤 커밋(또는 다른 소스)에서 파일 상태를 복원할 것인지를 지정) 사용 예: git restore -s HEAD ~ 1 file.txt 명령은 HEAD ~ 1 (즉, 현재 브랜치에서 한 커밋 이전)의 file.txt 파일 상태를 작업 디렉토리로 복원합니다. 이는 마지막으로 수행한 커밋 이후에 발생한 file.txt에 대한 변경사항을 되돌리고, 그 파일을 마지막으로 커밋된 상태로 되돌리는 것을 의미 이러한 방식으로,특정 파일을 이전 커밋의 상태로 되돌릴 수 있다, 그러나 다른 파일들은 그대로 두며 파일 단위로 작업을 되돌리는 데 매우 유용하다.
* -W, --worktree: 작업 디렉토리에서 수행된 변경사항이 초기화되고, 해당 파일이 마지막으로 커밋된 상태(또는 지정된 소스)로 되돌아간다. 이것은 마치 변경을 아예 하지 않은 것처럼 파일을 되돌린다 사용 예: git restore -W file.txt 
* --staged: 스테이징 영역에 있는 변경사항을 복원한다. 파일을 스테이지 했던 변경사항이 되돌려지고 스테이징 영역이 이전 커밋 상태(또는 지정된 소스)로 복원된다. 하지만 작업 디렉토리의 파일은 그대로 유지된다. 사용 예: git restore --staged file.txt
* --ignore-unmerged: 병합 중인 파일(즉, 현재 병합 중이거나 병합 충돌이 발생한 파일)을 무시하고 다른 파일들에 대해서만 복원 작업을 수행한다. 병합 중에 충돌이 발생했을 때, 이 옵션을 사용하면 아직 해결되지 않은 충돌이 있는 파일을 제외하고 나머지 파일들을 지정한 상태(예를 들어, 특정 커밋 또는 HEAD)로 되돌릴 수 있다. 이는 병합 충돌 해결 중에 다른 변경 사항을 롤백하고 싶을 때 유용할 수 있다. 사용 예: git restore --ignore-unmerged
* -p, --patch:  git의 "패치 모드"를 사용하여 파일의 변경 사항을 부분적으로 되돌릴 수 있게 해준다. 이 모드는 사용자에게 각 변경된 부분에 대해 개별적으로 검토하고, 그 중 어떤 것을 되돌릴지 선택할 수 있는 기능을 제공한다. 이는 파일 전체를 되돌리는 것이 아니라, 파일 내에서 특정 변경된 섹션만을 선택적으로 되돌리고 싶을 때 유용하다. 명령어를 실행하면, 콘솔에 변경 사항이 표시되며, 사용자는 각 변경 사항을 개별적으로 되돌릴지 여부를 결정할 수 있다. 사용 예: git restore -p file.txt


## checkout,switch,restore 차이점 
| 기능/명령어     | git checkout                     | git switch                         | git restore                      |
|-----------------|----------------------------------|------------------------------------|----------------------------------|
| 소개            | 브랜치 변경 및 파일 체크아웃     | 브랜치를 변경 (v2.23.0부터 도입)   | 작업 디렉토리의 파일 복원 (v2.23.0부터 도입) |
| 브랜치 전환     | 가능                             | 가능 (이 기능에 특화)              | 불가능                           |
| 파일 복원       | 가능 (스테이지와 작업 디렉토리)  | 불가능                             | 가능 (이 기능에 특화)            |
| 사용하기        | 초기 사용자도 쉽게 접근 가능    | 명확한 명령으로 혼동 줄임          | 파일 상태를 명확하게 복원        |
| 안전성          | 잘못된 사용으로 데이터 손실 가능 | 안전한 브랜치 전환 제공            | 작업 내용을 안전하게 복원        |

* git checkout: 이전 버전의 Git에서는 브랜치를 전환하거나 파일을 체크아웃하는 데 사용되었다. 하지만, 사용자들 사이에서 명령어의 용도가 혼동되는 경우가 많았다.
* git switch: 브랜치를 전환하는 기능에 특화되어 있다. 브랜치를 전환하는 것이 더 명확하고 직관적이어서 사용자가 혼동할 일이 적다.
* git restore: 작업 디렉토리의 파일을 복원하는 데 사용된다. 이 명령은 특히 파일의 변경 사항을 되돌리는 데 중점을 둔다.

이 세 명령어 간의 주요 차이점은 사용 목적과 안전성에 있다. git switch와 git restore는 사용자가 실수로 데이터를 잃어버릴 위험을 줄이기 위해 도입된 명령어이다.



## git stash
![git-stash-untracked](https://github.com/FE-SW/StudyGit/assets/54196723/46d933dc-567d-44b5-97f5-c82e99caf163)
git stash는 수정한 파일들을 임시로 저장하고, 작업 디렉토리를 깨끗한 상태(마지막 커밋 시의 상태)로 되돌려놓는데 사용된다. 이는 현재 브랜치를 변경해야 하지만, 아직 커밋하지 않은 작업을 잠시 보관하고 싶을 때 유용하다. 나중에 사용자는 git stash pop 또는 git stash apply를 사용하여 이전의 변경 사항을 다시 적용할 수 있다

* git stash save "message": 현재 변경 사항을 스태시에 저장하고 선택적으로 메시지를 추가한다.
* git stash list: 모든 스태시된 변경 사항의 목록을 표시한다.
* git stash show: 마지막으로 스태시된 변경 사항을 표시한다.
* git stash pop: 가장 최근의 스태시를 적용하고 스태시 목록에서 제거한다.
* git stash apply: 가장 최근의 스태시를 적용하지만 스태시 목록에서 제거하지 않는다.
* git stash drop: 가장 최근의 스태시를 스태시 목록에서 제거한다.
* git stash clear: 모든 스태시된 변경 사항을 제거한다.
* git stash branch <branchname>: 새 브랜치를 생성하고 스태시의 변경 사항을 그 브랜치에 적용한다.
* git stash push: 새로운 스태시 항목을 만든다. 선택적으로 파일을 지정하여 특정 파일만 스태시할 수 있다.
* git stash create: 스태시 객체를 만들지만 스태시 스택에 넣지 않는다.
* git stash -u 또는 git stash --include-untracked: 추적되지 않는 파일(새 파일)을 포함하여 스태시한다.
* git stash -a 또는 git stash --all: 추적되지 않는 파일과 무시된 파일까지 모두 스태시한다.

#### [참고]
git stash는 변경 사항을 스택에 저장한다. 이 스택은 전역적으로 사용되므로 브랜치에 구속되지 않는다.

1.git stash를 사용하여 "A" 브랜치의 변경 사항을 스태시한다.<br/>
2.git checkout B를 사용하여 "B" 브랜치로 이동한다.<br/>
3.git stash pop을 사용하여 스태시된 변경 사항을 적용한다.<br/>

이 경우, "A" 브랜치에서 스태시한 변경 사항은 "B" 브랜치에 적용된다. git stash pop은 스태시 스택의 최상단에 있는 변경 사항을 가져와 현재 체크아웃된 브랜치에 적용한 후, 그 스태시를 스택에서 제거한다.
단, 이 과정에서 변경 사항이 현재 "B" 브랜치의 파일과 충돌할 수도 있으므로, 그런 경우에는 수동으로 충돌을 해결해야 한다.

#### [로컬에서 작업 중인 변경 사항이 있지만, 원격 저장소의 최신 변경 사항을 통합하고 싶을 때]
![Gitstash](https://github.com/FE-SW/StudyGit/assets/54196723/e38e5a2e-a189-4f94-a305-54eb0a7cea77)
이 절차는 원활한 통합을 위해 로컬 변경 사항을 임시로 제쳐두고 원격의 변경 사항을 로컬에 통합한 후, 로컬 변경 사항을 다시 적용하려는 경우에 유용하다. 이는 또한 여러 사람이 동일한 코드 베이스에 작업할 때 병합 충돌을 방지하거나 최소화하는 데 도움이 된다.

* 1.git stash: 현재 작업 중인 변경 사항을 임시로 저장하고 작업 디렉토리를 깨끗한 상태로 만든다. 이를 통해 pull 또는 rebase가 충돌 없이 이루어질 수 있게 해준다.
* 2.git pull --rebase: 원격 저장소의 최신 변경 사항을 로컬 저장소로 가져온 후, 로컬에서 생성된 커밋들을 최신 원격 변경 사항 위로 재배치한다. 이 방법은 커밋 이력을 깔끔하게 유지할 수 있도록 도와줍니다, 왜냐하면 불필요한 "merge commit"이 생기지 않기 때문이다.
* 3.git stash pop: 이전에 스태시에 저장했던 변경 사항을 다시 적용한다. 이 단계에서 변경 사항과 새로 통합된 커밋 사이의 충돌이 발생할 수 있으므로, 충돌 해결이 필요할 수 있다.

## git diff
![gitdiffmarklodato](https://github.com/FE-SW/StudyGit/assets/54196723/f0419528-6a2a-4e6f-bf80-f6702fee5559)
git diff 명령어는 커밋, 브랜치, 파일 등 간의 차이점을 보여준다. 이를 통해 아직 스테이지되지 않은 변경 사항, 스테이지된 변경 사항, 두 커밋 간의 차이점 등을 확인할 수 있다. 이는 코드 리뷰 시 코드 변경 사항을 확인하거나, 버그를 추적할 때 수정된 부분을 찾는 데 유용하다.

* --staged (또는 --cached): 스테이징 영역에 있는 파일과 마지막 커밋 사이의 차이를 보여준다. 사용 예: git diff --staged
* --name-only: 변경된 파일의 목록만을 출력한다. 사용 예: git diff --name-only
* --stat: 변경된 파일, 추가된 줄, 삭제된 줄의 통계를 제공한다. 사용 예: git diff --stat
* -b 또는 --ignore-space-change: 공백의 추가 또는 제거를 무시하고 차이점을 보여준다. 사용 예: git diff -b
* -w 또는 --ignore-all-space: 모든 공백 변경을 무시하고 차이점을 보여준다. 사용 예: git diff -w
* --color: 차이점을 색상으로 표시하여 가독성을 높인다. 이 옵션은 기본적으로 활성화되어 있다. 사용 예: git diff --color
* HEAD: 마지막 커밋과 작업 디렉토리 사이의 차이점을 보여준다. 사용 예: git diff HEAD
* [첫번째 브랜치 또는 커밋] [두번째 브랜치 또는 커밋]: 두 개의 브랜치나 커밋 사이의 차이점을 보여준다. 사용 예: git diff master feature-branch

## git remote
![R1280x0-2](https://github.com/FE-SW/StudyGit/assets/54196723/0b01427e-701d-423b-b88e-b842f0ebce4f)
git remote 명령어는 원격 저장소를 관리하기 위한 명령어이다. 이를 통해 사용자는 원격 저장소를 추가, 조회, 수정, 삭제할 수 있으며, 원격 저장소의 URL을 확인하거나 변경할 수도 있다.

* add [name] [url]: 새로운 원격 저장소를 추가한다. 사용 예: git remote add origin url
* rename [old-name] [new-name]: 원격 저장소의 이름을 변경한다. 사용 예: git remote rename origin new-origin
* remove [name]: 원격 저장소를 삭제한다. 사용 예: git remote remove origin
* set-url [name] [newurl]: 원격 저장소의 URL을 변경한다. 사용 예: git remote set-url origin url
* get-url [name]: 원격 저장소의 URL을 가져온다. 사용 예: git remote get-url origin
* show [name]: 특정 원격 저장소의 세부 정보를 보여준다. 사용 예: git remote show origin
* prune [name]: 로컬에는 있지만 원격에는 더 이상 존재하지 않는 참조(브랜치)를 정리한다. 사용 예: git remote prune origin

## git config
git config 명령어는 Git의 설정 변수를 조회하거나 설정할 수 있게 해주는 명령어이다. 이 설정들은 시스템 전체, 특정 사용자, 또는 특정 프로젝트에 적용될 수 있다. 이러한 구성은 Git 작업의 많은 측면을 제어하는 데 사용된다, 예를 들면 사용자의 이메일, 사용자 이름, 사용하는 에디터, 사용하는 diff 알고리즘 등을 설정할 수 있다.

* --local: 설정이 해당 저장소에만 적용된다(기본). .git/config 파일에 저장된다. 사용 예: git config --local user.name "Your Name"
* --global: 설정이 시스템의 현재 사용자에게 적용된다. ~/.gitconfig 또는 ~/.config/git/config 파일에 저장돈다. 사용 예: git config --global user.email "email_address", git config --global alias.st 'status'(git status 명령어를 git st로 줄이고 싶다면), git config --global --unset alias.별칭명(별칭제거), git config --global pull.rebase true
* --system: 설정이 시스템의 모든 사용자에게 적용된다. /etc/gitconfig 파일에 저장된다. 사용 예: git config --system core.editor "vim"
* --list (또는 -l): 저장된 모든 설정과 값을 리스트 형태로 보여준다. 사용 예: git config --list
* --unset: 특정 설정 값을 제거한다. 사용 예: git config --unset user.email
* --get: 특정 설정 값의 현재 값을 조회한다. 사용 예: git config --get user.name
* --add: 기존 값에 새로운 값을 추가한다. 사용 예: git config --add user.name "Another Name"
* --replace-all: 특정 설정의 모든 값을 주어진 값으로 바꾼다. 사용 예: git config --replace-all user.email "email_address"
* --edit: 시스템의 기본 에디터를 사용하여 설정 파일을 직접 연다. 사용 예: git config --edit

## git clone
git clone은 원격 저장소의 복사본을 로컬 시스템에 만드는 데 사용되는 명령어이다. 이것은 실질적으로 저장소의 모든 데이터(브랜치, 태그, 커밋 이력 등)를 포함하여 원격 저장소를 로컬로 "복제"한다. 이렇게 하면 로컬 환경에서 코드를 검토, 수정, 테스트 할 수 있으며 필요한 경우 변경 사항을 원격 저장소에 다시 푸시할 수 있다.

* -l, --local: 동일한 시스템에 있는 원격 저장소를 복제할 때 파일을 복사하는 대신 하드 링크를 사용한다. 사용 예: git clone --local /path/to/local/repo
* -s, --shared: 원격 저장소와 같은 객체를 로컬 저장소에서 공유한다, 최적화된 복제를 위한 것. 사용 예: git clone --shared /path/to/local/repo
* -q, --quiet: 작업 중인 진행 상황이나 정보를 출력하지 않는다, 조용한(clone) 모드이다. 사용 예: git clone --quiet url
* -v, --verbose: 자세한 정보를 출력하면서 복제를 진행한다. 사용 예: git clone --verbose url
* --progress: 진행 상황을 출력합니다(기본적으로 터미널에서는 활성화 되어 있음). 사용 예: git clone --progress url
* -n, --no-checkout: 복제 후에 "HEAD"를 체크아웃하지 않는다. 사용 예: git clone --no-checkout url
* --bare: 작업 디렉토리 없이 'bare' 저장소를 만든다. (즉, .git 폴더만 있음) 사용 예: git clone --bare url
* --mirror: 원격 저장소를 미러링한다, 'bare' 저장소를 생성하지만 모든 참조(refs)도 복사한다. 사용 예: git clone --mirror url
* -b, --branch: 지정된 브랜치만 로컬로 복제한다.(기본값은 원격 저장소의 기본 브랜치) 단, 저장소의 나머지 내용(커밋, 히스토리 등)은 다운로드된다 사용 예: git clone --branch develop url
* --single-branch: 하나의 브랜치만 복제한다. 지정된 브랜치의 커밋 히스토리만 가져오는 "얕은" 복제를 수행하게 되어, 다운로드 크기를 줄이는 데 도움이 될 수 있다. 사용 예: git clone --single-branch --branch develop url
* --depth: 지정된 커밋만큼의 최근 이력을 가진 얕은 복제(shallow clone)를 수행한다. 사용 예: git clone --depth 1 url
* --recurse-submodules: 저장소의 서브모듈도 함께 복제한다. 사용 예: git clone --recurse-submodules url

## git push 
git push 명령어는 로컬 저장소의 커밋을 원격 저장소에 업로드한다. 이를 통해 다른 개발자들과 협업하거나 코드를 원격 저장소에 백업할 수 있다.
```javascript
git push <원격 저장소 이름> <원격 브랜치로 푸시할 로컬 브랜치>
```
여기서 <원격 저장소 이름>은 대개 "origin"이다. "origin"은 클론(clone)을 통해 처음 저장소를 복사해올 때 Git이 자동으로 생성하는 기본 원격 저장소의 별칭이다. <원격 브랜치로 푸시할 로컬 브랜치>는 푸시하려는 로컬 브랜치의 이름이다.
(참고로 별칭 변경은 git remote rename origin new-origin)

* -u, --set-upstream: 푸시할 때 지정한 브랜치를 기본적인 상류(upstream) 브랜치로 설정한다. 추후 해당 브랜치로 푸시하거나 풀을 할 때 브랜치를 명시하지 않아도 된다. 사용 예: git push -u origin new-branch
* --force: 변경 사항을 원격 브랜치로 강제로 푸시한다, 이 옵션은 원격 브랜치의 히스토리를 덮어쓰기 때문에 주의해서 사용해야 한다. 사용 예: git push origin branch-name --force 또는 git push origin +branch-name
* --tags: 모든 태그를 함께 푸시한다. 사용 예: git push origin --tags(--tags 옵션은 저장소의 모든 태그를 원격으로 푸시) 또는 git push origin v1.0("v1.0"이라는 이름의 태그를 원격 저장소로 푸시)
* --dry-run: 실제로 푸시하지 않고, 푸시될 변경 사항을 체크한다. 사용 예: git push --dry-run origin feature
* --delete: 원격에 없는 로컬 변경 사항 삭제한다. 사용 예: git push origin --delete branch-name
* --all: 로컬 저장소의 모든 브랜치를 원격 저장소로 푸시한다 사용 예: git push origin --all

## git pull 
git pull은 Git 명령어 중 하나로, 원격 저장소의 변경 사항을 로컬 저장소로 가져와 현재 브랜치에 병합한다. 기본적으로, git pull은 git fetch를 실행한 후 git merge를 사용하여 원격 저장소의 변경 사항을 현재 브랜치로 병합한다.

* --rebase: 이 옵션은 원격 변경 사항을 병합하는 대신 현재 브랜치의 변경 사항을 원격 브랜치 위로 재배치한다. 사용 예: git pull --rebase origin master
* --no-rebase: 기본적으로 설정되거나 구성된 재배치 대신 병합을 수행한다.(pull이 rebase가 기본설정인 경우 사용) 사용 예: git pull --no-rebase origin master
* -q, --quiet: 진행 상황을 제외하고 메시지를 최소화한다. 사용 예: git pull -q origin master
* --force: 서버의 업데이트 내역과 로컬의 업데이트 내역이 서로 상충하더라도 강제로 페치를 수행한다. 사용 예: git pull --force origin master
* -X, --strategy-option=<option>: 병합 전략 옵션을 지정한다. 예를 들어, 충돌 해결 시 우선 순위를 정할 수 있다. 사용 예: git pull -X theirs origin master
* --depth=<depth>: 불필요한 이력 정보 없이 최근 커밋만 가져올 수 있도록 히스토리의 깊이를 제한한다. 사용 예: git pull --depth=1 origin master

### 기본설정,--rebase,--no-rebase 차이점

| 구분           | 아무 설정도 안 함                                         | `--rebase`                                             | `--no-rebase`                                       |
|----------------|-----------------------------------------------------------|-------------------------------------------------------|-----------------------------------------------------|
| 동작           | 사용자의 Git 설정에 따라 다름 (기본적으로는 'fetch' 후 'merge') | 무조건 'fetch' 후 'rebase'                             | 무조건 'fetch' 후 'merge'                           |
| 설명           | 전역 또는 저장소별 Git 설정에 따라 `git pull`이 'merge' 또는 'rebase'를 수행함(기본적으로는 'merge'가 수행) | `git pull`이 변경 사항을 'fetch' 한 다음 현재 브랜치에서 변경 사항을 'rebase'한다. 이는 현재 브랜치의 커밋들을 베이스 브랜치 위로 옮기고, 그 위에 새로 'fetch'한 커밋들을 적용 | `git pull`이 변경 사항을 'fetch' 한 다음 현재 브랜치에 'merge'를 수행한다. 이는 두 브랜치의 히스토리를 유지하면서 브랜치를 합친다. |
| 사용 시나리오 | 사용자가 별도의 pull 동작을 설정하지 않았거나, 기본 설정을 사용하고자 할 때 | 커밋 히스토리를 깔끔하게 유지하고자 할 때 또는 특정 브랜치에서 작업 중 다른 변경 사항을 포함시키고 싶을 때. | 브랜치의 병합 히스토리를 유지하고 싶을 때 또는 리베이스로 인한 충돌을 피하고 싶을 때 |

## git fetch 
git fetch는 원격 저장소에서 데이터를 가져오는 Git 명령어이다. 이 명령은 로컬 저장소에 원격 저장소의 최신 커밋, 브랜치, 태그 등의 정보를 업데이트하지만, 현재 작업 중인 로컬 브랜치의 상태를 변경하진 않습니다. 이를 통해, 사용자는 먼저 최신 변경 사항을 검토하고 로컬 브랜치에 병합하거나 리베이스하기 전에 준비할 수 있다.

git fetch origin feat 명령어를 사용하면, 실제로 로컬의 "feat" 브랜치에 직접적인 변화가 일어나지는 않는다. 대신, 원격 저장소(origin)의 "feat" 브랜치에 대한 최신 정보를 로컬에 가져오게 된다. 그리고 이 정보는 "origin/feat"라는 이름으로 참조된다.
즉, 이 명령은 원격 브랜치의 최신 상태를 로컬에 반영하는 것이지만, 로컬 브랜치 "feat"에는 직접적인 변경을 가하지 않는다. 로컬 브랜치에 변경 사항을 병합하려면, git merge origin/feat와 같은 명령어를 별도로 실행해야 한다. 이렇게 하면 "origin/feat"의 변경 사항이 로컬의 "feat" 브랜치와 병합(merge)된다.

git fetch origin feat를 실행했을 때 "origin/feat"라는 로컬 브랜치가 생성되는 것이 아니다. 대신, "origin/feat"는 원격 추적 브랜치(remote-tracking branch)라고 불리는 특별한 참조(reference)이다.
원격 추적 브랜치는 원격 저장소에 있는 브랜치의 상태를 반영한다. 이것은 로컬에 있는 복사본이지만, 직접적으로 변경할 수 없는 read-only 형태의 참조이다. git fetch를 사용하면 원격 저장소의 최신 변경 사항을 반영하여 이러한 원격 추적 브랜치를 업데이트한다.

"origin/feat"이 실제로 존재하는 브랜치는 아니며, 로컬 저장소에서 직접 변경하거나 체크아웃할 수 없다. 대신, 이것은 원격 브랜치 "feat"의 마지막 상태를 나타내며, 로컬에서 해당 상태를 보거나, 이를 기반으로 실제 로컬 브랜치를 생성하거나, 기존의 로컬 브랜치와 병합할 수 있다.
실제로 로컬 브랜치를 생성하려면 git checkout feat 또는 git switch feat 명령어를 사용하여 "origin/feat"를 기반으로 새 브랜치를 생성하거나, 만약 "feat" 브랜치가 이미 존재한다면 원격 추적 브랜치의 변경 사항을 병합할 수 있다.

* --all: 설정된 원격 저장소로부터 모든 브랜치와 데이터를 가져온다. 사용 예: git fetch --all
* --append: 가져온 레퍼런스를 기존 레퍼런스에 추가한다. 사용 예: git git fetch --append origin branch-name
* --depth=<depth>: 지정한 수의 최신 커밋만 가져온다. 이는 얕은 클론을 만드는 데 사용된다. 사용 예: git fetch --depth=1 origin branch-name("origin"에서 "branch-name" 브랜치의 최신 커밋 1개만 가져옴)
* --force: 로컬 변경 사항을 덮어쓰고, 로컬 브랜치를 원격 브랜치와 일치하게 강제 업데이트한다. 사용 예: git fetch --force origin branch-name
* --prune: 로컬에는 존재하지만 원격에는 더 이상 존재하지 않는 브랜치를 삭제한다. 사용 예: git fetch --prune origin
* --no-tags: 태그를 가져오지 않고 브랜치 정보만 가져온다. 사용 예: git fetch --no-tags origin branch-name
* --tags: 모든 태그를 가져오고 추가적으로 다른 객체를 가져온다. 사용 예: git fetch --tags origin
* --dry-run: 실제로 가져오지 않고 가져올 내용만 확인한다. 사용 예: git fetch --dry-run origin branch-name

## git merge 
![git-three-way-merging](https://github.com/FE-SW/StudyGit/assets/54196723/9e69b1bb-950a-4f27-bdb2-45861012c8a5)
git merge 명령어는 두 개 또는 그 이상의 개발 히스토리를 통합한다. 주로 두 개의 브랜치를 병합할 때 사용된다.

* --no-commit: 병합은 이루어지지만, 병합 커밋은 자동으로는 이루어지지 않는다. 사용자가 수동으로 커밋해야 한다. 사용 예: git merge --no-commit feature-branch
![05 04 01-2](https://github.com/FE-SW/StudyGit/assets/54196723/8a81d3c9-2947-4cc2-a3dd-cd4d182a8ce0)
* --ff: "fast-forward" 병합을 강제하는 옵션이다. 이 경우, 현재 브랜치가 병합될 브랜치의 앞에 있지 않다면, Git은 병합 커밋 없이 현재 브랜치를 병합할 브랜치의 최신 커밋으로 갱신한다. 사용 예: git merge --ff feature-branch
* --no-ff: 항상 병합 커밋을 생성하며, "fast-forward" 병합을 수행하지 않는다. 이 옵션은 두 브랜치의 히스토리를 유지한다. 사용 예: git merge --no-ff feature-branch
* --ff-only: "fast-forward" 병합만 수행하며, "fast-forward" 병합이 불가능할 경우 병합하지 않고 실패한다.(현재 체크아웃된 브랜치의 헤드가 feature-branch의 특정 커밋을 기반으로 한 후속 커밋이 없음을 의미) 사용 예: git merge --ff-only feature-branch
![05 04 06](https://github.com/FE-SW/StudyGit/assets/54196723/69aab496-3ee4-4404-83af-0bbf9b2cd87d) 
* --squash: 변경 사항을 하나의 새 커밋으로 병합하지만, 병합 커밋은 생성하지 않는다. feature-branch의 모든 변경 사항을 하나의 커밋으로 압축하지만, 자동으로 커밋하지는 않는다.스테이징 영역에 변경 사항들이 추가되어 기다리는 상태가 된다. 사용 예: git merge --squash feature-branch
* --abort: 병합 중 문제가 발생한 경우, 병합 이전 상태로 되돌린다. 사용 예: git merge --abort
* -m: 병합 커밋에 사용될 커밋 메시지를 지정한다. 사용 예: git merge -m "Merge feature branch" feature-branch

### 정리
* git merge --ff [브랜치명] : fast-forward 관계에 있으면 commit을 생성하지 않고 현재 브랜치의 참조 값 만 변경(default)
* git merge --no-ff [브랜치명] : fast-forward 관계에 있어도 merged commit 생성
* git merge --squash [브랜치명] : fast-forward 관계에 있어도 merged commit 생성, merging 브랜치 정보 생략


### 병합 커밋,Fast-forward 차이점
| 구분 | 병합 커밋(Merge Commit) | Fast-forward |
| --- | --- | --- |
| 정의 | 두 개의 브랜치를 병합할 때 생성되는 특별한 커밋이다. 병합 커밋은 두 부모를 가지며, 병합하는 브랜치의 히스토리를 모두 포함한다. | "Fast-forward"는 현재 브랜치(일반적으로 'master')가 병합하려는 브랜치(예: 'feature-branch')로 "앞당겨지는" 상황을 의미한다. 이 경우 별도의 병합 커밋 없이도 병합할 수 있다. |
| 히스토리 | 병합 커밋은 프로젝트의 커밋 히스토리에 명시적인 구조를 제공하며, 어떤 변경 사항이 어떤 브랜치에서 왔는지 명확하게 보여준다. | Fast-forward는 병합 대상 브랜치의 모든 커밋을 현재 브랜치로 그대로 가져와서 커밋 히스토리가 선형적으로 유지된다. |
| 사용 시나리오 | 팀이 공동으로 작업하는 브랜치에서 여러 개발자가 다양한 기능을 개발할 때 유용하다. 병합 커밋을 통해 언제 어떤 기능이 추가되었는지 쉽게 추적할 수 있다. | 개별적으로 작업한 작은 기능이나, 병합할 커밋이 현재 브랜치의 앞쪽에만 있는 경우에 유용하다. 히스토리를 간결하게 유지하고 싶을 때 사용한다. |

## git rebase 
![Rebasing-in-git](https://github.com/FE-SW/StudyGit/assets/54196723/ff2f84c6-ebaf-4b59-a198-c8d91d61d5cb)
git rebase는 한 브랜치에서 만든 커밋들을 다른 브랜치로 옮겨서(재배치해서) 기존의 커밋들 위에 적용하는 과정이다. 이 과정은 커밋 히스토리를 더 깔끔하게 만들어주며, 병합된 커밋들을 선형적으로 만들어주기 때문에 프로젝트의 히스토리를 더 읽기 쉽게 해준다.
그러나, rebase는 기존의 커밋 히스토리를 변경하기 때문에 주의해서 사용해야 한다. 이미 공개된 원격 브랜치의 커밋을 rebase하면 커밋의 해시가 변경되어, 다른 이력과 충돌할 가능성이 있다. 이런 이유로 rebase는 주로 로컬 브랜치에서 사용하는 것이 좋다.

* -i, --interactive: 리베이스를 인터랙티브하게 수행한다. 이 모드에서는 사용자가 커밋을 수정, 삭제, 합치기 등을 수행할 수 있다. 사용 예: git rebase -i HEAD~3(현재 브랜치에서 최근 3개의 커밋을 선택하여 인터랙티브 리베이스를 시작한다. 인터랙티브 세션에서는 커밋 순서 변경, 커밋 삭제, 커밋 메시지 수정 등을 할 수 있다.)
* --onto <newbase>: 현재 브랜치의 커밋들을 <newbase> 위로 리베이스한다. 사용 예: git rebase --onto master feature1 feature2(feature1 브랜치와 feature2 브랜치 사이의 커밋들을 가져와서 master 브랜치 위에 재배치한다.)
* --continue: 리베이스 과정 중에 충돌이 발생하고, 해결한 후 리베이스를 계속 진행하도록 명령한다. 사용 예: git rebase --continue(충돌해결 후 사용할 수 있는 명령이며, 이 명령은 리베이스 과정을 계속 진행한다.)
* --abort: 현재의 리베이스를 중지하고, 리베이스를 시작하기 전 상태로 돌아간다. 사용 예: git rebase --abort
* --skip: 충돌로 중단된 리베이스를 계속 진행하지만, 충돌난 커밋은 스킵한다. 사용 예: git rebase --skip
* --edit-todo: 인터랙티브 모드에서 할 일 목록을 편집한다. 사용 예: git rebase --edit-todo
* -p, --preserve-merges: 리베이스하는 동안 병합 커밋을 유지하려고 시도한다. 사용 예: git rebase -p master(이는 master로 리베이스하면서 병합 커밋도 유지한다.)

![image](https://github.com/FE-SW/StudyGit/assets/54196723/04a1158e-b189-43e0-80f8-6671591fcdb2)

| 기준            | merge                                            | rebase                                        |
|-----------------|--------------------------------------------------|-----------------------------------------------|
| 목적            | 두 브랜치의 히스토리를 합친다.                    | 한 브랜치의 커밋을 다른 브랜치 위로 옮긴다.       |
| 히스토리        | 병합된 히스토리를 유지하여 복잡해질 수 있다.       | 더 깔끔하고 선형적인 히스토리를 생성한다.          |
| 커밋            | 새로운 '병합 커밋'을 생성한다.                     | 기존 커밋을 재사용하거나 새로운 커밋을 만든다.     |
| 충돌            | 한 번에 처리되며, 병합 커밋에서 확인할 수 있다. | 각 커밋마다 발생할 수 있으며, 각각 해결해야 한다. |
| 공유된 브랜치   | 안전하다. 공유된 브랜치의 커밋 히스토리를 변경하지 않는다. | 주의가 필요하다. 공유된 브랜치의 커밋 히스토리를 변경한다. |



# 참고
* https://wikidocs.net/book/7060



