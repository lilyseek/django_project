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

https://django-container-zdiah.run.goorm.io/ 와 같이 메인 페이지로('') 요청이 들어왔을 때 **common/views 의 index**로 이동하게 설정

**config/urls.py 수정**
``` python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('', include('common.urls')),
    path('admin/', admin.site.urls),
]

```

**common/urls.py 생성**
``` python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.index)
]

```

**common/views.py 에 index() 함수 생성**
``` python
from django.http import HttpResponse


def index(request):
    return HttpResponse("main page")

```

# Template 

루트 디렉토리에 templates 디렉토리 생성 (django_container/templates)
templates 디렉토리 등록 (config/settings.py >> TEMPLATES >> DIRS 수정)
``` python
'DIRS': [os.path.join(BASE_DIR, 'templates')],
```



templates 에 기본 틀 페이지인 main.html 템플릿 생성 (django_container/templates/main.html)



# 부트스트랩 적용

### static 디렉토리 등록 ###

루트 디렉토리에 static 디렉토리 생성 (django_container/static)



config/settings.py에 제일 아래 부분에 코드를 추가하여 static 디렉토리 등록

``` python
STATICFILES_DIR = [
    os.path.join(BASE_DIR, 'static'),
]

```

<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta1/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-giJF6kkoqNQ00vy+HMDP7azOuL0xtbfIcaT9wjKHr8RbDVddVHyTfAAsrekwKmP1" crossorigin="anonymous">
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta1/dist/js/bootstrap.bundle.min.js" integrity="sha384-ygbV9kiqUc6oa4msXn9868pTtWMgiQaeYH7/t7LECLbyPA2x65Kgf80OJFdroafW" crossorigin="anonymous"></script>
<script src="https://code.jquery.com/jquery-3.5.1.slim.min.js" integrity="sha384-DfXdz2htPH0lsSSs5nCTpuj/zy4C+OGpamoFVy38MVBnE+IbbVYUew+OrCXaRkfj" crossorigin="anonymous"></script>
