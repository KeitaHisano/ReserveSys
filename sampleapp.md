## アプリケーションの作成

sampleappというアプリを作成する場合  

    python manage.py startapp sampleapp

以下の構成になる  

    reservesys
    ├── db.sqlite3
    ├── manage.py
    ├── mysite
    │   ├── __init__.py
    │   ├── settings.py
    │   ├── urls.py
    │   └── wsgi.py
    ├── myvenv
    │   └── ...
    ├── sampleapp
    │   ├── admin.py
    │   ├── apps.py
    │   ├── __init__.py
    │   ├── migrations
    │   │   └── __init__.py
    │   ├── models.py
    │   ├── tests.py
    │   └── views.py
    └── requirements.txt

アプリを作成するとDjangoの設定を更新する必要がある

  setting.py  

    INSTALLED_APPS = [
        'django.contrib.admin',
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.messages',
        'django.contrib.staticfiles',
        'sampleapp.apps.SampleappConfig',  ← ココ
    ]

## ポストモデルの作成

models.pyにModelオブジェクトを定義する  
とりあえず、以下の内容に変更する

sampleapp/models.py

    from django.conf import settings
    from django.db import models
    from django.utils import timezone


    class Post(models.Model):
        author = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
        title = models.CharField(max_length=200)
        text = models.TextField()
        created_date = models.DateTimeField(default=timezone.now)
        published_date = models.DateTimeField(blank=True, null=True)

        def publish(self):
            self.published_date = timezone.now()
            self.save()

        def __str__(self):
            return self.title

## データベースにモデルのためのテーブル作成

    PS C:\reservesys> python manage.py makemigrations sampleapp
    Migrations for 'sampleapp':
      sampleapp\migrations\0001_initial.py
        - Create model Post

## 実行してみる

sampleapp/admin.py に以下を追加

    from django.contrib import admin
    from .models import Post

    admin.site.register(Post)

サーバーを立てる

    python manage.py runserver  

admin にアクセスしてみる

    http://localhost:8000/admin

管理者画面が表示される
