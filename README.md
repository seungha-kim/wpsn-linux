# WPSN Linux 튜토리얼

## EC2

[AWS EC2(Elastic Compute Cloud)](http://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/concepts.html)는 리눅스 및 Windows 가상 서버를 제공하는 AWS 서비스입니다. 서버를 사용한 시간만큼만 과금되고, 필요에 따라 서버의 갯수를 늘였다가 줄였다가 하는 일을 자유롭게 할 수 있습니다. 또한 서버를 다시 구축할 필요 없이 서버의 사양을 높이거나 낮출 수도 있습니다.

- [인스턴스 및 AMI](http://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/ec2-instances-and-amis.html)
- [리전 및 가용 영역](http://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/using-regions-availability-zones.html)
- [IAM 역할](http://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html)
- [보안 그룹](http://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/using-network-security.html)
- [Elastic Block Store](http://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/AmazonEBS.html)
- [키 페어](http://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/ec2-key-pairs.html)

EC2 인스턴스에 접속하기 위해 키 페어가 필요합니다. 인스턴스 생성 시 다운로드 받은 비밀 키를 잃어버리면 인스턴스에 접속할 수 없게 되니 주의하세요.

## SSH

SSH(Secure Shell)는 네트워크 상의 다른 컴퓨터에 접속해서 명령을 실행하거나 파일을 전송할 수 있도록 해 주는 응용 프로그램, 혹은 그 프로토콜을 말합니다. 보통 22번 포트를 사용합니다.

SSH는 통신을 암호화하기 때문에 다른 사람이 통신의 내용을 엿볼 수 없습니다. Git 역시 통신을 위해 SSH 프로토콜을 사용하고 있습니다.

EC2 인스턴스 역시 SSH를 통해 접속할 수 있습니다. 접속을 위해서 인스턴스 생성 시에 부여받은 비밀 키가 필요합니다. EC2 Instances 페이지 상단의 **Connect** 버튼을 눌러 가이드를 따라하세요.

## 리눅스에서 자주 사용되는 명령

아래에 자주 사용하는 리눅스 명령을 모아두었습니다. `man` 명령을 사용하면 다른 명령에 대한 도움말을 표시할 수 있습니다. (예: `man ls`)

### 파일 관리 명령

- `ls`: 디렉토리의 내용을 표시합니다.
- `pwd`: 작업 디렉토리를 표시합니다.
- `touch`: 빈 파일을 만듭니다.
- `cp`: 파일 혹은 디렉토리를 복사합니다.
- `mv`: 파일 혹은 디렉토리를 이동합니다. 이름을 바꿀 때에도 사용됩니다.
- `rm`: 파일 혹은 디렉토리를 삭제합니다.
- `chmod`: 파일의 접근 권한을 설정합니다.
- `chown`: 파일의 소유자를 변경합니다.
- `ln`: [파일 링크](https://ko.wikipedia.org/wiki/%EC%8B%AC%EB%B3%BC%EB%A6%AD_%EB%A7%81%ED%81%AC)를 만듭니다.

### 시스템 및 접속 정보

- `who`: 시스템에 접속 중인 계정을 표시합니다.
- `whoami`: 현재 접속자의 계정 이름을 표시합니다.
- `date`: 현재 시간을 표시합니다.
- `top`: 시스템 자원과 프로세스의 정보를 표시합니다. 이와 유사하지만 더 편리하게 사용할 수 있는 [htop](http://hisham.hm/htop/)라는 도구도 있습니다.
- `free`: 시스템의 메모리 사용량을 표시합니다.
- `df`: 시스템의 디스크 사용량을 표시합니다.
- `du`: 파일 및 디렉토리의 디스크 사용량을 표시합니다.

### 프로세스 관리

- `sleep`: 쉘을 일정 시간동안 정지시킵니다.
- `ps`: 시스템에서 실행되고 있는 프로세스의 정보를 표시합니다.
- `jobs`: 현재 쉘에서 실행 중인 작업을 표시합니다.
- `fg`: 중지되었거나 백그라운드에서 실행되고 있는 작업을 포그라운드로 표시합니다.
- `bg`: 중지되어 있는 작업을 백그라운드에서 실행시킵니다.
- `kill`: 특정 프로세스를 종료합니다.
- `nohup`: 터미널이 종료되어도 프로세스가 종료되지 않도록 합니다.

### 파일의 내용 표시

- `cat`: 파일의 내용을 출력합니다.
- `less`: 파일의 내용을 스크롤하며 탐색합니다.
- `tail`: 파일의 마지막 부분의 내용을 출력합니다.
- `echo`: 문자열을 출력합니다.
- `wc`: 파일의 단어 갯수를 세어 표시합니다.
- `tee`: 표준 입력으로 출력과 파일 저장을 동

### 기타

- `grep`: 파일의 내용을 필터링합니다.
- `curl`: URL을 통해 통신을 합니다. curl 명령을 통해 파일을 다운로드 받을 수 있습니다.
- `clear`: 터미널 화면의 내용을 비웁니다.
- `sudo`: 관리자 권한으로 명령을 실행합니다.

### 패키지 관리

- `apt`: 데비안 계열 리눅스의 패키지 매니저인 APT를 이용해 패키지를 관리합니다.

### 리눅스 참고자료

- [Subshell](https://mug896.gitbooks.io/shell-script/content/subshells.html)
- [Redirection](https://mug896.gitbooks.io/shell-script/content/redirections.html)
- [Pipe](https://mug896.gitbooks.io/shell-script/content/pipe.html)
- [Job](https://mug896.gitbooks.io/shell-script/content/job_control.html)
- [Signal](https://mug896.gitbooks.io/shell-script/content/signals_and_traps.html)

## Cyberduck

[Cyberduck](https://cyberduck.io/)은 SSH를 통해 파일을 전송할 수 있는 프로토콜인 [SFTP](https://ko.wikipedia.org/wiki/SSH_%ED%8C%8C%EC%9D%BC_%EC%A0%84%EC%86%A1_%ED%94%84%EB%A1%9C%ED%86%A0%EC%BD%9C)을 지원하는 파일 브라우저입니다. SFTP 외에도 많은 프로토콜 및 서비스를 지원합니다.

Cyberduck을 이용해 편하게 EC2에 파일 전송을 할 수 있습니다. SFTP 연결을 새로 만들고 EC2 주소와 EC2 비밀 키를 넣어 주면 됩니다.

## RDS

RDS는 클라우드에서 관계형 데이터베이스를 제공하는 AWS 서비스입니다. EC2와 유사하게 유연한 배포 및 확장이 가능합니다. MySQL, PostgreSQL, Oracle, MS SQL 등의 다양한 RDBMS를 지원합니다.

### RDS 보안 그룹

RDS 보안 그룹의 소스로 다른 보안 그룹을 지정할 수 있습니다. 이렇게 설정하면, 외부(인터넷)으로부터의 접속은 막히는 대신 해당 보안 그룹을 사용하는 모든 인스턴스(일반적으로 애플리케이션 서버)에서 수신 트래픽이 허용됩니다. 자세한 내용은 [공식 문서](http://docs.aws.amazon.com/ko_kr/AmazonRDS/latest/UserGuide/Overview.RDSSecurityGroups.html)를 참고해주세요.

위와 같은 보안 그룹 설정을 적용하면 일반적인 방식으로는 보안 그룹 바깥에서 RDS 인스턴스에 접속할 수 없게 됩니다. 대신 [SSH 터널링](http://www.hanbit.co.kr/network/category/category_view.html?cms_code=CMS5064906327)을 활용해 SSH를 거쳐서 접속하면, 바깥에서도 RDS 인스턴스에 접속할 수 있습니다. MySQL Workbench를 이용하면 SSH를 거치는 MySQL 커넥션을 쉽게 만들 수 있습니다.

## Git을 이용한 웹 서버 배포

이제 이전에 실습했었던 [채팅 서버](https://github.com/seungha-kim/wpsn-socketio)를 EC2와 RDS를 사용해서 배포해보겠습니다.

일단 서버에서 Github 저장소를 복제하기 위해서는 SSH key 생성과 등록이 필요합니다.

```bash
$ ssh-keygen
$ cat ~/.ssh/id_rsa.pub
```

그 다음, 보안 그룹이 잘 설정되었는지 확인하고 EC2 주소에 접속해보세요.

## Route 53

Route 53은 도메인과 관련된 기능을 제공하는 AWS 서비스입니다. Route 53을 통해 도메인 구입, DNS 서버 설정 등을 할 수 있습니다.

Route 53에서 구입한 도메인을 EC2 인스턴스에 연결시킬 수 있습니다. 자세한 내용은 [공식 문서](http://docs.aws.amazon.com/ko_kr/Route53/latest/DeveloperGuide/routing-to-ec2-instance.html)를 참고해주세요.

## PM2

Node.js로 만들어진 웹 서버는 예기치 못한 에러 때문에 종료되어버리는 경우도 있고, 메모리 누수가 발생하는 경우도 잦습니다. 이런 문제를 해결하기 위해 서버가 예상치 못한 이유로 종료되었을 때 서버를 재시작해주고, 또 메모리 사용량이 일정량 이상이 되면 서버를 재시작해주는 등의 작업이 필요합니다. 이런 작업을 자동화해주는 도구를 보고 **프로세스 매니저**라고 부릅니다.

**PM2**는 Node.js 생태계에서 가장 널리 사용되는 프로세스 매니저입니다. [비슷한 다른 도구들과 비교](http://expressjs.com/ko/advanced/pm.html)했을 때 사용하기 쉽고 편의 기능이 많습니다. 또한 Node.js 모니터링 도구인 [Keymetrics](https://keymetrics.io/)와 긴밀하게 통합됩니다.

또한 PM2에는 Node.js cluster를 자동 생성해주는 기능 및 로드 밸런서가 포함되어 있어서, 고성능 웹 서버를 쉽게 운영할 수 있도록 해줍니다. Cluster에 대한 자세한 설명은 [공식 문서](http://pm2.keymetrics.io/docs/usage/cluster-mode/)를 참고해주세요.

보통 아래와 같이 프로세스 정의 파일을 통해 실행할 스크립트와 환경변수 등을 설정한 후, 해당 설정에 이름을 붙여서 실행하게 됩니다. 자세한 사용법은 [공식 문서](http://pm2.keymetrics.io/docs/usage/application-declaration/)를 참고해주세요.

```yml
# process.yml
apps:
  apps:
  - script   : ./api.js
    name     : 'api-app'
    instances: 4
    exec_mode: cluster
  - script : ./worker.js
    name   : 'worker'
    watch  : true
    env    :
      NODE_ENV: development
    env_production:
      NODE_ENV: production
```

```bash
$ pm2 start process.yml --name myapp
```

## Reverse Proxy

리버스 프록시는 웹 서버의 일종으로, 시스템의 바깥 쪽에서 내부에 있는 웹 서버로 요청을 전달해주는 기능을 합니다. 리버스 프록시는 보통 다음과 같은 역할을 수행합니다.

- DDoS 등의 공격을 막는 방화벽
- 부하를 분산시키는 로드 밸런서
- 정적 컨텐츠 제공
- 압축
- 하나의 IP 주소와 포트를 이용해 여러 개의 웹 서버 운영

### Caddy

[Caddy](https://caddyserver.com/)는 [리버스 프록시 기능을 내장](https://caddyserver.com/docs/proxy)하고 있는 웹 서버로, 인증서 등록 및 설치를 자동으로 해주기 때문에 굉장히 편하게 HTTPS 웹 서버를 운영할 수 있습니다. 또한 [Caddyfile](https://caddyserver.com/tutorial/caddyfile)이라는 간단한 문법의 설정 파일을 통해 웹 서버를 설정하도록 하고 있습니다. 아래는 리버스 프록시 설정을 한 Caddyfile 예제입니다.

```
# https://example.com URI로 들어온 요청을 http://localhost:3000 서버에 연결시킴
# http://example.com 쪽으로 들어온 요청은 https로 리다이렉트
example.com {
  proxy / localhost:3000 {
    # 리버스 프록시에 요청이 어떤 형태(IP, 프로토콜)로 왔는지를
    # 뒤쪽 서버에 별도의 헤더를 통해 전달
    transparent
  }
}

chat.example.com {
  proxy / localhost:4000 {
    transparent
    # 웹소켓 요청도 전달하기
    websocket
  }
}
```

Caddyfile을 작성한 뒤에 해당 폴더에서 `caddy` 명령을 통해 Caddy 웹 서버를 실행시킬 수 있습니다. 터미널이 꺼져도 계속 Caddy가 실행되게 하려면 아래의 명령을 실행하면 됩니다.

```bash
$ nohup caddy &
```

HTTPS를 사용하려면 먼저 DNS 설정이 되어 있어야 합니다. Route 53에서 먼저 DNS 설정을 한 뒤에 Caddy를 실행시켜 주세요.

### Reverse Proxy + Express

리버스 프록시를 통해 운영되는 Express 웹 서버가 IP 추적 기능이나 쿠키를 사용한다면 반드시 trust proxy 옵션을 설정해주어야 합니다. 자세한 사항은 [공식 문서](http://expressjs.com/ko/guide/behind-proxies.html)를 참고해주세요.
