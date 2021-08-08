# 장고 ORM과 QuerySets 정리

## 장고 쉘

```bash
$ python manage.py shell
```

## Queryset

- 전달받은 모델의 객체 목록

- 데이터베이스로부터 데이터를 읽어오며 여러 동작을 할 수 있다

  - 모든 객체 조회

    ```bash
    $ from blog.models import Post
    $ Post.objects.all()
    ```


  - 객체 생성

    ```bash
    $ from django.contrib.auth.models import User
    $ User.objects.all()
    $ me = User.objects.get(username='sangjs')
    $ Post.objects.create(author=me, title='Sample title', text='Test')
    $ Post.objects.all()
    ```

  - 필터링

    ```bash
    $ Post.objects.filter(author=me)
    $ Post.objects.filter(title__contains='title')
    ```

  - 객체 추가

    ```bash
    $ post = Post.objects.get(title="Sample title")
    $ post.publish()
    ```

  - 게시일로 필터링

    ```bash
    $ Post.objects.filter(published_date__lte=timezone.now()) # 현재 
    ```

  - 정렬

    ```bash
    $ Post.objects.order_by('created_date')
    $ Post.objects.order_by('-created_date') # 내림차순
    ```

  - 쿼리셋 연결

    ```bash
    $ Post.objects.filter(published_date__lte=timezone.now()).order_by('published_date')
    ```

- 쉘 종료하기

  ```bash
  $ exit()
  ```

  
