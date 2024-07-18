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
//app.set('port,포트) : 서버가 실행될 포트 설정

// view engine setup
app.set("view engine", "ejs");
app.set("views", path.join(__dirname, "views"));

app.use(morgan('dev'));
app.use('/',express.static(path.join(__dirname, 'views')));
app.use(express.json());
app.use(express.urlencoded({ extended: false}));
app.use(cookiParser(process.env.COOKIE_SECRET));
app.use(session({
    resave: false,
    saveUninitialized: false,
    secret: process.env.COOKIE_SECRET,
    cookie: {
        httpOnly: true,
        secure: false,
    },
    name: 'session-cookie',
}));

app.use((req, res, next) => {
    console.log('모든 요청에 다 실행됩니다.');
});

```


### PM2, nodemon
노드 프로세스 관리 도구(PM2는 global로 설치해서 사용)

현재 nodemon 사용중

```javascript
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "nodemon app"
  }

```

### Sequelize

- ORM of Javascript

```
npm i sequelize mysql2
npm i -g sequelize-cli
sequelize init
```

### Mocha(적용 예정)

- 동기 / 비동기 각 경우에 대한 단위 테스트
- Transaction Rollback (적용 예정)
- Mocking (적용 예정)

```javascript
const assert = require('assert');
const userRepository = require('../../persistence/userRepository');

describe('userRepository', () => {
    it('should return 2 elements when call userCategories', function (done) {
        userRepository.getUsers().then((val) => {
            assert.strictEqual(val[0].id, 1);
            assert.strictEqual(val[0].name, '테스터');
            done();
        })
    });
});
```

### CI & CD & AWS (적용 예정)

- [참고 문서 : Git Lab+Teamcity+Docker+AWS로 CI/CD 구축하기](https://jiseok-woo.tistory.com/19)

- [참고문서 : AWS Lambda 기초 개념 및 간단 사용](https://cumulus.tistory.com/11)


