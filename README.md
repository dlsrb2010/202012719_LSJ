#202012719 이상준
===
DAY6. 서비스 작성하고 사용하기
===

#### 개인별 서비스 작성

##### - REST 기반

##### - 통신 규약 작성(엑셀 혹은 README.md)

##### - github Organizations(IDU-SW/2020-1)에 Repositories 생성 후 올리기

##### - gitignore 작성 (node_modules 포함하지 말것)

##### - gitignore.io 참고

#### 팀원의 다른 서비스 사용하기

##### - 팀원의 서비스 다운로드

##### - 서비스 동작시키기

##### - 통신규약을 보고 서비스 사용해보기

##### - 사용 내역 3장 이상 캡쳐(요청/응답이 보이도록, 서로 다른 메소드와 URL)

--------------
### 🎈CONTENT🎈

##### - [음악 전체보기](#음악-목록-전체보기)

##### - [음악 상세보기](#음악-정보-상세보기)

##### - [음악 추가](#음악-정보-추가)

##### - [음악 삭제](#음악-정보-삭제)

##### - [음악 수정](#음악-정보-수정)


| 업무 구분 |        항목        |    URL     | METHOD |
| :-------: | :----------------: | :--------: | :----: |
|   목록    | 음악 목록 전체보기 |  /musics   |  GET   |
|   CRUD    | 음악 정보 상세보기 | /musics/ID |  GET   |
|           |   음악 정보 추가   |  /musics   |  POST  |
|           |   음악 정보 삭제   | /musics/ID | DELETE |
|           |   음악 정보 수정   | /musics/ID |  PUT   |

--------------

### 📃음악 목록 전체보기

#### 요청

|    업무     | 음악 목록 전체보기 |
| :---------: | ------------------ |
|     URL     | /musics            |
| 요청 메소드 | GET                |

#### 응답

| 컨텐트 타입 | JSON                                                         |
| :---------: | ------------------------------------------------------------ |
| 메세지 구조 | - id : 음악 ID<br />- title : 노래제목<br />- artist : 아티스트<br />- genre : 음악 장르<br />- date : 음악 발매일 |
|  메세지 예  | {<br/>    "data": [<br/>        {<br/>            "id": 0,<br/>            "title": "새로고침(Feat. 강민경 of 다비치)",<br/>            "artist": "박경",<br/>            "genre": "랩/힙합",<br/>            "date": "2020.03.18"<br/>        },<br/>        {<br/>            "id": 1,<br/>            "title": "겨울 끝",<br/>            "artist": "반하나, 하준석",<br/>            "genre": "발라드",<br/>            "date": "2019.03.02"<br/>        }<br/>    ],<br/>    "count": 2<br/>} |

--------------

### 📖음악 정보 상세보기

#### 요청

|     업무      | 음악 정보 상세보기                                           |
| :-----------: | ------------------------------------------------------------ |
|      URL      | /musics/ID                                                   |
|  요청 메소드  | GET                                                          |

#### 응답

| 컨텐트 타입 | JSON                                                         |
| :---------: | ------------------------------------------------------------ |
| 메세지 구조 | - id : 음악 ID<br />- title : 노래제목<br />- artist : 아티스트<br />- genre : 음악 장르<br />- date : 음악 발매일 |
|  메세지 예  | {<br/>    "id": 1,<br/>    "title": "빌런(Villain)",<br/>    "artist": "스텔라장",<br/>    "genre": "인디음악, 포크/블루스",<br/>    "date": "2020.04.07"<br/>} |

--------------

### 📋음악 정보 추가

#### 요청

| 업무          | 음악 정보 추가                                               |
| ------------- | ------------------------------------------------------------ |
| URL           | /musics                                                      |
| 요청 메소드   | POST                                                         |
| 콘텐트 타입   | application/json                                             |
| 메세지 구조   | - **title : 노래제목**<br />- **artist : 아티스트**<br />- genre : 음악 장르<br />- date : 음악 발매일 |
| 요청메세지 예 | { <br/> "title" : "10분 전",<br/> "artist" : "보라미유",<br/> "genre" : "댄스, 인디음악",<br/> "date" : "2020.03.30"<br/>} |

#### 응답

| 컨텐트 타입 | JSON                                                         |
| ----------- | ------------------------------------------------------------ |
| 메세지 구조 | - msg : 성공/실패 메세지<br />- data<br />-- id : 음악 ID<br />-- title : 노래제목<br />-- artist : 아티스트<br />-- genre : 음악 장르<br />-- date : 음악 발매일 |
| 메세지 예   | {<br/>    "msg": "SUCCESS : 다음 내용을 추가하였습니다.",<br/>    "data": {<br/>        "id": 3,<br/>        "title": "10분 전",<br/>        "artist": "보라미유",<br/>        "genre": "댄스, 인디음악",<br/>        "date": "2020.03.30"<br/>    }<br/>} |

--------------

### 🗑음악 정보 삭제

#### 요청

| 업무        | 음악 정보 삭제 |
| ----------- | -------------- |
| URL         | /musics/ID     |
| 요청 메소드 | DELETE         |


#### 응답

| 컨텐트 타입 | JSON                                                         |
| ----------- | ------------------------------------------------------------ |
| 메세지 구조 | - msg : 성공/실패 메세지<br />- data<br />-- id : 삭제된 음악 ID<br />-- title : 삭제된 노래 제목<br />-- artist : 삭제된 노래 아티스트<br />-- genre : 삭제된 노래 음악 장르<br />-- date : 삭제된 노래 발매일 |
| 메세지 예   | {<br/>    "msg" : "SUCCESS : 다음 내용이 삭제되었습니다.",<br/>    "data": {<br/>        "id": 2,<br/>        "title": "겨울 끝",<br/>        "artist": "반하나, 하준석",<br/>        "genre": "발라드",<br/>        "date": "2019.03.02"<br/>    }<br/>} |

--------------

### 🔧음악 정보 수정

#### 요청

|     업무      | 음악 정보 수정                                               |
| :-----------: | ------------------------------------------------------------ |
|      URL      | /musics/ID                                                   |
|  요청 메소드  | PUT                                                          |
|  콘텐트 타입  | application/json                                             |
|  메세지 구조  | - **title : 노래제목**<br />- **artist : 아티스트**<br />- genre : 음악 장르<br />- date : 음악 발매일 |
| 요청메세지 예 | { <br/> "title" : "겨울 끝",<br/> "artist" : "반하나, 하준석",<br/> "genre" : "발라드",<br/> "date" : "2019.03.02"<br/>} |

#### 응답

| 컨텐트 타입 | JSON                                                         |
| :---------: | ------------------------------------------------------------ |
| 메세지 구조 | - msg : 성공/실패 메세지<br />- data<br />-- id : 수정된 음악 ID<br />-- title : 수정된 노래 제목<br />-- artist : 수정된 노래 아티스트<br />-- genre : 수정된 노래 음악 장르<br />-- date : 수정된 노래 발매일 |
|  메세지 예  | {<br/>    "msg": "SUCCESS, 1번의 내용이 변경되었습니다.",<br/>    "data": {<br/>        "id": 1,<br/>        "title": "겨울 끝",<br/>        "artist": "반하나, 하준석",<br/>        "genre": "발라드",<br/>        "date": "2019.03.02"<br/>    }<br/>} |
