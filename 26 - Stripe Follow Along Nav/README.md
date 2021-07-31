# 26. Stripe Follow Along Dropdown

nav메뉴에 mouse가 올라가면 dropdown메뉴가 각각의 크기,위치에 맞게 보여짐.

<img src="./readme_images/resultScreen.gif" alt="결과화면"/>

**초기코드**

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Follow Along Nav</title>
</head>
<body>
    <h2>Cool</h2>
    <nav class="top">
        <div class="dropdownBackground">
            <span class="arrow"></span>
        </div>
    
        <ul class="cool">
            <li>
                <a href="#">About Me</a>
                <div class="dropdown dropdown1">
                    <div class="bio">
                        <img src="https://logo.clearbit.com/wesbos.com">
                        <p>Wes Bos sure does love web development. He teaches things like JavaScript, CSS and BBQ. Wait. BBQ isn't part of web development. It should be though!</p>
                    </div>
                </div>
            </li>
            <li>
                <a href="#">Courses</a>
                <ul class="dropdown courses">
                <li>
                    <span class="code">RFB</span>
                    <a href="https://ReactForBeginners.com">React For Beginners</a>
                </li>
                <li>
                    <span class="code">ES6</span>
                    <a href="https://ES6.io">ES6 For Everyone</a>
                </li>
                <li>
                    <span class="code">NODE</span>
                    <a href="https://LearnNode.com">Learn Node</a>
                </li>
                <li>
                    <span class="code">STPU</span>
                    <a href="https://SublimeTextBook.com">Sublime Text Power User</a>
                </li>
                <li>
                    <span class="code">WTF</span>
                    <a href="http://Flexbox.io">What The Flexbox?!</a>
                </li>
                <li>
                    <span class="code">GRID</span>
                    <a href="https://CSSGrid.io">CSS Grid</a>
                </li>
                <li>
                    <span class="code">LRX</span>
                    <a href="http://LearnRedux.com">Learn Redux</a>
                </li>
                <li>
                    <span class="code">CLPU</span>
                    <a href="http://CommandLinePowerUser.com">Command Line Power User</a>
                </li>
                <li>
                    <span class="code">MMD</span>
                    <a href="http://MasteringMarkdown.com">Mastering Markdown</a>
                </li>
                </ul>
            </li>
            <li>
                <a href="#">Other Links</a>
                <ul class="dropdown dropdown3">
                    <li><a class="button" href="http://twitter.com/wesbos">Twitter</a></li>
                    <li><a class="button" href="http://facebook.com/wesbos.developer">Facebook</a></li>
                    <li><a class="button" href="http://wesbos.com">Blog</a></li>
                    <li><a class="button" href="http://wesbos.com/courses">Course Catalog</a></li>
                </ul>
            </li>
        </ul>
    </nav>
    
    <style>
    html {
        box-sizing: border-box;
        font-family: "Arial Rounded MT Bold", "Helvetica Rounded", Arial, sans-serif;
    }
    
      *, *:before, *:after {
        box-sizing: inherit;
    }
    
    body {
        margin: 0;
        min-height: 100vh;
        background:
            linear-gradient(45deg, hsla(340, 100%, 55%, 1) 0%, hsla(340, 100%, 55%, 0) 70%),
            linear-gradient(135deg, hsla(225, 95%, 50%, 1) 10%, hsla(225, 95%, 50%, 0) 80%),
            linear-gradient(225deg, hsla(140, 90%, 50%, 1) 10%, hsla(140, 90%, 50%, 0) 80%),
            linear-gradient(315deg, hsla(35, 95%, 55%, 1) 100%, hsla(35, 95%, 55%, 0) 70%);
    }
    
    h2 {
        margin-top: 0;
        padding-top: .8em;
      }
    
    nav {
        position: relative;
        perspective: 600px;
    }
    
    .cool > li > a {
        color: yellow;
        text-decoration: none;
        font-size: 20px;
        background: rgba(0,0,0,0.2);
        padding: 10px 20px;
        display: inline-block;
        margin: 20px;
        border-radius: 5px;
    }
    
    nav ul {
        list-style: none;
        margin: 0;
        padding: 0;
        display: flex;
        justify-content: center;
    }
    
    .cool > li {
        position: relative;
        display: flex;
        justify-content: center;
    }
    
    .dropdown {
        opacity: 0;
        position: absolute;
        overflow: hidden;
        padding: 20px;
        top: -20px;
        border-radius: 2px;
        transition: all 0.5s;
        transform: translateY(100px);
        will-change: opacity;
        display: none;
    }
    
    .trigger-enter .dropdown {
        display: block;
    }
    
    .trigger-enter-active .dropdown {
        opacity: 1;
    }
    
    .dropdownBackground {
        width: 100px;
        height: 100px;
        position: absolute;
        background: #fff;
        border-radius: 4px;
        box-shadow: 0 50px 100px rgba(50,50,93,.1), 0 15px 35px rgba(50,50,93,.15), 0 5px 15px rgba(0,0,0,.1);
        transition: all 0.3s, opacity 0.1s, transform 0.2s;
        transform-origin: 50% 0;
        display: flex;
        justify-content: center;
        opacity:0;
    }
    
    .dropdownBackground.open {
        opacity: 1;
    }
    
    .arrow {
        position: absolute;
        width: 20px;
        height: 20px;
        display: block;
        background: white;
        transform: translateY(-50%) rotate(45deg);
    }
    
    .bio {
        min-width: 500px;
        display: flex;
        justify-content: center;
        align-items: center;
        line-height: 1.7;
    }
    
    .bio img {
        float: left;
        margin-right: 20px;
    }
    
    .courses {
        min-width: 300px;
    }
    
    .courses li {
        padding: 10px 0;
        display: block;
        border-bottom: 1px solid rgba(0,0,0,0.2);
    }
    
    .dropdown a {
        text-decoration: none;
        color: #ffc600;
    }
    
    a.button {
        background: black;
        display: block;
        padding: 10px;
        color: white;
        margin-bottom: 10px;
    }
    
    /* Matches Twitter, TWITTER, twitter, tWitter, TWiTTeR... */
    .button[href*=twitter] { background: #019FE9; }
    .button[href*=facebook] { background: #3B5998; }
    .button[href*=courses] { background: #ffc600; }
    </style>
    
    <script>
    </script>
    
</body>
</html>
```



**초기화면**

<img src="./readme_images/startScreen.png" alt="시작화면"/>



### 과정

<strong>1. 마우스 올릴 시 dropdown띄우기</strong>

trigger-enter클래스를 추가하여 띄우고 지운다.

```css
/*추가*/
.trigger-enter .dropdown {
    display: block;
}
.trigger-enter-active .dropdown {
    opacity: 1;
}
```



```javascript
const triggers = document.querySelectorAll(".cool > li");
const background = document.querySelector(".dropdownBackground");
const nav = document.querySelector(".top");

function handleEnter(){
    // console.log("ENTER!!");
    this.classList.add('trigger-enter');
    setTimeout(()=>
               this.classList.add('trigger-enter-active'), 150)
}

function handleLeave(){
    console.log("LEAVE!!");
    this.classList.remove('trigger-enter', 'trigger-enter-active');
}

triggers.forEach(trigger => trigger.addEventListener('mouseenter', handleEnter));
triggers.forEach(trigger => trigger.addEventListener('mouseleave', handleLeave));
```



<strong>2. 내용크기따라 흰색박스 변경</strong>

```css
/*추가*/
.dropdownBackground.open {
    opacity: 1;
}
```

dropdown의 opacity를 1로하여 보이게한다.



```javascript
 const triggers = document.querySelectorAll(".cool > li");
 const background = document.querySelector(".dropdownBackground");
 const nav = document.querySelector(".top");

function handleEnter(){
    // console.log("ENTER!!");
    this.classList.add('trigger-enter');
    setTimeout(()=>this.classList.add('trigger-enter-active'), 150);
    background.classList.add('open');

    const dropdown = this.querySelector('.dropdown');
    // console.log(dropdown);
    const dropdownCoords = dropdown.getBoundingClientRect();
    const navCoords = nav.getBoundingClientRect();
    // console.log(navCoords);
    const coords = {
        height: dropdownCoords.height,
        width: dropdownCoords.width
    };
        background.style.setProperty('width', `${coords.width}px`);
        background.style.setProperty('height', `${coords.height}px`);
}
```

getBoundingClientRect()를 통해 해당 컨텐츠의 정보를 받아와 흰박스의 style을 변경해준다.

<img src="./readme_images/resize.gif" alt="드롭다운내용"/>



<strong>3. 흰박스 위치 이동</strong>

```java
<script>
function handleEnter(){
    // console.log("ENTER!!");
    this.classList.add('trigger-enter');
    setTimeout(()=>this.classList.add('trigger-enter-active'), 150);
    background.classList.add('open');

    const dropdown = this.querySelector('.dropdown');
    const dropdownCoords = dropdown.getBoundingClientRect();
    const navCoords = nav.getBoundingClientRect();

    const coords = {
        height: dropdownCoords.height,
        width: dropdownCoords.width,
        top: dropdownCoords.top,
        left: dropdownCoords.left
    };
    background.style.setProperty('width', `${coords.width}px`);
    background.style.setProperty('height', `${coords.height}px`);
    background.style.setProperty('transform', `translate(${coords.left}px, 					 ${coords.top}px)`);
}
```

넓이와 높이 뿐만아니라 left, top값도 변경해준다.

<img src="./readme_images/moveDropBox.gif" alt="박스 위치 이동"/>



그러나 메뉴위에 h2가 위에있으면 깨짐.

<img src="./readme_images/broke.gif" alt="깨짐현상"/>



<strong>4. 위치조정 </strong>

offsetTop과 Left를 빼줌

```javascript
const coords = {
    height: dropdownCoords.height,
    width: dropdownCoords.width,
    top: dropdownCoords.top - navCoords.top,
    left: dropdownCoords.left - navCoords.left
};
```

<img src="./readme_images/subOffset.gif" alt="위치조정"/>



마우스를 빠르게움직이면 내용이 계속 보인상태로 움직임

<img src="./readme_images/scatter.gif" alt="흐뜨려짐 현상"/>



<strong>5. 클래스 추가 조건식 변경 </strong>

```javascript
this.classList.add('trigger-enter');
setTimeout(()=>this.classList.contains('trigger-enter') && this.classList.add('trigger-enter-active')
```

trigger-enter가 있는지 확인하고, active를 추가함.



<img src="./readme_images/resultScreen.gif" alt="결과화면"/>