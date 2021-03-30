### AUTH_USER_MODEL

> User를 나타내는데 사용하는 모델
>
> 기본 값은 auth.User > 커스텀 후 하는법은 '앱이름.User'(유저 클래스가 정의된 곳의 앱 이름)
>
> 프로젝트가 진행되는 동안 변경할 수 없음(마이그레이션 이후)
>
> #### AbstractBaseUser
>
> - 기본적으로  password, last_login제공
>
> - 자유도 높으나 다른거는 직접 작성해야함
>
> #### AbstructUser
>
> - 관리자권한을 갖춤
>
> 
>
> User와 연결되어있어서 커스텀 유저모델 사용하려면 써야하는 forms
>
> - UserCreationForm
> - UserChangeForm
>
> 
>
> #### 유저모델 참조하기
>
> - settings.AUTH_USER_MODEL
>   - 유저모델에 대한 왜래키
>   - models.py에서 유저모델을 참조할때 사용
