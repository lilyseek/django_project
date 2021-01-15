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

# 부트스트랩 적용

**루트 디렉토리에 static 디렉토리 생성**
django_container/static

**static 디렉토리 등록**

config/settings.py에 제일 아래 부분에 코드 추가

``` python
STATICFILES_DIR = [
    os.path.join(BASE_DIR, 'static'),
]

```

