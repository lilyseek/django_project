# 프로젝트 생성

### 새 컨테이너 생성 / 설정

goorm IDE에 접속하여 새 컨테이너 생성

> 이름: django_container 
> 소프트웨어 스택: Python 
> OS: Ubuntu 18.04 LTS

### 프로젝트 생성
```python
django-admin startproject config .
```

config/settings.py 파일을 열어 ALLOWED_HOST = [] 부분을 ALLOWED_HOST = ['*'] 로 변경

```python
ALLOWED_HOSTS = ['*']
```

프로젝트를 실행한 후 웹 브라우저에 접속하여 정상 동작 확인

```python
python manage.py runserver 0:80
```
> URL과 포트는 **[메뉴]->[프로젝트]->[실행URL과 포트]** 에서 확인 가능

##
# 공통 앱 생성

```python
python manage.py startapp common
```
