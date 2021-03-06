### 레이아웃 또는 리플로우

렌더 트리 구성이 끝나면 레이아웃 단계가 이어진다. 모질라에서는 이 과정을 리플로우(reflow)라고 부르기도 한다.

레이아웃 단계에서는 **렌더 트리에서 계산되지 않았던 노드들의 크기와 위치, 레이어 간 순서와 같은 정보를 계산하여 좌표에 나타낸다**. 

이 과정은 HTML의 루트 오브젝트로부터 재귀적으로 실행이 된에서는 렌더 트리에서 계산되지 않았던 노드들의 크기와 위치, 레이어 간 순서와 같은 정보를 계산하여 좌표에 나타낸다. 이 과정은 HTML의 루트 오브젝트로부터 재귀적으로 실행이 된다.

한편, 레이아웃은 계산의 범위에 따라 **전역적 레이아웃(Global Layout)**과 **증분적 레이아웃(Incremental Layout)**으로 구분할 수 있다.

**전역적 레이아웃**은 말 그대로 화면 전체의 레이아웃을 계산하는 것이다. 

가령 새로운 폰트를 적용하거나, 폰트 사이즈가 바뀌거나, 뷰포트의 사이즈 변경 같은 경우가 있을 때 전체 레이아웃을 다시 계산한다. `offsetHeight` 같은 일부 DOM 관련 JavaScript API에 접근을 하는 경우에도 전역적 레이아웃이 다시 계산되기도 한다.

이러한 전역적 레이아웃 단계는 모든 렌더 트리 노드에 대해 기하학적인 계산을 수행하기 때문에, 노드가 많아지게 된다면 그 속도가 느려지게 된다. 따라서 브라우저에서는 자체적인 최적화 로직을 탑재하고 있다.

그 중 하나가 바로 **더티 비트 시스템(Dirty bit system)이**다. 더티 비트 시스템은 특정 엘리먼트의 레이아웃이 변경이 되었을 때, 렌더 트리를 처음부터 탐색하면서 레이아웃을 계산하지 않고 특정한 부분만 다시 계산하여 리소스의 낭비를 줄이는 최적화 방법이다.

**증분적 레이아웃**은 이러한 더티 비트 시스템을 활용한다. 

레이아웃 과정에서 렌더 트리를 재귀적으로 탐색을 하다가 더티한 엘리먼트들, 즉 레이아웃의 변경이 발생해야 하는 엘리먼트들을 만나게 되면, 그 계산을 즉시 수행하는 것이 아니라 스케쥴러를 통해 비동기로 일괄 작업(batch)을 진행한다. 이를 통해 연산의 횟수와 범위를 줄일 수 있다.

하지만 아주 복잡한 레이아웃의 경우에는 브라우저 단에서의 최적화만으로는 충분하지 않기 때문에, 프론트엔드 개발자 역시 레이아웃 과정의 연산을 최소화하도록 신경을 써야 한다. 때문에 브라우저처럼 행동하는 것이 필요하다. DOM의 레이아웃과 관련된 값을 직접 읽어오거나 변화를 주는 JavaScript 코드를 작성해야 한다면, 그러한 구문들을 최대한 묶어야 한다.

```jsx
const divWidth = div1.clientWidth;
div2.style.width = `${diwWidth}px`;

const divHeight = div1.clientHeight;
div2.style.height = `${divHeight}px`;
```

위의 코드는 `div1` 이라는 태그의 너비와 높이 값을 읽어와 `div2` 의 인라인 스타일에 적용하는 방식으로 DOM을 직접 수정하는 코드이다.

위에서 언급한 바와 같이, 브라우저는 *더티*한 레이아웃이 발생할 때마다 증분적 레이아웃을 수행하기 위해 레이아웃 계산을 스케쥴러에 등록한다. 

위의 코드는 `div2` 의 너비를 변경한 후 다시 `div1` 의 높이를 불러오기 때문에, 두 과정 사이에서 발생했을 수도 있는 레이아웃의 변경 때문에 불필요한 계산이 추가가 된다. 즉, 레이아웃 관련 값을 읽어오는 부분과 레이아웃을 수정하는 코드가 혼용되었기 때문에 최적화 관점에서 문제가 된다.
 
따라서 위 코드는 아래와 같이 수정함으로써 계산 과정을 줄일 수 있다.

```jsx
const divWidth = div1.clientWidth;
const divHeight = div1.clientHeight;

div2.style.width = `${diwWidth}px`;
div2.style.height = `${divHeight}px`;
```
