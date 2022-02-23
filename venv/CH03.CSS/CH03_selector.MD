# CSS

```buildoutcfg
선택자{속성: 값;} - 스타일(CSS)을 적용할 대상 (Selector)
    ✔ 선택자 : html의 어느부분에 적용될 것 인지
    ✔ 속성: 값 : ex) color :red;
    
ex)
div{
    color: red; 
    margin(요소외부여백): 20px;
}

div : 태그 선택자 
```

## 선택자 -기본
```buildoutcfg
✔ 전체선택자
ex)
    *{
        color: red;
    }    
    * : 모든 요소를 선택

✔ 태그선택자
ex)
    li{
        color: red;
    }
    li : 태그이름이 li인 요소 선택

✔ 클래스선택자
ex)
    -html-
    <div>
        <ul>
            <li>사과</li>
            <li>딸기</li>
            <li class="orange">오렌지</li>
        </ul>
        <div>당근</div>
        <p>토마토</p>
        <span class="orange">오렌지</span>
    </div>
    -css-
    .orange{
        color: red;
    }
    .orange : 클래스 속성값이 orange 인 요소 선택 
✔ 아이디선택자
ex)
    -html-
    <div>
        <ul>
            <li>사과</li>
            <li>딸기</li>
            <li id="orange">오렌지</li>
        </ul>
        <div>당근</div>
        <p>토마토</p>
        <span class="orange">오렌지</span>
    </div>
    -css-
    #orange{
        color: red;
    }
    #orange : 아이디 속성값이 orange 인 요소 선택 
✔
```

## 복합 선택자
```buildoutcfg
✔ 일치 선택자(Basic Combinator)
ex) 
-html-
<div>
    <ul>
        <li>사과</li>
        <li>딸기</li>
        <li class = "orange">오렌지</li>
    <\ul>
    <div>당근</div>
    <p>토마토</p>
    <span class="orange">오렌지</span>
</div>
-css-
span.orange{
    color: red;
}
# 태그선택자와 클래스 선택자가 붙어있는경우 : span 태그면서 orange 클래스를 가지고 있는 것만 해당

✔ 자식 선택자(Child Combinator)
ex)
-html-
<div>
    <ul>
        <li>사과</li>
        <li>딸기</li>
        <li class = "orange">오렌지</li>
    <\ul>
    <div>당근</div>
    <p>토마토</p>
    <span class="orange">오렌지</span>
</div>

-css-
ul > .orange{
    color: red;
}
# ul 태그의 자식인 orage라는 클래스를 가지고 있는 것에 해당  

✔ 하위(후손) 선택자(Descendant Combinator)
ex)
-html-
<div>
    <ul>
        <li>사과</li>
        <li>딸기</li>
        <li class = "orange">오렌지</li>
    <\ul>
    <div>당근</div>
    <p>토마토</p>
    <span class="orange">오렌지</span>
</div>

-css-
div .orange{
    color: red;
}
# div 하위(후손)의 orange 클래스를 가지고 있는 것에 해당 

✔ 인접 형제 선택자(Adjacent Sibling Combinator)
ex)
-html-
<ul>
    <li>딸기</li>
    <li>수박</li>
    <li class="orange">오렌지</li>
    <li>망고</li>
    <li>사과</li>
</ul>   

-css-
.orange + li{
    color: red;
}
# 오렌지 클래스 값을 가지고 있는 요소의 다음 형제 요소가 선택이 됨
# 위 예시에선 망고가 선택이 됨

✔ 일반 형제 선택자(General Sibling Combinator)
ex)
-html-
<ul>
    <li>딸기</li>
    <li>수박</li>
    <li class="orange">오렌지</li>
    <li>망고</li>
    <li>사과</li>
</ul>   

-css-
.orange ~ li{
    color: red;
}
# 오렌지 클래스 값을 가지고 있는 요소의 다음 형제 요소 모두가 선택이 됨
# 위 예시에서 망고, 사과 선택 됨
```

## 가상 클래스 선택자
```buildoutcfg
✔ HOVER
* ABC:hover - 선택자 ABC 요소에 마우스 커서가 올라가 있는 동안 선택

-html-
<a href="https://www.naver.com>NAVER</a>

-css-
a:hover{
    color: red;
}
# a 태그에 마우스커서가 올라가 있는 경우엔 빨간색 글씨로 나오게 한다.

✔ ACTIVE
* ABC:active - 선택자 ABC 요소에 마우스를 클릭하고 있는 동안 선택.

-html-
<a href="https://www.naver.com>NAVER</a>

-css-
a:acitve{
    color: red;
}
# a 태그에 있는 요소를 클릭하고 있는 동안은 빨간색 글씨로 나오게 한다.

✔ FOCUS
* ABC:focus - 선택자 ABC 요소가 포커스되면 선택.
-html-
<input type="text">

-css-
input:focus{
    background-color: orange
}
# focus를 사용할 수 있는 요소는 한정되어있음
# input 요소가 포커스(선택)이 되면 오렌지색으로 변함. 포커스의 반대는 블러라고 부름
# 블러가 되면 다시 색이 하얀색으로 돌아옴

✔ FIRST CHILD
* ABC:first-child - 선택자 ABC가 형제 요소 중 첫째라면 선택.
-html-
<div class = "fruit">
    <span>딸기</span>
    <span>수박</span>
    <div>오렌지</div>
    <p>망고</p>
    <h3>사과</h3>
</div>
-css-
.fruites span:first-child{
    color: red;
}
# 첫번째 자식요소를 찾는다.
# 그 조건은 span 태그에 fruites 클래스의 후손이여야 한다.
# 위 예시에서 딸기가 해당됨

※ if 
-css-
.fruites div:first-child{
    color: red;
}
# 첫번째 요소가 div 태그가 아니므로 아무것도 바뀌지 않게 된다.

✔ LAST CHILD
* ABC:last-child - 선택자 ABC가 형제 요소 중 막내라면 선택.
-html-
<div class = "fruit">
    <span>딸기</span>
    <span>수박</span>
    <div>오렌지</div>
    <p>망고</p>
    <h3>사과</h3>
</div>
-css-
.fruites h3:last-child{
    color: red;
}
# 막내요소를 찾는다
# 그 조건은 h3 태그에 fruites 클래스의 후손이여야 한다.
# 위 예시에선 사과가 해당됨

✔ NTH CHILD 
* ABC::nth-child(n) 형제 요소들 중에 (n)째라면 선택
-html-
<div class="fruites>
    <span>딸기</span>
    <span>수박</span>
    <div>오렌지</div>
    <p>망고</p>
    <h3>사과</h3>
</div>

-css-
.fruits *:nth-child(2){
    color: red;
}
# 2번째 자식요소를 찾는다.
# * 에스터리스크는 (전체선택자) 어떤 태그가 오는지 상관없음. fruits 클래스의 후손이면 된다.
# 위 예시는 수박

※ 추가
.fruits *:nth-child(2n){
    color: red;
}
# 제로베이스 부터 시작해서 0,2,4.... 자식요소가 선택이됨
# 수박, 망고 
```

## 가상요소 선택자
```buildoutcfg
✔ BEFORE
* ABC::before - 선택자 ABC 요소의 내부 앞에 내용(Content)을 삽입
-html-
<div class="box">
    # ::before 글자 삽입 됨 
    Content!
</div>

-css-
.box::before{
    content: "앞!";
}
# 출력 : 앞! Content!

✔ AFTER
* ABC::after - 선택자 ABC 요소의 내부 뒤에 내용(Content)을 삽입
-html-
<div class="box">
    # ::before 글자 삽입 됨 
    Content!
</div>

-css-
.box::after{
    content: "뒤!";
}
# 출력 : Content! 뒤!
```

## 속성 선택자
```buildoutcfg
✔ ATTR 
* [ABC] - 속성 ABC을 포함한 요소 선택 (대괄호를 사용한다.)
* [ABC="XYZ"]

-html-
<input type="text" value="HEROPY">
<input type="password" value="1234">
<input type="text" value="ABCD" disabled>

-css-
[disabled] {
    color: red;
}
# disabled 속성을 가지고있는 3번째 인풋 요소만 선택됨
[value] {
    color: red;
}
# value 속성을 가지고 있는 모든 인풋 요소 선택
[type="password"] {
    color: red;
}
# type 속성의 password 값을 포함하고 있는 요소도 선택가능, 2번째만 선택이 됨
```