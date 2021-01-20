# URLを変更する

URL初期値

    http://127.0.0.1:8000/  
    http://localhost:8000/


## 
mysite/urls.py の中身  
こんなのが書かれている

    from django.contrib import admin
    from django.urls import path

    urlpatterns = [
        path('admin/', admin.site.urls),
    ]

adminのURLについてはこの部分

    path('admin/', admin.site.urls),

sample.urls をインポートする行を追加。

    from django.contrib import admin
    from django.urls import path, include

    urlpatterns = [
        path('admin/', admin.site.urls),
        path('', include('sampleapp.urls')),
    ]

sampleapp フォルダ内にurls.py ファイルを作成し以下の2行を追加する

    from django.urls import path
    from . import views

これはpath 関数と、sampleapp アプリのすべてビューをインポートするという意味  

最初のURL パターンを追加する

    urlpatterns = [
        path('', views.post_list, name='post_list'),
    ]

post_list という名前のビューをルートに割り当てている  
なので、http://localhost:8000/もアクセスすると、行き先をview.post_list だとDjango に伝える  
name はビューを識別するために使われるURL の名前