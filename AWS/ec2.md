# AWS EC2 시작하기

## 1. 리전 설정

![image](https://user-images.githubusercontent.com/63284310/130569686-e29d2eef-89f4-42fd-99c2-8f8daf543886.png)

- 리전은 서울로 설정

![image](https://user-images.githubusercontent.com/63284310/130569691-95ace6b7-372c-48fd-b33c-8b7fec76c4cf.png)

- 리전 설정 후 EC2 선택

</br>

## 2. 인스턴스 시작

![image](https://user-images.githubusercontent.com/63284310/130570285-ebdc3eb4-85fd-4338-94c7-b33833f71e7c.png)

1. 좌측 인스턴스 선택
2. 우측 상단의 인스턴스 시작 클릭

</br>

## 3. AMI 선택

![image](https://user-images.githubusercontent.com/63284310/130570289-395433aa-d744-4fea-8726-6e750e86d0c7.png)

- 예상 가능하겠지만 운영체제를 선택하는 페이지이다.
- ubuntu 64비트 선택

  \* AMI(Amazon Machine Image)은 미리 만들어진 머신 이미지라 생각하면 된다.

</br>

## 4. 인스턴스 유형 선택

![image](https://user-images.githubusercontent.com/63284310/130570295-b6853ccc-8120-40eb-a6ae-c793ee51f512.png)

- 프리티어 전용 t2.micro를 선택하고 세부 정보 구성 클릭

  \* 유형 별로 cpu, 메모리 등 사양이 다르며 좋은 사양일수록 시간당 추가 비용이 발생한다.
  t2.medium이 시간당 200원, t2.large가 시간당 400원 꼴이다.

</br>

## 5. 인스턴스 구성

![image](https://user-images.githubusercontent.com/63284310/130570300-facda710-8255-4b47-b22a-cdc6e8a369f6.png)

- 따로 설정해줄건 없다. 다음 선택

  \* VPC 설정은 추후 정리 예정

</br>

## 6. 스토리지 추가

![image](https://user-images.githubusercontent.com/63284310/130571925-8234440c-bc71-4378-9c76-8729908c851a.png)

- 용량을 설정하는 페이지이다. 간단한 어플은 8기가로도 충분하다!! 다음 클릭!!

  \* 프리티어는 30시간까지 무료로 사용가능

</br>

## 7. 태그 추가

![image](https://user-images.githubusercontent.com/63284310/130571931-2bb9ee31-65c2-4d20-8192-4d32db9fe1bf.png)

1. 키를 Name(지정된 값, 대소문자 구별 함)으로 값은 인스턴스 이름을 정해서 기입해주면 된다.

   \* 굳이 지정하지 않아도 생성 가능

2. 다음 클릭

</br>

## 8. 보안 그룹 구성

![image](https://user-images.githubusercontent.com/63284310/130571935-5b03efb0-1d52-4c7d-9dab-57857fc3621e.png)

1. 새 보안그룹 생성 선택, 보안그룹 이름 지정, 보안그룹에 대한 설정 기입

   \* 만들어진 보안 그룹은 계속 사용할 수 있다. 한마디로 규칙이 동일한 보안을 설정할 경우 새로 만들지 않고 그대로 사용하면 된다.

2. 규칙 추가를 통해 사용자 지정 TCP 선택 후 8080 포트를 열어준다.

   \* 규칙은 간단하게 EC2 컴퓨터에 접속할수 있도록 범위를 설정해주는 것이다.

   \* ssh의 22번 포트를 통해 0.0.0.0/0 범위에 해당하는 ip의 접속을 허용하겠다는 뜻이다. 주의할 점으로 ssh 접속으로 모든 ip를 허용하게 되면 누구나 어디서든 내 서버에 접속할 수 있기때문에 위험하다.

   \* 0.0.0.0/0는 인터넷 프로토콜 IPv4 버전의 모든 ip를 의미한다.(0.0.0.0/0, ::/0은 IPv6)

   \* 사용자 지정 TCP의 8080 포트를 열어주는 이유는 보통 서버를 실행하면 8080포트로 실행이 되기 때문에 해당 포트로 접속 시 서버의 API를 요청할 수 있도록 하기 위해서다.

</br>

## 9. 검토

![image](https://user-images.githubusercontent.com/63284310/130571938-f659020c-6ba0-4449-8f67-85cb96d3002b.png)

- 시작하기 클릭

  \* 주의사항이 뜬 이유는 위에 설명했듯이 ssh 접속을 모든 ip로 설정했기 때문이다. 연습이니 넘어가자.

</br>

## 10. 키 페어 생성

![image](https://user-images.githubusercontent.com/63284310/130575186-9c4ae0c3-0078-4d86-83f8-53eab1c1c06f.png)

1. 새 키 페어 생성 선택, 키 페어 이름 기입, 키 페어 다운로드 클릭

   \* ssh 접속을 하기위한 키 파일을 생성하기 위한 페이지이다.

   \* 키 페어 다운로드는 한번밖에 안된다.

2. 키 페어를 다운받았으면 인스턴스 시작을 클릭한다.

</br>

## 11. 확인

![image](https://user-images.githubusercontent.com/63284310/130575189-6d1dd66f-3a21-4022-b680-74c370a1adec.png)

- 해당 페이지가 보이면 정상적으로 인스턴스가 설정 된 것이다. 인스턴스 보기를 클릭하여 확인한다.

![image](https://user-images.githubusercontent.com/63284310/130575195-03456d9f-3850-4585-9562-4cb4f7ff07b8.png)

- 해당 인스턴스가 만들어지고 있는 중이다.

![image](https://user-images.githubusercontent.com/63284310/130575198-c02c9b71-7e34-49aa-b99a-f562bf543fd3.png)

- 해당 인스턴스를 사용할 준비가 완료 되었다.

  \* 프리티어 경우 EC2는 한달에 750시간 무료로 사용가능하다. 인스턴스 하나만 실행 시 한달 내내 돌리기가 가능하지만 2개일 경우 2개의 시간을 합하여 계산된다.

![image](https://user-images.githubusercontent.com/63284310/130575203-608bb376-133f-45e2-89a0-042735c8becd.png)

</br>

## 12. EC2 접속 방법

![image](https://user-images.githubusercontent.com/63284310/130576311-12388e11-be4b-4cd9-a9c7-133a71c2a10d.png)

- 인스턴스 id를 클릭한다.

![image](https://user-images.githubusercontent.com/63284310/130576325-39b823dc-d0e8-4f8f-9897-826fd306c50b.png)

- 연결을 클릭 한다.

![image](https://user-images.githubusercontent.com/63284310/130576332-ba601c3c-c6ef-4dcf-8e52-ea0816be5826.png)

1. SSH 클라이언트 클릭

2. ssh 접속을 위해 키 파일의 권한을 변경하는 명령어이다.

3. 도메인 접속을 위한 주소이다.

4. ssh 접속을 하기 위한 명령어이다.

   \* -i 옵션은 키 파일을 지정한다.

   \* ubuntu는 EC2 사용자의 이름이다.(해당 이미지의 EC2 인스턴스 연결 탭에서 확인 할 수 있다.)

   \* 3번에 언급한대로 도메인 주소이다. 퍼블릭 ip주소로도 접속 가능하다.

</br>

## EC2 접속

![image](https://user-images.githubusercontent.com/63284310/130578004-105edb69-86ff-421d-989e-bbf3b2b92aa6.png)

- chmod 명령어를 통해 키 파일의 권한을 변경한다.

- ssh 접속 명령어를 통해 EC2에 접속한다. 처음 접속 시 해당 메세지가 출력되며 yes를 입력해준다.(이후 접속 시에는 해당 메세지가 출력되지 않는다.)

  \* ssh 폴더에 키를 저장하게 된다. 그렇기 때문에 인스턴스의 ip나 키가 변경 되면 ssh 접속 시 ssh 폴더를 먼저 뒤지게 되면서 해당 ip와 키가 일치하지 않으면 접속이 불가하다. 그 땐 기록을 지우고 다시 ssh 접속을 시도하면 위와 동일한 메세지가 출력되며 다시 정상적으로 접속이 가능하다.

![image](https://user-images.githubusercontent.com/63284310/130576340-4dc8607a-726f-4f4c-b5e2-013ba6bcaf5e.png)

- 정상적으로 접속 된 모습이다.
