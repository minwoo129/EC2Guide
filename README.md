# AWS EC2 인스턴스 생성

## 작업 환경

- 컴퓨터 OS: MacOS

## 생성 방법

1. [AWS](https://aws.amazon.com/ko/?nc2=h_lg) 접속

   ![img01.png](https://fejumvuajiwc28287693.gcdn.ntruss.com/EC2Guide/img01.png)

2. 로그인 후 콘솔에서 EC2 접속

   ![img02.png](https://fejumvuajiwc28287693.gcdn.ntruss.com/EC2Guide/img02.png)

   ![img03.png](https://fejumvuajiwc28287693.gcdn.ntruss.com/EC2Guide/img03.png)

3. 하단에 “인스턴스 시작” 클릭

   ![img04.png](https://fejumvuajiwc28287693.gcdn.ntruss.com/EC2Guide/img04.png)

4. 이미지 속 페이지가 열리면 관련 정보 입력

   ![img05.png](https://fejumvuajiwc28287693.gcdn.ntruss.com/EC2Guide/img05.png)

   - 이름: 원하는 대로(가급적 영어로)
   - 애플리케이션 및 OS 이미지
     - OS: (원하는 OS를 사용하면 되지만 나는 **Ubuntu**를 자주 사용함)
       ⇒ 보안 및 개인정보 보호에 용이하고 다양한 언어를 지원하며, 특히 초심자가 사용하기 편함
       ⇒ 참고 자료: [https://ciksiti.com/ko/chapters/9815-ubuntu-vs-amazon-linux](https://ciksiti.com/ko/chapters/9815-ubuntu-vs-amazon-linux)
       (리눅스 아님 우분투 둘중 하나를 사용하면 문제 없을 듯)
   - 인스턴스 유형
     - 프리티어 기간이 남아있다면 프리티어로 사용할 수 있는 인스턴스를 사용하면 됨
   - 키페어

     - 만약 만들어둔 키페어가 없는 경우

       1. “새 키 페어 생성” 클릭
       2. 페이지가 열리면 원하는 키페어 이름을 입력하고 “생성”을 누른다.
       3. 그렇게 하면 생성한 키페어 파일을 다운받을 수 있다. 키 페어를 다운받고 컴퓨터 내 원하는 디렉토리에 저장해둔다.

          ⇒ 키페어 파일은 **다시 생성할 수 없고** 내 컴퓨터에서 ssh로 인스턴스에 접속할 때 필요하기 때문에 잘 관리해야 한다.

     - 만약 이전에 만들어둔 키페어가 있는 경우
       1. Select Box를 열어보면 이전에 생성한 키페어가 표시된다. 사용할 키페어를 선택하면 된다.

   ⇒ 이 과정들이 완료되면 “인스턴스 시작”을 클릭한다. 그러면 1,2분안에 인스턴스가 생성되어 사용이 가능하다.

5. 인스턴스 정보 확인

   EC2 메인 콘솔에서 왼쪽에 인스턴스를 클릭하면

   ![img07.png](https://fejumvuajiwc28287693.gcdn.ntruss.com/EC2Guide/img07.png)

   다음과 같은 페이지가 열린다.

   ![img08.png](https://fejumvuajiwc28287693.gcdn.ntruss.com/EC2Guide/img08.png)

   여기서 내가 생성한 인스턴스 ID를 클릭하면 다음과 같이 인스턴스 상세 정보를 확인할 수 있다.

   ![img09.png](https://fejumvuajiwc28287693.gcdn.ntruss.com/EC2Guide/img09.png)

6. 인스턴스 보안설정

   인스턴스 상세에서 하단에 “보안”을 클릭하면

   ![img10.png](https://fejumvuajiwc28287693.gcdn.ntruss.com/EC2Guide/img10.png)

   아래와 같은 화면이 표시된다.

   ![img11.png](https://fejumvuajiwc28287693.gcdn.ntruss.com/EC2Guide/img11.png)

   여기서 주황색 박스로 표시된 부분에 보안그룹 아이디가 적혀있는데(보안을 위해 모자이크 처리해둠), 이 아이디를 클릭한다.

   아래와 같은 창이 열리면 아래 이미지와 같이 포트 80번, IPv4로 모든 IP에서 접속할 수 있게 하면 된다.(22번은 기본 생성된다)

   ⇒ 3306번은 mySQL 접속 디폴트 포트번호. mySQL을 안 쓴다면 추가 안해도 됨

7. 인스턴스 접속하기

   인스턴스 상세정보 페이지에서 상단에 “연결”버튼을 클릭하면 인스턴스의 **사용자 이름**과 **퍼블릭 IP**가 표시된다. 이 두 정보를 적어둔다.

   이제부터 인스턴스를 추가할 때 컴퓨터에 다운받은 AWS 키페어파일을 사용해야 한다.

   터미널을 통해 키페어 파일이 추가된 디렉토리로 접속한다.

   그리고 이 키페어를 사용해서 처음 접속하는 경우 다음 명령어를 먼저 실행한다.

   ```xml
   chmod 400 {키페어 파일 이름(확장자까지 입력)}
   ```

   이 다음에 아래 명령어를 입력하면 인스턴스에 접속할 수 있다.

   ```xml
   ssh -i "{키페어 파일 이름(확장자까지)}" {사용자 이름}@{퍼블릭 IP 주소}
   ```

   접속 성공 예시

   ![img12.png](https://fejumvuajiwc28287693.gcdn.ntruss.com/EC2Guide/img12.png)
