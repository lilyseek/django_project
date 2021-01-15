# 웹 서버
웹 서버의 소프트웨어와 데이터(HTML, CSS, Images, JavaScript …)들을 저장하는 컴퓨터

인터넷에 연결되어 웹에 연결된 다른 기기들이 웹 서버의 데이터를 주고받을 수 있도록 함

# 프로젝트 생성

## 새 컨테이너 생성 / 설정

### goorm IDE에 접속하여 새 컨테이너 생성

> 이름: django_container 
> 소프트웨어 스택: Python 
> OS: Ubuntu 18.04 LTS![enter image description here](https://drive.google.com/file/d/18mFa71ECBETSN6bqbyAisKz63mz1IFUi/view?usp=sharing)

### 프로젝트 생성
```python
django-admin startproject config .
```

### config/settings.py 파일을 열어 ALLOWED_HOST = [] 부분을 ALLOWED_HOST = ['*'] 로 변경

```python
ALLOWED_HOSTS = ['*']
```

### 프로젝트를 실행한 후 웹 브라우저에 접속하여 정상 동작 확인
```python
python manage.py runserver 0:80
```
> URL과 포트는 **[메뉴]->[프로젝트]->[실행URL과 포트]** 에서 확인 가능

# 공통 앱 생성
```python
python manage.py startapp common
```
