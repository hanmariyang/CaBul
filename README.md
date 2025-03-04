# CaBul (사물인식 머신러닝 기반 카테고리 자동 분류 커뮤니티)

## 프로젝트


### CaBul

시연 영상 :

[https://youtu.be/Sg0NXNq49mw/](hhttps://youtu.be/Sg0NXNq49mw/)

프로젝트 일정 : 2022.10.17 ~ 2022.10.21

백엔드  Repository :[https://github.com/devjunseok/CaBul](https://github.com/devjunseok/CaBul)

S.A 링크 : [B-1팀 사물인식 서비스](hhttps://iodized-justice-c7c.notion.site/B1-56fb2a3285fe4d8cb53e1f9f5494d948)

## 1. 프로젝트 주제

### Pytorch, yolo를 활용하여 사용자가 업로드한 이미지를 사물인식 하여 자동으로 카테고리 생성 및 분류 하는 커뮤니티

사물인식 서비스를 접목한 간단한 커뮤니티 사이트

## 2. 기술 스택

- 백엔드
    - Python 3.10
    - Django 4.1.3
    - Pytorch 1.13.0

## 3. 싸지방 팀 팀원 및 역할

### 박준석 - [devjunseok - Overview](https://github.com/devjunseok)

팀장 / 프로젝트 기획 / 사이트 배포 / user 기능/ DB 모델링 / 머신러닝 코드 작성

### 노우석 - [WooSeok-Nho - Overview](https://github.com/WooSeok-Nho/)

팀원 / 프로젝트 기획 / user기능 / 날씨추천기능 / 포인트적립기능 / FrontEnd 제작,API연결

### 성창남 - [SungChangNam - Overview](https://github.com/SungChangNam)

팀원 / 프로젝트 기획 / communities 기능/ DB 모델링 / FrontEnd 제작,API연결

### 양기철 - [hanmariyang - Overview](https://github.com/hanmariyang)

팀원 / 프로젝트 기획 / products, recommend 기능 / 상품정보 크롤링 / DB모델링 / 추천 서비스 기능 / FrontEnd 템플릿 제작 및 API연결

### 이태겸 - [poro625 - Overview](https://github.com/poro625)

팀원 / 프로젝트 기획 / communites 기능, products 기능, weather 기능/크롤링/ DB 모델링 /태그 기능/ 검색 기능/상세보기 수정 및 삭제

## 4. 프로젝트 기능

### User 기능(회원가입/로그인 - simple jwt 사용)
- 회원가입 시, 비밀번호 유효성 검사 기눙
- 회원정보 CRUD 기능
- 소셜로그인 기능(카카오톡)
- 팔로우, 팔로워

### contents 기능 (게시글, 댓글, 사물인식)

- 게시글 CRUD
- 댓글 CRUD
- 게시글 검색
- Pytorch, yolo 사용 업로드한 이미지 사물인식
 
## 4-1. 트러블 슈팅

### 박준석

**문제 : 아이템 기반 협업 필터링으로 추천받은 영화를 DB에 접근해서 가져오지 못하는 상황 발생**

**원인 : 협업 필터링은 단순히 csv파일을 기준으로 영화를 추천해주기 때문에 db에 있는 영화와 연동을 하지 못하는 것이 원인**

**해결 : 리스트 축약식을 사용하여 추천된 영화를 장고 ORM에 적용하여 db에서 추출하여 해결 (recommend/views.py/TasteView)** 


### 양기철

**문제 : Serializer를 사용하지않고 ManyToMany 필드를 사용하는 대량 DB 저장시 각 필드끼리 연결되지 않는 문제 발생**

**원인 : 크롤링한 외부 데이터를 가져와서 DB에 저장시키려다보니 각각 알맞는 필드를 연결시키지 못함**

**해결 : ManyToMany 필드에 맞는 로직으로 저장하여 해결**
### 노우석

**문제 : 출석버튼을 눌렀을 때 db에 저장되어 있는 point가 증가하게 설계해놓았다.**

**다만 코드 로직 자체를 하루에 한번 포인트가 증가하게 할 수 있게 datetime.today()와 버튼을 클릭했을 때의 현재 날짜를 저장하는 click_time의 값을 비교해서 값이 같으면 기능이 작동하지 않게 작성해놓았는데 제대로 작동하지 않는 상황 발생**

**해결 : 두개의 값이 완전히 같게 보여도 타입이 달랐기 때문에 타입을 모델에서 변경해주어 같게 만들어주었더니 해결.**

### 이태겸

**문제 : 태그 기능을 게시글에 작성 시 여러개를 저장하더라도 각각 DB에 저장이 되도록 해야 하는데 각각 저장이 되지 않는 상황 발생**

**원인 : 원인은 Serializer 사용 시 ManyToMany 관계를 의식하지 않고 태그 기능을 구현하였기 때문에 생긴 현상.**

**해결 :ManyToMany 관계 Serializer를 사용하여 기존 Serializer를 수정 보완하여서 해결**

### 성창남

**문제 : 연동 하여 관리자가 신고 게시글 삭제 기능 구현 할 때 백엔드 정보가 프로트엔드에 구현되지 않은 오류가 발생 하는 문제가 발생. 처음에는 await fetch 만 사용 하여 원치않는 정보도 같이 들어와서 오류 발생.**

**해결 : 이중 반복문 을 활용하여 해결.**


## 5. 와이어프레임

[https://www.figma.com/file/hgtTToRaWbfP87GfNvHaMa/Off_the_Outfit?node-id=0%3A1&t=xw7FNe87Jr8IecaC-1](https://www.figma.com/file/hgtTToRaWbfP87GfNvHaMa/Off_the_Outfit?node-id=0%3A1&t=xw7FNe87Jr8IecaC-1)

![https://user-images.githubusercontent.com/111295065/207312359-91bb78a9-c108-4897-8cc3-e0cbb1f00cd0.png](https://user-images.githubusercontent.com/111295065/207312359-91bb78a9-c108-4897-8cc3-e0cbb1f00cd0.png)

## 6. API 명세서

[off_the_outfit (getpostman.com)](https://documenter.getpostman.com/view/24913558/2s8YzWRfo4)

## 7. DB 설계 ERD

![https://user-images.githubusercontent.com/111295065/207309475-759e6e8d-8265-4c49-8c8f-9f83478c329d.png](https://user-images.githubusercontent.com/111295065/207309475-759e6e8d-8265-4c49-8c8f-9f83478c329d.png)
