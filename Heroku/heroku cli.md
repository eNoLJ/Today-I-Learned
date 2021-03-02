## heroku cli를 이용하여 앱 배포하기

### **heroku cli 설치**

[heroku cli 설치](https://devcenter.heroku.com/articles/deploying-spring-boot-apps-to-heroku)에 들어가서 운영체제에 맞는 cli를 설치한다.

하지만 m1 맥을 사용해서 그런진 몰라도 segmentation fault 오류가 뜨면서 사용을 할 수 없었다.

그래서 [heroku homebrew](https://devcenter.heroku.com/articles/heroku-cli)를 이용해서 설치를 진행 했다. 해당 링크를 보면

```bash
brew tap heroku/brew && brew install heroku
```

명령어를 이용해 설치하라고 안내가 되어있다. 여기서 arm 아키텍쳐 오류가 뜨면서 설치가 되지않아

```bash
brew tap heroku/brew && arch -x86_64 brew install heroku
```

명령어로 설치를 진행했다. 이번엔 xcode를 설치하란 안내가 떴고

```bash
 xcode-select --install
```

명령어를 통해 설치한 후 다시 brew install을 진행 했더니 설치가 되었다.

</br>

### **heroku cli 사용**

1. heroku login

   ```bash
   heroku login
   ```

   명령어로 로그인 한다.

2. heroku repository 설정

   배포하려는 웹 앱 폴더로 이동한다.

   ```bash
   heroku create
   ```

   명령어로 heroku repository를 설정한다. 여기서 주의할 점은 해당 앱에 git이 설치되어 있어야 한다. 그리고 설치를 진행하면 앱에 이름이 부여된다.

   ```bash
   git remote -v
   ```

   명령어를 통해 확인해보면 heroku가 들어와 있는걸 확인 할 수 있다.

3. heroku 배포

   여기까지 왔으면 배포는 간단하다. origin에 push 하듯이 heroku에 pugh 해주면 된다.

   ```bash
   git push heroku main
   ```

   배포가 완료되면

   ```bash
   heroku open
   ```

   명령어로 열어볼 수 있다.

TIP

heroku app 삭제

```bash
heroku apps:destroy --app [heroku 앱 이름] --confirm [heroku 앱 이름]
```

heroku app 이름변경

```bash
heroku apps:rename [새로운 이름] --app [기존 이름]
```
