# 티스토리에 깃허브처럼 잔디깔기!
 

## 1. 계기
지난 10월에 첫 포스팅을 올린 이래로 이제 4개월 차,

언제부턴가 깃허브의 잔디가 부러워지기 시작했다 ㅠㅠㅠ


지금이라도 넘어갈까 고민도 잠시 해봤지만, 지금껏 함께해온 티스토리에 정도 많이 들었고...

편의성 부분에서 깃허브 페이지는 도무지 메인으로 사용하고 싶은 마음이 들지 않았다.
 

그렇다면, 깃허브의 잔디같은 시스템(?)을 티스토리에 구현해보면 어떨까하는 생각이 들었다.

조사 차 찾아보니 생각보다 어려울 것 같지 않았고, 반나절을 꼬박 들인 결과... 제법 만족스러운 그림이 나왔다!
 

그래서 공유해본다! 일명 티스토리에 잔디 깔기 대작전이다! ( ｯ◕ ܫ◕)ｯ' 

---

## 2. 구현 방법

티스토리에는 포스팅 달력이라는 위젯이 있다.

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FoEbAg%2FbtrpOxl4ckK%2FZSxTGl6rbAFD9KyY1oskj0%2Fimg.png">

포스팅을 올린 날짜에 주황색 표식이 생긴다고 이해하면 된다.

표식을 클릭하면 해당 포스팅으로 넘어가주는 기능까지 있다.

사실상 필요한 기능은 이 정도면 충분하기 때문에,

여기에 CSS를 추가해주고 JS로 HTML의 구조를 변조하여 깃의 잔디처럼 보이게 하는 것을 목표로 삼았다!

---

## 3. 생김새 및 기능
 

### 완성본은 이렇게 생겼다

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcUyvIW%2FbtrpLtqYipg%2FdeMCfj7hB03wdhYkReVLrK%2Fimg.png">

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbGUurC%2FbtrpJQtmOtC%2FqrDsYILTzu7VL1GFARlDj0%2Fimg.png">

달력을 셀로 바꿔놨다고 생각하면 이해하기 편하다.

셀의 기본 색상은 회색이며, 포스팅을 올리면 해당 날짜의 셀이 녹색으로 변한다.

텀 없이 매일 게시글을 올리면 색이 점점 진해지게끔 해줬다.

(하루라도 놓치면 리셋이다 ㅎ)

<br>

### 적용해놓고 보면 이런 느낌이다

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FtZbwd%2FbtrpMRE6FI3%2Fv8FPGpc3R93LmRPtuD6m3k%2Fimg.png">

제법 귀엽다.....ㅎ

원본 위젯의 기능을 그대로 유지하고 있기 때문에,

셀을 클릭할 시 해당 날짜에 작성한 포스팅 모음을 볼 수 있다.

---

## 4. 티스토리 잔디 적용 방법
 

### 설명
지금부터는 적용 방법이다.

크게 복잡하지 않다!

 

### 주의사항
기존 스킨에 포함되어있는 달력 위젯이 있다면 깨끗하게 제거한 후 진행하는 것이 안전하다!

▶ HTML 내부의 달력 element 관련 코드를 삭제하고 CSS에서도 calendar 관련 코드를 삭제해주어야 한다.


---

### [1] 스킨 편집창으로 들어가기
1. 설정 화면 > 스킨 편집 을 클릭한다.

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdLBCM0%2FbtrpSkFPuLI%2FXOq2v5Gak4uFsmr0jBTTsK%2Fimg.png">

<br>

2. html 편집 을 클릭한다.

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F2eYap%2FbtrpP35UWIS%2FSKVZkXFAmPKIkvZ2D0AxCk%2Fimg.png">

<br>

3. 여기서 현재 적용중인 스킨의 HTML/CSS 를 볼 수 있다.

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fc6PuPA%2FbtrpP3SlQBU%2FW5pjiKopiXrqyVn55JPCT1%2Fimg.png">
 
<br>

### [2] HTML에 jandi_html.html을 추가한다
HTML 탭에 들어가서 코드를 훑어보면 중간에 <s_sidebar_element>들이 모여있는 구간이 있을 것이다.

해당 구간의 원하는 위치에 jandi_html의 내용을 복붙해주면 된다.

▶ 이 글은 사이드바가 있는 스킨을 기준으로 작성되었다. 사이드바가 없는 스킨을 사용하고 있다면 적절한 위치를 직접 선정하여 코드를 넣어준다.

복붙을 완료했다면 HTML 탭 우측 상단의 적용 버튼을 꼭 눌러주자!

<br>

### [3] CSS 가장 아래쪽에 jandi_css.css를 추가한다
CSS 탭에 들어간 후 스크롤바를 쭉 밑으로 내려준다.

가장 끝자리에 jandi_css의 내용을 추가해주면 된다.

복붙을 완료했다면 이번에도 CSS 탭 우측 상단의 적용 버튼을 눌러준다.

<br>

### [4] 새로고침
블로그를 새로고침하면 아마 <b>어딘가 좀 이상한 모양의 잔디밭</b>을 볼 수 있을 것이다.

▶ 만약 잔디밭 모양이 정상적으로 출력된다면 운이 좋은 케이스이고 여기서 끝이다! 👏🏻

<br> 

### [5] 잔디밭의 너비와 높이를 스킨에 맞게 수정한다
위 CSS는 내가 사용하고 있는 스킨에 맞게 너비와 높이를 고정값으로 짜놓은 것이라

나와 다른 스킨을 사용하고 있다면 십중팔구 잔디밭이 꾸겨져 있을 것이다 ㅠㅠ

물론 반응형으로 짜고 싶었지만... 잘 안됐다 ㅎ

따라서 CSS를 조금 수정하여 자신의 스킨에 맞게 조정해주어야 한다.

아까 추가했던 CSS 내부에서 다음 두 부분을 찾은 후, 너비와 높이를 수정하여 각 셀이 정사각형 모양을 띄게끔 만들어주면 된다.

값 수정 → 적용 → 새로고침 순으로 테스트하며 적정한 값을 찾아주자!

```css
/* width = 너비를 결정하는 값이다 */
.calendar .tt-calendar {margin-top:8%;margin-bottom:10%;width:280px !important;border-collapse:collapse;}

/* font-size = 높이를 결정하는 값이다 */
.calendar .tt-calendar td {font-size:1.3em; color:#bbb;}
```

▶ 잔디밭 모양은 잡았는데, 캡션 부분이 너무 길어서 줄바꿈되어버린다면 추가했던 HTML 코드 내의 이전 달로 가는 버튼과 다음 달로 가는 버튼에 포함된 공백 특수문자의 개수를 줄여주면 된다. (해당 부분에 주석을 달아놨으므로 Ctrl+F 하여 찾아준다.)

<br>

### [6] 끝!
수정이 성공적으로 끝났다면 드디어 푸릇푸릇한 잔디밭을 볼 수 있다!

---
      
## 5. 추가적으로 커스터마이징하고 싶다면?
 

### 참고
커스터마이징을 하고 싶다면 가장 먼저 해당 위젯의 구조를 파악하여야 한다.

다음 포스팅에 달력 위젯의 소스 코드와 클래스 관련 정보가 깔끔하게 정리되어있다.

https://tistory.noo9ya.com/67
 

### 잔디의 색상을 바꾸고 싶다면?
위에 첨부했던 HTML 코드를 살펴보면 중간에 cnt의 값에 따라 color에 각기 다른 값을 할당하는 구간이 있음을 확인할 수 있다.

이 부분의 color에 원하는 색상을 넣어주면 된다!

```javascript
    if(cnt<1){
        color = "#C5E1A5"  // 여기!
    } else if(cnt<2){
        color = "#AED581"  // 여기!
    } else if(cnt<3){
        color = "#9CCC65"  // 여기!
    } else if(cnt<4){
        color = "#8BC34A"  // 여기!
    } else if(cnt<5){
        color = "#7CB342"  // 여기!
    } else if(cnt<6){
        color = "#689F38"  // 여기!
    } else{
        color = "#558B2F"  // 여기!
    }
```
