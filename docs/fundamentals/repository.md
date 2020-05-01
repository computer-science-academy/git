### Repository

[Git glossary](https://git-scm.com/docs/gitglossary#Documentation/gitglossary.txt-aiddefrepositoryarepository)에 따르면 Repository의 정의는 다음과 같다.
> A collection of refs together with an object database containing all objects which are reachable from the refs, possibly accompanied by meta data from one or more porcelains. A repository can share an object database with other repositories via alternates mechanism.

[`ref`](https://git-scm.com/docs/gitglossary#Documentation/gitglossary.txt-aiddefrefaref)의 집합이면서
그 `ref`들로 부터 도달 가능한 [`object`](https://git-scm.com/docs/gitglossary#Documentation/gitglossary.txt-aiddefrefaref)들을 포함한다.

여기서 `ref`는 또 다른 `ref` 혹은 `object`를 가리키는 참조이며, `object`는 실제 데이터를 담고 있는 객체들이다.

`object`는 그 내용에 따른 hash 값을 name으로 갖기 때문에, 수정이 불가능하다는 특징이 있다(내용을 수정하면 수정된 새 객체를 만드는 것일 뿐 기존 객체를 수정할 수는 없다).
바로 이 점 덕분에 같은 내용을 가지는 객체는 여럿을 만들 필요 없이 하나를 공유해서 사용할 수 있어 스토리지를 절약할 수 있다.
[COW(Copy On Write)](https://en.wikipedia.org/wiki/Copy-on-write)의 컨셉과 유사하다고 볼 수 있다.

object의 hash 값을 만들어내는 plumbing 명령어 가 있다.
```bash
printf 'Hello, git\n' | git hash-object --stdin
```
언제, 어디서 저 명령을 실행하든 다음과 같은 동일한 출력을 볼 수 있다.
```
22f46444d223ec55b7677c6dd212b155fe2a7661
```
