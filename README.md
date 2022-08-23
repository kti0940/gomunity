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
  
## 프로젝트를 통한 성장 목표

- ERD 구성에 항상 어려움을 느꼈었기에 개념적, 논리적, 물리적 ERD를 직접 Drawio에 그려가며 익혀갈 수 있도록 진행 했습니다.
- DRF와 Serializer등 부족했던 이해도를 높이고자 노력했습니다. (Custom Validate)
- Serializer를 활용하여 MethodField를 통해 원하는 데이터 값이 리턴해줄 수 있도록 진행하였습니다.
- JWT를 활용하여 토큰기반의 로그인 기능에 대한 이해도를 높이고자 했습니다.
- 커뮤니티 게시판이라는 기획의도는 가장 기본이되는 CRUD에 중점을 잡고자 기획되었기에, 게시글 CRUD를 반복적으로 작성하며 학습했습니다.
- 공식문서 참조를 통해 예제를 이해하고 프로젝트에 녹일 수 있도록 팀원들과 함께 노력하였습니다.
  
## 핵심기능

- [Serializer 활용 회원가입](https://github.com/kti0940/gomunity/blob/ee64543807ae13ed30f9a89c12044ec36dd9e883/user/views.py#L17)

- [JWT Claim Custom](https://github.com/kti0940/gomunity/blob/ee64543807ae13ed30f9a89c12044ec36dd9e883/user/jwt_claim_serializer.py#L1)

- [Serializer MethodField를 통해 원하는 데이터 조회](https://github.com/kti0940/gomunity/blob/ee64543807ae13ed30f9a89c12044ec36dd9e883/qna/serializers.py#L20)

- [Serializer 활용 게시판CRUD](https://github.com/kti0940/gomunity/blob/ee64543807ae13ed30f9a89c12044ec36dd9e883/qna/views.py#L44)

- [게시글, 답글 좋아요 기능](https://github.com/kti0940/gomunity/blob/ee64543807ae13ed30f9a89c12044ec36dd9e883/qna/views.py#L148)

- [공식문서를 활용한 SearchView](https://github.com/kti0940/gomunity/blob/ee64543807ae13ed30f9a89c12044ec36dd9e883/qna/views.py#L141)
    
## 프로젝트 트러블슈팅
<details>
<summary>📌DRF 시리얼라이저 데이터 리턴 과정 오류</summary>
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
	
<details>
<summary>📌DRF 시리얼라이저 새로운 필드 생성시 검증 통과 오류</summary>
<div markdown="1">

# 상황

- 질문글 상세 조회 뷰에서 특정 질문 글과 답글까지 출력하기 위해서 시리얼라이저에 코드를 적어주었다.

```python
from rest_framework import serializers
from .models import QnAQuestion as QnAQuestionModel, QnAAnswer as QnAAnswerModel

class AnswerSerializer(serializers.ModelSerializer):
	class Meta:
		model = QnAAnswerModel
		fields = "__all__"

class QuestionSerializer(serializers.ModelSerializer):
    answer = AnswerSerializer(many=True, source="qnaanswer_set")
    class Meta:
        model = QnAQuestionModel
        fields = "__all__"
```

- 문제는 질문글을 작성하는 뷰에서 발생했다. 질문글을 작성할 때 제목과 내용을 입력받아 데이터베이스에 저장해야 하는데, 갑자기 웬 answer를 필수 값으로 받아야만 한다는 것이다!
- 엥? 그럴리가 하면서 계속 찾았지만 오류가 어디서 뜨는 지 좀처럼 알 수 없는 상황!

```python
def post(self, request):
        question_serializer = QuestionSerializer(data=request.data)
        if question_serializer.is_valid():
            question_serializer.save(user=self.request.user)
            return Response({"message":"질문글 작성에 성공했다북!"})
        else:
            return Response({"message":"질문글 작성에 실패했다북..."})
```

# 코드

`{'answer': [ErrorDetail(string='이 필드는 필수 항목입니다.', code='required`

- answer라는 값을 입력할 때 필수로 받아야 한다는 뜻이었다. 질문글을 작성한 뒤에나 답글을 작성할 수 있는데 말이다…

# 트러블슈팅

- 위의 오류코드 조차도 볼 수 없었던 상황에서 오류를 찾기 위해 가장 먼저 한 것은 시리얼라이저가 제대로 검증되었는지 부터 파악할 필요가 있었다.
- 시리얼라이저가 오류가 있는 지 보기 위해서 `print(question_serializer.errors)` 코드를 else 구문에 작성하여 검증이 통과하지 않는다면 오류를 보여주도록 했다.
- answer 값은 조회를 위해서만 필요한건데, 작성할 때는 무시하게 할 수는 없나 하고 고민하면서 두 가지의 방법을 생각해냈다.
1. 시리얼라이저를 새로 써준다
    - 먼저 생각난 방법이지만 왠지 이렇게 하고 싶지는 않다. 케이스가 생겨날 때마다 시리얼라이저를 계속 만들어줘야 한다니..
2. read_only 옵션을 넣는다
    - 읽기만 가능하게 한다면 작성할 때는 자연스럽게 무시하지 않을까 하고 작성해보기로 했다

# 해결

read_only=True를 쓰면 조회에는 사용하고, 작성에는 사용하지 않는다. 읽기 옵션이기 때문에 시리얼라이저 검증을 거치지 않는다!

```python
from rest_framework import serializers
from .models import QnAQuestion as QnAQuestionModel, QnAAnswer as QnAAnswerModel

class AnswerSerializer(serializers.ModelSerializer):
	class Meta:
		model = QnAAnswerModel
		fields = "__all__"

class QuestionSerializer(serializers.ModelSerializer):
    answer = AnswerSerializer(many=True, source="qnaanswer_set", **read_only=True**)
    class Meta:
        model = QnAQuestionModel
        fields = "__all__"
```

```python
def post(self, request):
        question_serializer = QuestionSerializer(data=request.data)
        if question_serializer.is_valid():
            question_serializer.save(user=self.request.user)
            return Response({"message":"질문글 작성에 성공했다북!"})
        else:
						**print(question_serializer.errors)**
            return Response({"message":"질문글 작성에 실패했다북..."})
```

</div>
</details>

<details>
<summary>📌모델 CASCADE, SET NULL 충돌</summary>
<div markdown="1">

# 상황

- 배포 후 사용자 피드백을 받던 도중 500 error를 뱉으며 게시글 리스트 조회가 전부 되지 않았다
- 메인페이지는 곧 얼굴인 상황에서 제일 큰 문제를 직면해서 적잖이 당황했다
- 이유를 찾아보니 질문글의 모델을 구성할때 질문글과 답변, 좋아요 모델등이 set null 과 CASCADE로 혼용하여 설계한 상태였고, 이는 초기 테스트코드를 작성함에 있어서 CASCADE는 통과를 하지 못하고 set null은 통과가 되었기에 간과하고 지나간 부분이 우리의 발목을 잡았다
- 로그를 확인하며 추측한 바 현재 생긴 오류는 유저가 삭제한 게시글에 답변과 좋아요가 남아있는 상태에서, set null값에 의해 존재하지 않는 글에 댓글과 좋아요값을 찾으면서 발생한 에러라고 추측하고 디버깅에 들어갔다

# 트러블 슈팅

- 금번 데이터베이스는 postgresql를 통해 구축을 하였기에 gui를 통해 db에 접근하여 set null 데이터를 삭제하려 시도하였으나 postgresql failed timeout expired 해당 오류를 뱉으면서 접속이 되지 않았다
- 구글링을 통해 확인해보니 보안그룹에 관한 이슈인것같다는 글이 나왔고 AWS를 접속하여 확인해보니 보안그룹 설정에 postgresql은 설정이 되어있지 않았다
- 인바운드 규칙에 PostgreSQL을 추가해주었고 포트는 5432포트로 규칙을 열어주었다

![Untitled](https://user-images.githubusercontent.com/61997714/186050692-bea7f1e1-3361-49a4-b73a-5f7df8e06b7d.png)

- 이후 서버 배포한 IP와 유저명, 패스워드로 접근하니 접근에 성공할 수 있었고, postgresql에서 set null 데이터들을 삭제하며 상황을 해결 할 수 있었다

</div>
</details>
	
<details>
<summary>📌urls.py path 경로 오류 (Reverse for 'urlname' not found)</summary>
<div markdown="1">

# 🌧상황

- 테스트 코드 작성을 위해 [urls.py](http://urls.py) 에 path 경로에 지정해둔 name을 활용하여 reverse를 통해 해당 경로를 불러오던 중 ‘Reverse for ‘urlname’ not found’라는 오류를 만나게 되었다
- 기존에 user앱에서 테스트 코드를 진행했을 땐 name을 활용하여 reverse를 지정하여 아무런 문제가 없었기에 새로운 앱에서도 문제가 발생하리라고는 생각하지 못했는데 꽤나 당황스러웠다. 구글링을 통해 일단 기본 [urls.py](http://urls.py) 에 앱네이밍을 별도로 해주었고, reverse 내에도 앱네이밍을 연관지어 지정해주어 해결은 하였는데 user앱에서 처럼 별도로 앱네이밍을 지정해주지 않아도 잘 동작하는 코드들이 있어서 이유를 알고자 트러블 슈팅을 시도하게 되었다 (일명 왜 돼? 를 해결하기 위한 케이스)

# 🛠오류코드

```bash
Reverse for 'notice' not found. 'notice' is not a valid view function or pattern name.
```

# 🚀트러블슈팅

- 처음 시도해본 것은 네이밍의 문제가 아닐까 하여 list_notice 의 네임을 임의로 abc로 변경하여 진행해보았으나 마찬가지로 동일한 오류가 났다
- 네이밍 문제는 아니라고 판단, 기존의 코드를 주석 처리 한 채 user app에서 진행한 것과 같이 동일하게 코드를 구성하여 진행 해보았다

```python
urlpatterns = [
    path('webmaster/', include('webmaster.urls')),
    # path('webmaster/', include(('webmaster.urls','webmaster'), namespace='webmaster')),
]
```

- 그러자 기존의 오류 코드가 사라지고 잘 진행되는 것을 확인하게 되었는데, 생각해본 바 모종의 이유로 ‘visual studio상의 일시적인 에러 혹은 코드 사이에 눈에 보이지 않는 공백 같은 것이 존재했을 확률이 있었다’ 라고 잠정적으로 결론을 짓고 트러블 슈팅을 마치게 되었다

# 👻느낀점

- 이틀동안 고생한것 치고는 사실상 왜 돼? 에서 출발했던 트러블슈팅이 이건 또 왜 돼? 로 끝나게 되었다, 그래도 문제를 끊임없이 파고들고 해결한 우리 팀원에게 칭찬해💚
</div>
</details>
	
<details>
<summary>🐳 도커 numpy install 오류</summary>
<div markdown="1">

# 상황

---

- 도커 빌드를 통해 도커 컨테이너에 numpy를 설치하려 시도했으나 pip install 관련된 오류가 발생했다
- pip install 이후 numpy 설치 과정에서 3~40분정도의 설치를 계속 시도하고있었고 결국 마지막엔 장문의 에러를 띄우며 설치가 진행되지않았다.

```python
ERROR: Failed building wheel for numpy
Failed to build numpy
```

# 트러블 슈팅

---

### 시도 1

- 구글링을 통해 확인해보니 M1 맥이나 윈도우등 특정 환경에 국한되어 나타나는 에러는 아니고 pip 버전이 낮을 때 발생할 수 있는 에러라는 글을 보게 되었고 pip 를 업그레이드 한 후 재시도를 하였다

```python
pip install --upgrade pip
```

- 그러나 결과는 마찬가지로 numpy 설치가 진행되지 않았다

### 시도 2

- 검색 후 현재 빌드하고있는 도커파일의 파이썬 버전은 python:3.8-alpine이였고 동일한 문제를 겪고있는 글을 확인하였고 알파인에서 numpy등을 빌드하는것은 용량에 문제가 된다는 것을 확인했다
- Docker file에 아래와 같은 명령어를 통해 일부 캐시를 비워내며 진행하는것인가? 라고 생각했고 진행을 해보았다

```python
Run apk --no-cache add musl-dev linux-headers g++
```

- 결과는 마찬가지로 동일하게 실패했다

### 시도 3

- 2번의 시도와 함께 numpy의 버전이 현재 python 3.8.6과 충돌이 발생하는것은 아닐까? 라는 생각이 들었다
- requirements 를 통해 numpy 를 인스톨하지 않고 직접 버전을 지정하여 진행해보기로 했다

```python
pip install numpy==1.19.1
```

- 결과는 실패했다

# 해결

---

### 시도 4

- dockerfile 빌드시 2번의 문제처럼 alpine과정에서 오류를 많이 겪는 사람들을 보게되었다
- 설치가 전혀 불가능한것은 아니였지만 이문제를 해결하기위해 8시간이상의 트러블슈팅을 진행하고있던 찰나였기에 조금 우회할 필요가 있었다
- 아래의 레퍼런스를 읽게되었고 alpine → buster 로 변경을 시도해보았다

[Alpine, Slim, Stretch, Buster, Jessie, Bullseye, Bookworm - What are the Differences in Docker...](https://medium.com/swlh/alpine-slim-stretch-buster-jessie-bullseye-bookworm-what-are-the-differences-in-docker-62171ed4531d)

```python
# FROM python:3.8-alpine
# ENV PYTHONDONTWRITEBYTECODE=1
# ENV PYTHONUNBUFFERED=1

# RUN apk update
# RUN apk add build-base python3-dev py-pip jpeg-dev zlib-dev libpq-dev
# # RUN apk --no-cache add build-base python3-dev py-pip jpeg-dev zlib-dev libpq-dev gcc gfortran musl-dev linux-headers g++ libffi-dev openssl-dev

# COPY requirements.txt /usr/src/app/

# WORKDIR /usr/src/app
# RUN pip install -r requirements.txt

# COPY . /usr/src/app/

FROM python:3.8-buster
ENV PYTHONDONTWRITEBYTECODE=1 
ENV PYTHONUNBUFFERED=1 
RUN apt-get update -y 
RUN apt-get upgrade -y 
RUN apt-get install -y ffmpeg libgl1-mesa-glx 
COPY requirements.txt /usr/src/app/ 
WORKDIR /usr/src/app 
RUN pip install -r requirements.txt 
COPY . /usr/src/app/
```

- 결과는 numpy가 잘 설치되었으며 이로 인해 게시물 추천 기능을 배포시에도 사용할 수 있게 되었다

<aside>
💡 잠정결론 : 경량화 버전인 alpine 아닌 buster버전을 사용함으로 용량에 대한 문제를 해결했다 라고 생각한다

</aside>

- 이 부분에 대해선 추후 Docker에 대한 딥한 공부를 통해 더 보충할 계획이다

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
