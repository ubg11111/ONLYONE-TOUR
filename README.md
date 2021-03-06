# 스프링 프로젝트
  스프링 프레임워크를 사용하여 팀원들과 여행사이트를 만드는 것으로 제작
  6명을 인원으로하여 각 파트에 나눠서 작업진행하였습니다.
  작업기간은 약 한달정도 소요가 되었으며,
  기획 및 깃&깃허브를 이용하여 팀원과 프로젝트 공유
  DB설계하는 시간까지 포함되어 있습니다.
  
  그중 제가 구현한 부분에 대해서 GIF형식으로 소개드리며,
  어떤식으로 작업을 진행하였는지 정리하겠습니다.

## 스프링 프로젝트 구현 목록
* 로그인
* 회원가입
* 아이디/비밀번호 찾기
* 상품검색
* 관리자 메인페이지 / 관리자 로그인
* 개인정보 수정 및 탈퇴

## 기능 소개

1. 로그인

  ![로그인](https://user-images.githubusercontent.com/84007964/178645782-39e3b732-1764-47bb-9e8e-b5dab6b3f78a.gif)
  
  JSP, CSS , Javascript을 이용하여 화면단을 먼저 구성하였습니다.
  DB의 정보와 연결을 해야하기에 form 형식으로
  
  로그인정보를 넘겨주는 식으로 구현하였습니다.
  
  * 아이디저장의 경우 쿠기값을 이용하여 로그인이력이 확인되면 정보가 입력값에 남게 끔 구현하였습니다.
  
  해당 정보를 Controller로 넘겨주게되고 RequestMapping을 통해서 정보를 받은 후 로그인 Mybatis를 DB와 연동 후
  로그인을 구현하였습니다. 
  
##

2.회원가입

  ![회원가입](https://user-images.githubusercontent.com/84007964/178647341-89b18b49-f280-486b-b772-46d9e87f7f19.gif)
  
  회원가입을 클릭하는 경우 컨트롤러에 맵핑을 이용하여 뷰페이지로 회원가입창을 사용자에게 띄우게끔 먼저 구현하였습니다.
  
  이후 CSS , JavaScript , jQuery를 이용하여 뷰페이지를 구성하였고,
  
  ajax와 정규식을 이용하여 회원가입시 잘못된 입력값 DB베이스와 중복되는(아이디, 이메일, 휴대전화) 부분에 대해서 
  
  중복검사버튼을 만들었습니다.
  
  외 비밀번호, 휴대폰번호, 생년월일등 옳바른 유효값을 입력시 통과하게끔 정규식을 이용하여 제어하였습니다.
  
  
##

3. 찾기

  ![찾기](https://user-images.githubusercontent.com/84007964/178648019-cc04c2a1-5d96-43a6-b591-c75cadf8ff2b.gif)
  
  로그인페이지에서 JavaScript를 통해서 Modal창을 따로 구현하였습니다. 찾기 항목을 클릭하는 경우 Modal창이 show되어지고
 
  닫기를 클릭하는 경우 hide되어 숨겨지게 됩니다.
  
  찾기 항목에서는 유효한 조건을 입력하게되면 DB상 입력한 사용자의 정보를 토대로 원하는 조건을 찾게 끔 구현하였습니다.

  
##

4. 개인정보 수정
  
  ![개인정보수정](https://user-images.githubusercontent.com/84007964/178648402-b755a29c-2657-43ba-802d-f8b07cf4e1b3.gif)
  
  로그인 이후에 메인화면에서 마이메뉴 -> 개인정보수정을 통해서 접근하게 끔 구현하였습니다.
  
  사용자가 개인정보 수정을 클릭하게 되면 비밀번호를 입력하는 보안검사를 한번 더 진행합니다.
  
  이후 회원가입 페이지의 디자인과 비슷한 화면으로 개인정보 수정을 진행하게 끔 구현하였습니다.
  
  아이디,이메일,생년월일,성별 등은 변경불가능하게 마크업 및 자바스크립트를 통해서 제어하였습니다.
  
##

5. 회원 탈퇴

  ![회원탈퇴](https://user-images.githubusercontent.com/84007964/178648717-79c7f5c8-e3ac-485e-87ee-a94b71169149.gif)

  로그인 이후 마이메뉴 -> 회원탈퇴 클릭 시 회원탈퇴 창으로 이동하게 끔 구현하였습니다.
  
  개인정보수정과 동일하게 비밀번호를 한번 검사하고 비밀번호가 맞게 입력된 경우 최종적으로 회원탈퇴가 진행됩니다.
  
  회원탈퇴 이후 기존에 로그인된 세션값은 지워지게 구현하였습니다.
  
  
  
##

6. 검색구현
  
  ![검색구현](https://user-images.githubusercontent.com/84007964/178649628-2b0d59eb-8e44-417c-8958-b6c7b4042149.gif)
  
  검색 뷰페이지를 먼저 구성하였습니다.
  
  맵핑을 통해서 DB 패키지상품,호텔상품을 List형식으로 받고 model에 해당정보를 넘겨주었습니다.
  
  Mybatis DB like문을 사용하여 해당되는 정보를 데이터베이스로부터 받고 model Attribue값을 최종적으로 뷰페이지로 넘겨주었습니다.
  
  뷰페이지에서는 조건문을 통해서 입력된 값이 DB 등록된 상품이 있는 경우와 없는 경우로 제어하여 사용자에게 보여주는 화면을 구성하였습니다.
  
  
##

7. 관리자 로그인
  
  ![관리자로그인](https://user-images.githubusercontent.com/84007964/178650499-409c05d8-fb4a-4dbf-b3b2-06724600d9a4.gif)

  사용자 DB에 인증서 라인을 두고 관리자 아이디를 따로 생성하였습니다.
  
  따라서 사용자 홈페이지에서와 동일하게 관리자아이디로 로그인을 하는 경우 메인 뷰페이지에서 관리자만 보이는 관리자화면에 접근하게 끔 구현하였습니다.
  
    
##

8. 관리자 메인페이지
  
  ![관리자 메인화면](https://user-images.githubusercontent.com/84007964/178650664-0911e5ba-c2e0-422e-a41e-948896fc4457.gif)
  
  관리자 메인화면의 헤더 부분은 관리자 메인화면으로 이동하거나 로그아웃을 할 수 있는 메뉴바를 구성하였고,
  
  왼쪽 사이드는 메뉴바를 고정하여 필요한 메뉴를 토글형식으로 구성하였습니다.
  
  메인화면의 여행자 분포도 그래프는 외부 API를 커스텀하여 구성하였습니다.


##


9. 관리자 고객정보 관리

  ![관리자 고객정보](https://user-images.githubusercontent.com/84007964/178650925-f05311b8-659a-48af-8851-0d92d5732670.gif)

  왼쪽 사이드바 메뉴에서 고객관리 -> 고객정보를 통해서 관리자가 고객정보를 관리할 수 있는 라인을 구성하였습니다.
  
  헤더부분은 해당 페이지의 전체 가입자수가 몇 명인지 가져오게 끔 하였고, 관리자가 직접적으로 회원탈퇴도 진행할 수 있게 끔 구현하였습니다.
  
  또한 사용자수가 늘어남에 따른 페이징처리도 정리하였습니다.
  
  
  
  

