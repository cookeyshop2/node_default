# node.js default

> 사용중인 노드 프로젝트의 초기 시작 설정들을 모아놓은 Repository

### Express

- [참고 문서 : express-generator - Node.js + Express 프로젝트 생성하기](https://jistol.github.io/nodejs/2017/09/07/express-generator/)

```
npm install
```


```javascript
{
  "name": "node_test",
  "version": "1.0.0",
  "description": "",
  "main": "app.js",                                                                                    
  "scripts": {
    "start" : "nodemon app", # start 수정
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```

Express와 자주 사용하는 라이브러리들 (파서, 로거 등)을 함께 셋업해준다.
기본 포트는 3000(.env에서 설정)
 
```javascript
const path = require("path");
const express = require('express');
const morgan = require('morgan');
const cookiParser = require('cookie-parser');
const session = require('express-session');
const dotenv = require('dotenv'); // 환경 변수 설정용
//설치한 미들웨어 및 모듈  불러오기

dotenv.config();
const app = express();
app.set('port',process.env.PORT || 9000);
//app.set('정

- [참고 문서 : Travis CI, AWS CodeDeploy, Docker 로 배포 자동화 및 무중단 배포 환경 구축하기 - (1)](https://velog.io/@jeff0720/Travis-CI-AWS-CodeDeploy-Docker-%EB%A1%9C-%EB%B0%B0%ED%8F%AC-%EC%9E%90%EB%8F%99%ED%99%94-%EB%B0%8F-%EB%AC%B4%EC%A4%91%EB%8B%A8-%EB%B0%B0%ED%8F%AC-%ED%99%98%EA%B2%BD-%EA%B5%AC%EC%B6%95%ED%95%98%EA%B8%B0)


### AWS (적용 예정)

Lambda 적용 예정

- [참고문서 : AWS Lambda 기초 개념 및 간단 사용](https://cumulus.tistory.com/11)

