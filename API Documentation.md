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

**[booksService]**

1. getBook() : 책 정보 호출

2. recommendBooks() : 추천할 책 호출
