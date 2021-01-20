# Viewを作る

Viewではアプリロジックを書く  
モデルに情報を要求し、テンプレートに渡す  

view.py ファイルに書くことになる  

以下を追加  

    def post_list(request):
        return render(request, 'sampleapp/post_list.html', {})
