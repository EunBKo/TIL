# 2021년 1월 회고

1월은 어땠는지, 앞으로는 어떠할지에 대한 고찰을 써봤다.

# 공적

---

2020년은 어리버리 였다면, 21년은 달랐다.

## 1. 2020년에는 양파생활🧅 2021년에는 탈출

처음 들어간 회사에서 내가 할 줄아는 부분은 한정되어 있었고, 대부분은 프로젝트에 억지로 끼어있는 느낌이었다.

7월에 입사해서 첫 프로젝트에서 리뉴얼을 할때도 개발은 했지만 한정적이었고 그 다음 프로젝트에서도 지원인력으로 투입되어 산출물 작업을 맡아서 했다.

이렇다 보니 , 내가 정말 이 프로젝트에 기여했다는 느낌이 아닌 코딩하는 기계가 된 것 같은 느낌이었다.

![Untitled (1)](https://user-images.githubusercontent.com/58289110/106560121-d685da80-6569-11eb-9030-056f9b772d34.png)

이렇다 보니 문득 데굴데굴 굴러가는 프로젝트 속에서 사람들의 말을 듣고만 있는 내 자신이 사진 속 욕듣는 양파가 된 것 같았고 자신감이 많이 떨어지고 위축되었다.

그렇게 찾아온 2021년의 첫 프로젝트는 달랐다.

2021년 처음으로 들어온 프로젝트는 내가 정말 프론트의 인력이 되었다는 느낌을 강하게 받았다.

어드민 백오피스 프론트는 외주인력이 프론트개발을 하였는데, 그 부분에서 수정할 부분이 생겼을때는 백오피스 프리 자바 개발자 분들이 수정해서 써야했다. ~~(리액트 리덕스 툴킷-사가 소스)~~

리액트를 처음접해보신 분들이 수정해서 써야하기에는 소스분석이 어려운 코드였다. 

2월부터 프론트 PL분이 참여하시기로 해서 1월에는 전체 인력중 리액트를 접해본 사람이 나밖에 없었고~~(물론 정말 접하기만 했지만)~~, 과장님들도 울며 겨자 먹기로 신입인 나에게 관련 개념들을 계속 여쭤보셨다. 

사실 나에게 코드를 보고 분석해보라고 하셨으면, 못했을 것 같다..😂

하지만 JSP에 다년간 다져진 과장님들께서 먼저 소스를 까보고 리액트의 이런부분들이 JSP의 이런개념인지 여쭤보셔서, 나도 차근차근 소스를 까보고 내가 알던 내용이 이렇게 바뀌어서 구조가 짜졌구나 분석할 수 있었다.

과장님들께서 여쭤보시면 모르는 개념들은 직접 구글링 해서 찾아보고 이해하고, 과장님들께 설명 드렸다.

이런식으로 한달동안의 학습량이 첫 프로젝트때 3개월 하면서 배운 양보다 많았던 것 같다. 

레거시코드만 조금 볼 수 있던 나에게 redux, toolikit, styled-component, contextAPI, saga 등의 개념을 구글링 할 수 있는 기회를,,, 주신셈이다... ~~(전에는 이런게 있는지도 몰랐다..;)~~

그래서 과장님들도 에러를 내가 해결해주니 맨날 감사하다고 하고, 나 또한 과장님들 덕분에 새로운 소스를 분석하고 개념을 배우고 있어서 정말 감사하다.

## 2. 처음 짜보는 React 폴더구조

위에서 본 것 같이 프론트 PL님께서 2월에 오시기로 하셨는데, 갑자기 못 오신다고 하셔서 프론트 폴더구조 및 환경 세팅을 PM님께서 나에게 하라고 하셨다.

(아악)

폴더 구조에 대한 개념이 아예 없었다. 어떤게 효율적인지 어떤게 비효율적인지 생각할 겨를도 없었다.

이런나에게 세팅을 맡기시다니,,, 처음에는 원망스러웠다.. 회사가 3개월차 신입에게!! 이런걸 맡기다니..

그래도 ducks, thunk 열심히 찾아보고 열심히 조언을 구해가며 첫 프로젝트 구조를 세팅해봤다. 

```jsx
## 3. 폴더 구조

> src
> <br>
>
> > app
> > <br>
> >
> > > components (Presentation Components)
> > > <br>
> > > containers (Container Components)
> > > <br>
> > > pages (Routes)
> >
> > stores (Actions)
> > <br>
> > styles (CSSmodules (\*.module.scss))
> > <br>
> > utils (Utilities)

### pages

- 라우팅 페이지 (ex. 로그인페이지, 메인페이지, 상세페이지 ...)

### containers

- 컨테이너 컴포넌트 (ex. JSX 마크업 X, fetching 등을 통해 데이터 가공 후 프리젠테이션 컴포넌트에 넘겨줌)

### components

- 프리젠테이션 컴포넌트 (ex. JSX 마크업 O, props로 가져온 데이터 O, UI위한 state 값 O)

### stores

> Component (폴더명)
>
> > actions.ts : 액션 타입 관리
> > <br>
> > constants.ts : 액션 관리
> > <br>
> > reducer.ts : 리듀서 관리
```

항상 말로는 어렵다 못한다 하지만 뭔가 어려운 상황이 생기면 꼭 해결해 내야겠다는 욕심이 생기는 것 같다.. 고통을..즐기는편.. ㅎ

~~(it's 약간 변태)~~

열심히 야근하면서 만들었는데 다시 1월 말쯤되자 PL님이 다시 오시는걸로 결정났다..ㅋㅋㅋㅋㅋ 날아가는줄 알고 걱정했는데, PL님께서 내가 만든 폴더구조를 날리지않고 유지하면서 가자고 말씀해주셔서 좋았다.

정말 몇일동안 어떤 구조가 효율적인지 계속 검색하면서 앞으로 공부할게 아직 정말 많이 남았다는걸 깨달았다.

항상 질 좋은, 최적화된 서비스를 제공하기 위해서 고민을 멈춰선 안 된다.

준일님 회고에 적혀있는 글이다. 나도 앞으로 계속 고민하는 개발자가 될 것이다.

# 사적

---

2020년은 나에게 정말 많은 변화를 준 해였고, 2021년은 더 열심히 살아보려고 한다.

## 1. 일일커밋, TIL을 시작했다.

### 계기

작년 7월에 입사해서 개발 일을 시작하면서, 모르는게 정말 많았다.

모르는 것을 구글링 해서 찾아보고 해결해나갔고, 이런 과정들을 반복하면서 이 모든 과정들이 나에게 도움이 되는 과정들이라는 것을 깨닫고 기록하고 싶었다.

### 방법

기록하는 방법은 정말 많았다. ~~[요블로그 참고](https://medium.com/amhocode/개발-블로그-플랫폼-선택-고민-f3a198b942d1)~~

Velog, Tstory, Medium.... 기존의 취미로 해나가던 네이버 블로그 또한 이중 하나였다. (틈새자랑..)

플랫폼이 정말 많아서 어디서 시작해야 될지 고민하고 구글링 하던 중 희망의 줄기... [갓 황준일님의 깃헙](https://junilhwang.github.io/TIL/Review/2020-year/01-January/#공적)을 보게 되었다...

황준일님이 2020년 하셨던 TIL을 보고 정말 심장이? 머리가 번뜩했다.. 

TIL은 Today I Learned에 약자로 매일매일 배운것을 기록한다는 의미를 가지고 있다.

이를 매일매일 커밋으로 하는사람도 있고 정리를 하는 사람들도 있는데, 

준일님의 TIL을 보고 나도 매일매일 회사에서 구글링 하고 에러를 해결해 나간 과정을 메모하는 방식으로 작성하면 좋겠다고 생각해서 깃허브에서 TIL을 시작하게 되었다.

![Untitled (2)](https://user-images.githubusercontent.com/58289110/106560148-e7365080-6569-11eb-88fd-ae4fb1d15f34.png)

깃허브의 초기세팅 등 처음시작하는 Git이 어려웠지만 처음시작한 1월11부터 2월이 된 지금까지 나름 열심히 잔디를 가꿔오고 있다.🌱

~~(옆에서 TIL올리라고 열심히 재촉해주시는 분들 감사합니다... 앞으로도 재촉 부탁드립니다 꾸벅)~~

### 앞으로의 TIL 방향

- TIL 레포지토리는 나의 일기장

→ TIL은 지금처럼 매일매일 메모용으로 사용하려고 한다. ~~형식에 구애받지않고~~ 다만, 주말마다 TIL을 보고 정말 유익했던 내용이나 에러를 처리한 부분을 velog에 하나씩 정리해 나가려고 한다.

그렇게 하면 TIL에는 최대한 빨리빨리 많은 내용을 담을 수 있을 것이고, velog에는 정말 알찬 정보만 쌓여가겠지..? (작은소망😊)

- TIL을 통한 회고작성

→ 한달을 마무리 하며 TIL을 기반으로 회고를 작성하려고 한다. 나의 생활을 되돌아보고 앞으로의 발전적인 계획을 세우기 위해서는 회고가 정말 필수 인 것 같다. 

처음에는 어떻게 적을지 막막할때가 많은데, 이럴때는 다른분들이 쓴걸 참고하면서,, 점점 나만의 레이아웃을 찾아가야겠다.

- TIL에 Gatsby & Github Actions 적용해보기

→ 황준일님의 틸은 Vue.js 기반의 Vuepress를 이용해서 블로그를 만드는 방식인데, 이처럼 나도 react 기반의 Gatsby를 이용해서 블로그에 적용해보고 싶다. 

[GatsbyJS 개발 환경 셋팅부터 GitHub Pages 배포까지](https://musma.github.io/2019/08/09/gatsby-js.html)

→ 기존의 있던 네이버 블로그를 당장 쓰지는 않지만 같이 포스팅 할수 있는 방법이 없을까 하고 생각하다가 알게 된 것이 깃헙 액션이다. 

깃헙 액션을 사용하면 깃에서 변경사항이 생겼을때 action을 취해준다고 한다.  네이버의 api문제 관련하며 puppeteer를 사용해야 한다고 한다. 

TIL Velog에 정리하는게 적응되면 천천히 시작해보려고 한다. 그 과정에서 Github Action도 적용시켜서 나의 일일 커밋 & TIL활동이 기존의 네이버 블로그에 뜰 수 있게 하는게 올해의 목표이다.

## 2. React 스터디를 시작했다. (갓녈녁👍)

### 갑자기 스터디? 왜?

React를 처음시작한건 지금 회사~~(나의 첫직장)~~에 들어와서 첫 프로젝트부터였다.

갓 졸업하고 아무것도 모르는 신입인 나에게 회사에서는 프론트영역부터 해보라고 하셨고, 처음 간 프로젝트는 React- JavaScript 기반의 하이브리드 앱을 리뉴얼 하는 것이었다.

JavaScript기반의 기존소스를 보고 React의 버전업과 TypeScript로의 컨버팅이 프론트파트의 궁극적인 개발 목적이었다.

React가 뭔지도 모르던 내가 들어와서 처음 사수분께 받은 과제는 React로 탭만들어서 클릭할 때 마다 색이 바뀌게 만들어 보는 것이었다.

탭만들고 기본적인 것만 하다가 개발이 시작되고 TS로 페이지를 쳐내다보니, 프로젝트가 끝났을때 머리속에 남는게 별로 없었다.

그래서 언젠가 한번쯤은 다시 만들어보고 공부하고 

왜 React인지? 왜 Redux, TypeScript를 많이 쓰는지? 에 대한 가장 기초적인 부분에 대한 답을 찾고 제대로 개발하고 싶다는 생각을 갖게 되었다.

### 어디에서?

처음 나에게 에러가 났을때 정말 막막했었다. 사수분께 여쭤보기에는 당시에는 어려웠고, 구글링도 무엇을 검색해야될지 모르겠다는 생각을 많이 했다.

그러던 중 카카오톡 프론트 개발자 오픈채팅방을 알게 되었고, 그곳에서 질문을 해가면서 답을 찾곤 했었다.

몇일 전 그곳에서, 내가 위에서와 한 생각과 같은생각을 가진 분들이 React의 대한 원론적인 공부를 하는 스터디를 만드신다고 들었고 바로 참여해도 되냐고 여쭤봐서 [스터디](https://github.com/AlpoxTutoring/react-project1)를 시작하게 되었다.

### 어떻게?

스터디는 메인 멘토(?) React를 정말 잘하시는.. 갓민열님과 함께한다.. 물론 중간에 또 정말 잘하시는 갓민혁님도 함께 참여하시게 되었다.

멘토의 과제와 tutoring을 중심으로 진행해 나가고 진행하는 과정속에서 모르는부분은 카카오톡으로 공유를 해서 해결해 나간다.

![Untitled (3)](https://user-images.githubusercontent.com/58289110/106560177-f1584f00-6569-11eb-9c72-34789c92bcfc.png)

## 3. 자극 뿜뿜

스터티를 시작한지는 얼마 되지 않았지만, 멘토분들 뿐만 아니라 다른 분야에서도 오래계셨던 분들도 있고 정말 좋으신분들이 모이신 것 같다.

서로 열심히 진행하다보니 각자의 활동이 욕심이 되고 좋은 자극이 되는 것 같다. 진행하면서 기본적인 목표인 React의 기본기를 다지고, 멤버들과의 경험을 공유해가며 성장해 나가고 싶다. (~~우물안 개구리 탈출 계획 중~~)

 

그리고 자극이 되는 영상을 보거나(EO, 연설문) , 회고 등을 읽으면서 공부에 대한 관성을 키우고 싶다.

- **[지방대 개발 비전공자가 배달의민족 리드 개발자가 되기까지(opens new window)](https://www.youtube.com/watch?v=V9AGvwPmnZU&t=165s)**
- **[체대 출신 개발자의 2019년 회고(opens new window)](https://ryan-han.com/post/memoirs/memoirs2019/)**
- **[나의 소중하고 또 존경하는 친구의 기록들 - ChoDragon9/Posts(opens new window)](https://github.com/ChoDragon9/posts/wiki)**
- **[김민준(Velopert)님의 2019년 회고](https://velog.io/@velopert/2019.log)**

준일님도 작년 이맘 회고에서 다른분들의 회고를 보고 많은 것을 느끼신 것 같았다.  치열하게 살아가는 사람들의 글을 읽다보니, 존경심, 욕심이 생겼고 그들그들처럼 살아가고 싶다는 생각을 하게 되었다.

 왜 이제야 봤을까하고 살짝 후회는 되지만, 자꾸 조급해 하지않고 천천히 열심히 잘 해보려고 한다..! 열심히 하면서 재미를 잃지않고 지치지 않게 하려면 아무래도 체력이 제일 우선인 것 같다. 

학생때는 춤을 자주 추면서 운동량을 유지했는데, 일을 시작하니 운동량이 현저히 작아져서 살도 많이 찌고 게을러졌다.

TIL 작성을 열심히 하면서 운동계획도 짜서 함께 실천해나가면서 체력을 길러야 할 것 같다.

# Summary

---

- 새로운 프로젝트 - React 폴더 구조 짜보기
- 일일 커밋 - TIL 시작
- 체력 키우기
