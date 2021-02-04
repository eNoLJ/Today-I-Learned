# Apple Silicon M1 Mac Docker와 MySQL 설치

### 시작 전 알아두면 편한 docker 명령어

> docker images : 이미지 보기
>
> docker rmi [image id] : 이미지 삭제
>
> docker ps : 동작중인 컨테이너 확인
>
> docker ps -a : 모든 컨테이너 확인
>
> docker rm [컨테이너 id] : 컨테이너 삭제
>
> docker start [컨테이너 이름] : 컨테이너 시작
>
> docker stop [컨테이너 이름] : 컨테이너 종료

</br>

## Docker 설치

- [m1 preview 버전](https://docs.docker.com/docker-for-mac/apple-m1/)

</br>

## MySQL 이미지 다운로드

```
$ docker pull mysql:[버전]
```

일반적으로 위에 보이는 명령어로 버전을 선택하여 설치하지만 M1 Mac의 경우 아래처럼 오류가 난다.

![image](https://user-images.githubusercontent.com/63284310/106711576-0ea91e00-663b-11eb-8715-925a9f50e8c6.png)

다시 아래 명령어로 실행해 본다.

```
$ docker run --rm --platform linux/amd64 -it mysql:[버전]
```

그럼 arm용 이미지가 아니라는 경고문이 뜨지만

```
$ docker images
```

명령어를 통해 확인해보면 이미지가 설치 된 것을 확인 할 수 있다.

![image](https://user-images.githubusercontent.com/63284310/106711956-a60e7100-663b-11eb-9a4b-b22e74295d63.png)

</br>

## MySQL 컨테이너 생성

```
$ docker run -d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=[비밀번호] --name [컨테이너 이름] mysql:[버전]
```

해당 명령어로 컨테이너를 생성할 수 있다.

하지만 MySQL Server와 Db의 characterset을 utf8md4로 지정해 주기 위해 밑에 인자를 추가해 줍니다.

```
--character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci
```

Example

```
$ docker run -d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=1234 --name myMySQL mysql:5.7 --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci
```

</br>

## MySQL 컨테이너 bash 접속

```
$ docker exec -it [컨테이너 이름] bash
```

해당 명령어를 통해 컨테이너에 접속 할 수 있다.

하지만 이렇게 접속 했을 때 한글이 입력되지 않는 문제가 생긴다. 그렇기 때문에 locale 설정을 해줘야 한다.

### 방법 1

```
-e LC_ALL=C.UTF-8
```

간단하게 위에 인자를 추가해서 locale을 C.URF-8로 변경 할 수 있다.

### 방법 2

두번째 방법은 docker 서버에 locale을 설치해서 ko_KR.UTF-8로 변경해 주는 방법이다.

아래 명령어를 순서대로 입력한다.

```
$ apt-get install
$ apt-get update
$ apt-get install locales
$ localedef -f UTF-8 -i ko_KR ko_KR.UTF-8
$ export LC_ALL=ko_KR.UTF-8
$ LC_ALL=ko_KR.UTF-8 bash
$ export LANG=ko_KR.UTF-8
```

```
$ locale
```

명령어로 확인하면 locale이 제대로 설정된 걸 확인할 수 있다.

![image](https://user-images.githubusercontent.com/63284310/106713478-e1aa3a80-663d-11eb-8921-19d43a025c18.png)

### 주의

재접속을 하면 locale 설정이 초기화되기 때문에 locale을 다시 export 해줄 필요가 있다.

</br>

## MySQL 접속

```
$ mysql -u [사용자 이름] -p
```

</br>

## MySQL characterset 설정

MySQL에서도 마찬가지로 한글을 사용하기 위해 characterset을 latin1을 UTF-8로 바꿔줄 필요가 있다.

```
$ cat << 'EOF' > /etc/mysql/mysql.conf.d/utf8.cnf
```

```
[client]
default-character-set = utf8

[mysqld]
init_connect = SET collation_connection = utf8_general_ci
init_connect = SET NAMES utf8
character-set-server = utf8
collation-server = utf8_general_ci

[mysqldump]
default-character-set = utf8

[mysql]
default-character-set = utf8
EOF
```

```
mysql> status
```

명령어로 확인해보면 characterset이 바껴있는걸 확인 할 수 있다.

![image](https://user-images.githubusercontent.com/63284310/106714473-3e5a2500-663f-11eb-84d3-99f0bc316a65.png)

</br>

참고사항

server characterset과 db characterset은 컨테이너를 생성할 때 "--character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci" 인자를 붙여주면 바꿀 수 있다.

client
characterset과 conn. characterset은 컨테이너 접속할 때 "-e LC_ALL=C.UTF-8" 인자를 넣거나 위 MySQL characterset 설정 방법을 통해 바꿀 수 있다.
