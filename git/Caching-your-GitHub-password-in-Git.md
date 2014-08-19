#Caching your GitHub password in Git

github 이용시 https를 이용하여 repository를 clone하면, **credential helper**를 이용하여 인증을 물어보지 않게 할 수 있다.

만약, ssh를 이용해서 clone을 했을 경우에는, ssh key를 이용하여 인증을 한다.

사용법
----
먼저, git 1.7.10이상 필요함
brew를 이용하여 git을 설치했으면, osxkeychain helper가 자동으로 설치됨

```sh
git credential-osxkeychain
```
위 명령어로 설치가 되었는지 확인

설치가 안되어 있는 경우는 [링크](https://help.github.com/articles/caching-your-github-password-in-git#platform-mac) 확인

```sh
git config --global credential.helper osxkeychain
```
위 명령어로 osxkeychain helper 설정

이제 다시 한번 인증을 거치고 나면 다음 push부터는 사용자 인증을 하지 않음