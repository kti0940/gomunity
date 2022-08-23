# 📌초보 개발자들의 커뮤니티, 거뮤니티

---

## 프로젝트 소개

![gomunity_og](https://user-images.githubusercontent.com/97969957/185279549-76daa3f9-50dc-4eb7-b412-2f9faec1c2b3.png)

- 거뮤니티는 초보 개발자들이 모여 거리낌없이 질문하고 답변하면서 어려운 점을 해소하기 위한 웹 프로젝트입니다.
- 개발자는 구글링을 통해 자신이 가지고 있는 이슈와 비슷한 케이스를 찾고 트러블 슈팅하게 되지만 초보 개발자는 익숙하지 않아 쉽지 않습니다. 스택오버플로우 또한 마찬가지입니다.
- 따라서 더 나은 개발자가 되기 위한 초석과 같은 커뮤니티가 있어서 성장을 할 수 있는 사이트가 필요할 것 같다는 저희 팀의 경험으로 구상하게 되었습니다.
- 사용자가 될 초보 개발자가 거뮤니티를 통해서 어떤 질문이라도 편하게 질문하고, 답변을 받아 해결하면서 그것을 스스로가 정리해 다음 스텝으로 나아갈 수 있도록 희망합니다.
- 개발 공부를 하면서 알게된 꼭 나와 같은 초보들에게 공유하고 싶은 팁을 게시하는 자료게시판또한 있어 누구나 초보였던 시절에 불편했던 일들을 해결했던 자료를 공유하여 쉽게 찾을 수 있는 레퍼런스가 되기를 희망합니다.

# 📌기술 스택

---

## 서버

<div style="display:flex">
    <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=Python&logoColor=white">
    <img src="https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=Django&logoColor=white">
<div>

## 데이터베이스

<img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=PostgreSQL&logoColor=white">

## 프론트엔드

<div style="display:flex">
    <img src="https://img.shields.io/badge/HTML5-e34f26?style=for-the-badge&logo=HTML5&logoColor=white">
    <img src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=CSS3&logoColor=white">
    <img src="https://img.shields.io/badge/Javascript-F7DF1E?style=for-the-badge&logo=JavaScript&logoColor=white">    
<div>

## 프로젝트관리, 배포

<div style="display:flex">
    <img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=Git&logoColor=white">
    <img src="https://img.shields.io/badge/Sourcetree-0052CC?style=for-the-badge&logo=Sourcetree&logoColor=white">
    <img src="https://img.shields.io/badge/Github-181717?style=for-the-badge&logo=Github&logoColor=white">
    <img src="https://img.shields.io/badge/Visual Studio Code-007ACC?style=for-the-badge&logo=Visual Studio Code&logoColor=white">    
<div>
<div style="display:flex">
    <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=Docker&logoColor=white">
    <img src="https://img.shields.io/badge/Amazon EC2-FF9900?style=for-the-badge&logo=Amazon EC2&logoColor=white">
    <img src="https://img.shields.io/badge/Amazon S3-569A31?style=for-the-badge&logo=Amazon S3&logoColor=white">
    <img src="https://img.shields.io/badge/Gunicorn-499848?style=for-the-badge&logo=Gunicorn&logoColor=white">
    <img src="https://img.shields.io/badge/NGINX-009639?style=for-the-badge&logo=NGINX&logoColor=white">
<div>

# 📌프로젝트 구조

---

## 프로젝트 아키텍쳐

![image](https://user-images.githubusercontent.com/97969957/185283041-45f4504d-e797-4714-9d7e-058568c20f8d.png)

### 서버

- 서버는 EC2 안에서 nginx,gunicorn/django,postgreSQL이 도커를 통해 이미지로 빌드되어 구축되어 있습니다.
- Lets Encrypt를 사용하여 443포트로 열린 HTTPS 도메인으로 배포되어 있습니다.
- 도메인은 Route 53을 사용하였습니다.

### 프론트엔드

- 프론트엔드는 S3를 통해 정적배포 되었습니다.
- AWS CloudFront으로 AWS SSL 인증서가 적용된 HTTPS 도메인으로 배포되어 있습니다.
- 도메인은 Gabia를 사용하였습니다.

## 개념적 / 논리적 ERD
![개념적ERD](https://user-images.githubusercontent.com/61997714/186041498-c5108c51-6bd9-4d8c-b1cd-b271fa9c32f8.png)

![Gomunity](https://user-images.githubusercontent.com/97969957/185282933-80713a8e-cdf6-47c4-ba20-ef985fddf0d0.png)

- 거뮤니티는 크게 세 가지로 나누어진 기능의 테이블로 작성되어 있습니다.
  - 회원 모델
  - 질의응답 게시글/답글/좋아요 모델
  - 자료게시판 게시글/답글/카테고리/좋아요 모델
    
## 트러블슈팅
<details>
<summary>DRF 시리얼라이저 데이터 리턴 과정 오류</summary>
<div markdown="1">
# 상황

- DRF의 시리얼라이저를 통해서 데이터를 리턴해주려고 했는데 문제가 발생했다.
- 시리얼라이저에 담아주고 싶은 데이터는 objects.all() 을 사용한 쿼리셋 데이터 형식이다

```python
.. 생략

class View(APIView):
	def get(self, request):
		notices = NoticeModel.objects.all()
		notice_serializer = NoticeSerializer(data=notices).data
		return Response(notice_serializer)
```

# 오류코드

- `Original exception text was: 'QuerySet' object has no attribute 'title'.`
- 쿼리셋 오브젝트(다수의 오브젝트)는 제목이라는 속성이 없다.
    - 왜냐하면 하나의 오브젝트에는 해당 속성이 있겠지만, 여러 개를 바라본다면 제대로 참조 할 수 없다

# 트러블슈팅

[[django] Serializer에 분명히 해당 필드가 있는데 없다고 하는 경우](https://dongza.tistory.com/20)

- 단일 오브젝트가 아닌, 여러 개의 오브젝트인 쿼리셋을 받아주려면 many=True 를 추가로 작성해주어야 한다고 한다.

# 해결

- 시리얼라이저로 보내주는 데이터가 여러 개의 오브젝트인 쿼리셋이었다
- 쿼리셋을 넘겨주기 위해서는 many=True 를 추가로 작성해주어야 한다
- 작성해주었더니 해결되었음

```python
.. 생략

class View(APIView):
	def get(self, request):
		notices = NoticeModel.objects.all()
		notice_serializer = NoticeSerializer(data=notices).data
		return Response(notice_serializer, many=True)
```
</div>
</details>

## 서비스 플로우

### 회원기능

![회원가입](https://user-images.githubusercontent.com/97969957/185279221-5abe2894-0fd2-4636-8023-a467a292a2d6.gif)

- 사용자는 거뮤니티의 게시글을 열람할 수 있습니다. 그러나, 작성/수정/삭제/좋아요 등의 기능은 로그인을 요구합니다.
- 사용자는 회원가입 페이지에서 아이디,비밀번호,닉네임,이메일을 입력하고 회원가입합니다.
  - 아이디,비밀번호,이메일은 작성조건이 있어 작성조건이 일치하지 않는다면 오류를 표시합니다.

![로그인 및 게시판](https://user-images.githubusercontent.com/97969957/185279234-26e622ee-b357-4830-9792-d0a63abe1336.gif)

- 사용자는 아이디 비밀번호를 입력하고 로그인합니다.
  - 로그인한 사용자는 DRF Simple JWT로 토큰이 브라우저 로컬 스토리지에 저장됩니다.
  - 사용자는 약 15분간 한 번 로그인한 상태를 유지하며, 새로고침을 통해서 토큰을 60일까지 저장합니다.

### 질의응답게시판

![게시글 등록](https://user-images.githubusercontent.com/97969957/185279026-1c6a22e1-b005-496e-977e-3940c4707a37.gif)

- 사용자는 질의응답게시판을 통해서 개발과 관련된 주제로 자유롭게 질문하고 답변할 수 있습니다.
- 사용자는 질의응답게시판에 작성된 글을 열람할 수 있습니다.
- 사용자는 질의응답게시판의 글 및 답변의 작성/수정/삭제/좋아요 기능은 로그인을 통해서만 접근할 수 있습니다.
- 사용자는 게시글 작성 버튼을 눌러 질문하고 싶은 내용을 담아 글을 작성합니다.
  - 해시태그를 작성하여 이 후 게시글을 추천하는 용도로 활용됩니다.
  - TOAST UI EDITOR가 적용되어 있어 마크다운 형식으로 글을 작성하거나 이미지를 업로드 할 수 있습니다.
- 사용자는 자신이 작성한 글에 대해 수정/삭제 권한이 있으며 버튼으로 표시됩니다.
  - 수정 버튼을 눌러 작성된 제목/해시태그/내용 등이 에디터 안에 표시되며 글을 수정할 수 있습니다.
  - 삭제 버튼을 눌러 작성한 글 레코드를 삭제합니다.
- 사용자는 게시글에 제목 밑의 좋아요 버튼을 클릭하여 좋아요 기능을 사용할 수 있습니다.
  - 좋아요 된 버튼은 모양이 변경되며, 다시 한 번 클릭하면 좋아요가 취소됩니다.
- 사용자는 게시글에 답글을 작성할 수 있습니다.
  - 텍스트를 입력하고 작성버튼을 눌러 답글을 작성할 수 있습니다.
- 사용자는 자신이 작성한 답글에 대해 수정/삭제 권한이 있으며 버튼으로 표시됩니다.
  - 수정 버튼을 눌러 작성된 내용이 인풋에 표시되며 답글을 수정할 수 있습니다.
  - 삭제 버튼을 눌러 작성한 답글 레코드를 삭제합니다.

![게시글추천](https://user-images.githubusercontent.com/97969957/185279067-0d0505ee-fea5-4667-ab82-bc58cbaf9043.gif)

- 사용자는 게시글을 조회 페이지에서 추천받기 버튼을 눌러 유사한 해시태그를 가진 게시글을 추천받을 수 있습니다.

### 자료게시판

![자료게시판](https://user-images.githubusercontent.com/97969957/185283883-96c75c91-1fb8-47a9-9d7d-4faf16956633.gif)

- 사용자는 자료게시판을 통해서 개발하면서 알게 된 팁을 글을 작성하여 공유할 수 있습니다.
- 사용자는 자료게시판의 글 및 답글의 조회가 가능합니다.
- 사용자는 자료게시판의 글 및 답글의 작성/수정/삭제/좋아요 기능을 로그인을 통해서 접근할 수 있습니다.
- 사용자는 게시글 작성 버튼을 눌러 질문하고 싶은 내용을 담아 글을 작성합니다.
  - 카테고리를 중 공용 및 특정 권한 전용 하나를 선택하여, 열람권한을 정합니다.
  - 해시태그를 작성하여 이 후 게시글을 추천하는 용도로 활용됩니다.
  - TOAST UI EDITOR가 적용되어 있어 마크다운 형식으로 글을 작성하거나 이미지를 업로드 할 수 있습니다.
- 사용자는 자신이 작성한 글에 대해 수정/삭제 권한이 있으며 버튼으로 표시됩니다.
  - 수정 버튼을 눌러 작성된 제목/해시태그/내용 등이 에디터 안에 표시되며 글을 수정할 수 있습니다.
  - 삭제 버튼을 눌러 작성한 글 레코드를 삭제합니다.
- 사용자는 게시글에 제목 밑의 좋아요 버튼을 클릭하여 좋아요 기능을 사용할 수 있습니다.
  - 좋아요 된 버튼은 모양이 변경되며, 다시 한 번 클릭하면 좋아요가 취소됩니다.
- 사용자는 게시글에 답글을 작성할 수 있습니다.
  - 텍스트를 입력하고 작성버튼을 눌러 답글을 작성할 수 있습니다.
- 사용자는 자신이 작성한 답글에 대해 수정/삭제 권한이 있으며 버튼으로 표시됩니다.
  - 수정 버튼을 눌러 작성된 내용이 인풋에 표시되며 답글을 수정할 수 있습니다.
  - 삭제 버튼을 눌러 작성한 답글 레코드를 삭제합니다.

# 버전 별 SA

---

## [ver.1.0]()

## [ver.1.1]()

## [ver.1.2]()

## [ver.1.2.1]()

## [ver.1.3]()

## [ver.1.4]()

# 이슈리포트
