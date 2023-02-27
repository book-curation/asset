## API 명세서

https://app.gitbook.com/o/axqdgQk3sHmxILfmFEmI/s/apWnuggqW2ZGOpTu8XnG/api/book-curation-api/hashtag



### User API 설계

**[usersService]**

1. isIdExist() : 아이디 중복확인

1. findByID() : 아이디 일치 여부

2. hashPassword() : 비밀번호 암호화

3. checkPassword() : 비밀번호 일치 여부


4. create() : 유저 생성

5. resetPassword() : 비밀번호 업데이트

6. delete() : 유저 삭제 = 회원 탈퇴


### Book API 설계

**API 설계**

1. getBookByHashtagId()
  - hashtagId 존재 여부 확인 : hashtag service의 findbyid()
  - hashtagId로 hashtag-book 매핑테이블에서 bookId 받고 book 정보 호출

**[booksService]**

1. findById() : 책 존재 여부 확인 후 책 상세 정보 호출

1. recommendBooks() : 추천할 책 목록 호출

1. getBookByHashtagId() : hashtag id로 book list 전부 호출


### Phrase API 설계

**API 설계**

1. create
  - BookId 존재여부: booksService의 findById
  - UserId 종재여부: usersService의 findById
  - content 길이 제한: pipe validator 통해서 처리

1. get phrase by book id
  - BookId 존재여부: booksService의 findById

1. udate, delete phrase
  - bookId 존재여부
  - 작성한 user id 일치 여부

**[phraseService]**

1. create() : phrase 생성

1. getPhrase() : phrase 목록 불러오기

1. findById() : phrase id 존재 여부 확인 후 phrase 정보 호출

1. checkUserId() : user id 일치 여부 (phrase를 작성한 사람이 맞는지 확인)

1. update() : phrase 업데이트

1. delete() : phrase 삭제

1. recommendPhrase() : phrase 추천 목록



### Hashtag API 설계

**API 설계**

1. get hashtag by book id
  - BookId 존재 여부 확인 : Book service의 findby
  - bookId로 book entity 통해서 hashtag-book 매핑테이블 통해서 hashtag 정보 받아오기 -> hashtag 가져오기

2. delete
  - hashtag 존재여부
  - ~~userId 검증~~
  - 사용자가 작성한 hashtag 삭제 처리
  - hashtag에 연결된 user가 0일 경우 hashtag 삭제

**[hashtagService]**

1. create() : hashtag 생성(생성시 book, user랑 연결되어야함), 중복 생성 x

1. getHashtagByBookId() : bookId로 책에 달린 해시태그 전부 불러오기

1. findById() : hashtag id 존재 여부 확인 후 hashtag 정보 호출

1. ~~checkUserId() : user id 일치 여부 (hashtag 작성한 사람이 맞는지 확인)~~

1. delete() : hashtag 삭제

1. deleteHashtagByUser() : 사용자가 작성한 hashtag 삭제


### Curation API 설계

**API 설계**

1. create
  - userId, bookId 각 service의 findById
  - 생성

1. delete
  - findById로 찾고
  - 위 정보랑 userId 매칭 여부 확인
  - isPublic으로 공개 여부 확인
  - 삭제

**[curationsService]**

1. create() : curation 생성

1. getCurationList() : userId 맞는지 확인 후 호출

1. findById() : curation id로 정보 불러오기

1. update() : curation 업데이트

1. delete() : curation 삭제 

1. recommendCuration() : curation 추천 목록

