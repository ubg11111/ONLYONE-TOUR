# 스프링 프로젝트
  스프링 프레임워크를 사용하여 팀원들과 여행사이트를 만드는 것으로 제작
  6명을 인원으로하여 각 파트에 나눠서 작업진행하였습니다.
  작업기간은 약 한달정도 소요가 되었으며,
  기획 및 깃&깃허브를 이용하여 팀원과 프로젝트 공유
  DB설계하는 시간까지 포함되어 있습니다.
  
  그중 제가 구현한 부분에 대해서 GIF형식으로 소개드리며,
  어떤식으로 작업을 진행하였는지 정리하겠습니다.
  
  MVC패턴 구성상 코드양과 자바 클래스의 양이 좀 많다보니 핵심 일부만 구성하여 표기하였습니다.
  또한 DB설계는 MyBatis를 통해서 구성하였고, XML로 설정된 스프링기반이다보니
  모든 라이브러리 관련된 DI는 pom.xml에서 관리하고 있습니다.
  

## 스프링 프로젝트 구현 목록
* 로그인
* 회원가입
* 아이디/비밀번호 찾기
* 상품검색
* 관리자 메인페이지 / 관리자 로그인
* 개인정보 수정 및 탈퇴


##




## 기획 설계

회원 도메인 설계 일부
![image](https://user-images.githubusercontent.com/84007964/186063016-c76feb37-66b4-4006-b6d0-e27112ff4e10.png)

##

회원 DAO 설계 일부
![image](https://user-images.githubusercontent.com/84007964/186063095-2d756fde-eb59-40d5-902b-0f84b00d0b33.png)

##

회원 DB 설계 일부
![image](https://user-images.githubusercontent.com/84007964/186063274-761e3802-e195-4b8b-8d09-96b5e9a86784.png)


##

MyBatis 설계 일부
![image](https://user-images.githubusercontent.com/84007964/186064628-6832e83d-223c-421a-ac5e-ca71079e823a.png)


##



## 기능 소개

1. 로그인

  ![로그인](https://user-images.githubusercontent.com/84007964/178645782-39e3b732-1764-47bb-9e8e-b5dab6b3f78a.gif)
  ![image](https://user-images.githubusercontent.com/84007964/186063429-cfb7ac03-35d5-4176-95b3-e277a9323d7f.png)
  
  @RequestMapping("login_ok.do")
  파라미터로 id와 pwd를 받아주고, 로그인이 실패한 경우와 성공한 경우 조건을 통해 컨트롤러에서 제어후
  성공한 경우 사용자의 아이디의 세션값을 넘겨주는 방식으로 구현하였습니다.
  이후 세션값은 로그아웃을 진행하게되면 세션종료 형태와 연결하기 위하여 미리 값을 넘겨주는 식으로 설계했습니다.
  
  
##

2.회원가입

  ![회원가입](https://user-images.githubusercontent.com/84007964/178647341-89b18b49-f280-486b-b772-46d9e87f7f19.gif)
  ![image](https://user-images.githubusercontent.com/84007964/186063779-5770a91b-3e0d-4d2f-9fb2-2d31175bbe61.png)
  
  회원JSP에서 폼으로 넘어온 정보를 컨트롤러에서 제어 및 DB 정보를 받은 후 필요한 정보를 클라이언트(사용자)에게 넘겨주는 방식으로 구현 하였습니다.
  
  
##

3. 찾기

  ![찾기](https://user-images.githubusercontent.com/84007964/178648019-cc04c2a1-5d96-43a6-b591-c75cadf8ff2b.gif)
  ![image](https://user-images.githubusercontent.com/84007964/186064025-9964ad57-72ff-4d90-8bc4-b30f8012b87a.png)

  MemberDTO 참조변수에 사용자의 ID(DAO)를 요청 해서 받은 후 조건문으로 제어하였습니다.
  

  
##

4. 개인정보 수정
  
  ![개인정보수정](https://user-images.githubusercontent.com/84007964/178648402-b755a29c-2657-43ba-802d-f8b07cf4e1b3.gif)
  ![image](https://user-images.githubusercontent.com/84007964/186064736-3714edae-f72e-4726-afda-d3c2e5802a77.png)
  
  MyBatis 설계에서 update로 설계하여 회원가입과 비슷한 형태로 설계하였습니다. 클라이언트에게 회원가입과 비슷한 환경에서
  직접 입력하는 것이 좋다고 기획하고 구현하였습니다.
  
##

5. 회원 탈퇴

  ![회원탈퇴](https://user-images.githubusercontent.com/84007964/178648717-79c7f5c8-e3ac-485e-87ee-a94b71169149.gif)
  ![image](https://user-images.githubusercontent.com/84007964/186064947-8e6ec8be-ee41-45f5-9427-1c8dd9a44cb3.png)


  회원탈퇴는 로그인 이후에만 탈퇴할 수 있게끔 클라이언트에 내용을 보여주는 것으로 하고,
  회원탈퇴를 최종적으로 진행하게되면 기존 패스워드를 한번 더 체크하게 한 후.
  회원탈퇴가 완료되면 기존 세션값을 종료함과 동시에 DB상에서 데이터가 지워지게 끔 구현하였습니다.
  
  
  
##

6. 검색구현
  
  ![검색구현](https://user-images.githubusercontent.com/84007964/178649628-2b0d59eb-8e44-417c-8958-b6c7b4042149.gif)
  ![image](https://user-images.githubusercontent.com/84007964/186065157-52aa7590-8339-4962-bf66-4c5ca2614e32.png)

  검색은 메인페이지에서 검색을 하는 경우 List로 호텔과 여행상품 두 객체를 지정해두고
  각각 설계에 맞게 구현하여 클라이언트에게 제공하는 방식으로 구현하였습니다.
  
  
##

7. 관리자 로그인
  
  ![관리자로그인](https://user-images.githubusercontent.com/84007964/178650499-409c05d8-fb4a-4dbf-b3b2-06724600d9a4.gif)
  ![image](https://user-images.githubusercontent.com/84007964/186065580-b944996a-4213-41f1-99aa-ebbe50d3d835.png)

  
  JSP에서 스클립틀릿코드로 자바형식과 HTML형식을 종합하여 로그인 형식을 다르게 구현하였습니다.
  조건문에서 verify가 9로 해당되는 값의 아이디는 관리자 아이디로 따로 나뉘었으며, 해당 아이디로 로그인시
  관리자 페이지로 이동할 수 있는 네비바 구성을 따로 구현하였습니다.
    
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
  
  
  
  

