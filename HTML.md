# HTML

> Hyper Text Markup Language
>
> - 웹페이지를 작성하기 위한 언어
> - 웹컨텐츠의 구조를 정의



> 구조
>
> - Head
>   - 해당 문서의 정보를 담고 있다.(제목, 문자 인코딩)
>   - 외부 로딩파일 지정도 할 수 있다. (`link` 태그 이용)
> - body
>   - 브라우저 화면에 실질적으로 나타나는 정보
> - DOM tree  : 부모관계, 형제관계
> - 요소(element) : 태그와 내용으로 구성
>   - 태그별로 사용하는 속성은 다르다.
>   - 시멘틱 태그 : 의미론적 요소를 담은 태그
> - 그룹 컨텐츠 : `p, hr, ol, ul, pre, blockquote, div`
> - 텍스트 관련요소 : `a, b, i, span, img, em, strong`
> - 테이블 관련 요소 : `tr, td, th, thead, tbody, tfoot, caption, colspan`
> - `form` 태그
>   - 입력받은 데이터와 함께 서버에 요청해 주는 태그
>   - `action` : 요청하는 서버의 주소를 설정하는 속성
>   - `input` : 다양한 타입을 가지는 입력데이터 필드  설정할 수 있음.
>     - `text, checkbox, radio, range, date`....
>     - `name`(데이터를 담을 이름, 변수명), `placeholder`, `required`, `disabled`, `autofocus` ....
>     - `label tag` : 서식의 입력의 캡션/이름표 같은 역할, `input` 의 `id` 값과 연결





> `<p>` : paragraph
>
> `pre` : 문장의 그대로의 모습을 보여주고싶을 때
>
> `<blockquote>` : 블럭
>
> `<div>` : 블럭으로 공간을 나누고 싶을 때
>
> `<a>` : 하이퍼링크
>
> `<b> vs <stront>` : 굵게, 스트롱의 시멘틱
>
> `<i> vs <em>` : 기울이기
>
> `<span>` : 인라인
>
> `<br>` : 줄바꾸기
>
> `<img>` : 이미지
>
> `<tr>` : 테이블
>
> `<td>` : 테이블 속에 한칸
>
> `<th>` : 작은 머릿말
>
> `<thead>`  : 
>
> - **`<form>` (서버에서 처리될 데이터를 제공하는 역할) 의 기본속성** 
>
>   - `action` : 요청할 주소 (입력된 데이터와 함께)
>   - `method` : http method에 대한 내용  get/post 에 대한 내용!! *매우 중요*
>





# css

> 스타일 레이아웃 등을 표시하는 방법을 저장하는 언어



> 적용 방법
>
> - 인라인 방식 : 관리하기 힘듦. 테스트용
> - 내부 참조 : `<style>` 태그 사이에 css 문법을 사용하는 방식. 모든 html에 적용할 수 없다.
> - 외부참조 : `<link>` 태그 에 css파일 경로를 명시해서 사용하는 방식 유지보수가 수월
>
> 선택자
>
> - 특정한 요소를 선택하기 위해서 필요
>
> - 기초선택자
>
>   - 전체선택자(*) 요소(element)선택자
>   - 아이디선택자, 클래스 선택자, 속성선택자
>
> - 고급 선택자
>
>   - 자손선택자 : 띄워쓰기로 구분, 하위의 모든 요소
>
>     `article p { color: red; }`
>
>   - 자식 선택자 : `>` 로 구분, 바로 아래의 요소만 해당
>
>     `article > p { color: blue; }`
>
>   - 형제 선택자 :  `~` 로 구분, 같은 계층(레벨)에 있는 요소
>
>     `p ~ section { color: green; }`
>
>   - 인접형제 선택자 : `+` 로 구분, 바로 붙어있는 형제요소
>
>     `section + p { color: orange; }`
>
> 적용 순서
>
> 1. `!important`
> 2. `inline style`
> 3. id 선택자 >  class선택자 > 요소선택자 > 코드순서
>
> CSS상속
>
> - 상속되는것 : text 관련 요소(font color text-align), opacity, visivility
> - 상속되지 않는것 : box model 관련 요소 (w, h, p, m, border), position 관련
>
> CSS 단위
>
> - px : 픽셀단위
> - % : 퍼센트 단위 기준되는 사이즈에서의 배율
> - em(상속받는 사이즈에서의 배율) / rem(root size 의 배율)
> - vh, vw 화면 사이즈를 기준으로 높이나 너비를 지정할 수 있다.
> - 색상표현 단위
>   - HEX (#000, #000000)
>   - RGB / RGBA
>   - 색상명
>   - HSL(명도, 채도, 색조) 잘 사용하지 않음
>
> Box model
>
> - margin : 바깥 여백
> - border : 테두리 영역
> - padding : 내부 여백
> - content : 글 이미지 등 실제 요소
>
> Box-sizing
>
> - content-box : 기본값, width의 너비는 content영역을 기준으로 잡는다.
> - border-box : width의 너비를 테두리를 기준으로 잡는다.
>
> 마진 상쇄
>
> - 수직간의 형제요소에서 주로 발생.
> - 해결 : 마진을 큰사이즈만 적용
> - 해결2 : padding을 이용한다.
>
> Display
>
> - block : 가로폭 전체를 차지한다.
>   - div, ul, ol, p, hr, form
>   - 수평정렬 margin auto 사용
> - inline : content의 너비만큼 가로폭 차지.
>   - width, heightm, margin-top, margin-botton 지정할 수 없다.
>   - line-height로 위아래 간격 조정.
> - inline-block : 높이와 너비지정가능한 인라인블럭
> - none : 화면에서 완전히 없애버림.
>   - visibility: hidden : 보여주지만 않을뿐 공간은 차지하고 있음.
>
> CSS position
>
> 