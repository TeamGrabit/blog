지금까지 저는 항상 React로 개발을 해왔습니다. 그런데 주변에서 React가 너무 느리다, 무겁다라고 하더라구요. 실제로도 React의 치명적인 단점으로 다른 프레임워크에 비해 너무 느리다는 것이 지적되기도 했구요. 그래서 이번에 한 프로젝트를 시작하면서 프론트엔드 프레임워크로 Svelte를 사용해보기로 했습니다. 3대 프론트엔드 프레임워크로 불리는 React, Vue.js, Angular를 두고 왜 Svelte를 선택했는지 차근차근 알아보도록 하겠습니다.

### Svelte에 대한 높은 관심과 만족도
[The State of JS 2021: Front-end Frameworks](https://2021.stateofjs.com/en-US/libraries/front-end-frameworks)

![](https://images.velog.io/images/tnghd5761/post/b1c478bc-490d-40fe-aa34-077cb8f7d244/image.png)

![](https://images.velog.io/images/tnghd5761/post/cc3706ee-4faf-4993-91e3-d24b66953b5e/image.png)

![](https://images.velog.io/images/tnghd5761/post/5d914d7e-e9db-4b77-869a-0581bef5fc5a/image.png)

State of JS 2021의 설문을 살펴보면 Svelte에 대한 만족도와 관심도 부분에서 굉장히 높은 순위를 기록하고 있고 Usage에서도 3대 프레임워크 React, Angular, Vue.js 다음으로 높은 순위를 차지하고 있습니다. 또한, 인식 조사에서 사용 경험이 3대 프레임워크보다 떨어짐에도 불구하고 React 다음으로 많은 사람들이 긍정적으로 평가하고 있습니다.

그렇다면 왜 사람들이 Svelte를 이렇게 높이 평가하는지, 왜 Svelte를 사용하는지 알아보도록 하겠습니다!

----

### Svelte의 특징

[Svelte 공식 홈페이지](https://svelte.dev/)
![](https://images.velog.io/images/tnghd5761/post/ec7d7c78-1d8a-443a-b867-0dcf10c30916/svelte.dev_.png)

Svelte 공식 홈페이지를 보면 특징으로 'Write less code', 'No virtual Dom', 'Truly reactive'라고 소개를 합니다.

### Write less code
>```Svelte
<!-- Svelte -->
<script>
	let a = 1;
	let b = 2;
</script>
>
<input type="number" bind:value={a}>
<input type="number" bind:value={b}>
>
<p>{a} + {b} = {a + b}</p>
>```

다음의 Svelte 코드를 React, Vue로 바꾸면 다음과 같습니다.
>```javascript
// React
import React, { useState } from 'react';
>
export default () => {
	const [a, setA] = useState(1);
	const [b, setB] = useState(2);
>
	function handleChangeA(event) {
		setA(+event.target.value);
	}
>
	function handleChangeB(event) {
		setB(+event.target.value);
	}
>
	return (
		<div>
			<input type="number" value={a} onChange={handleChangeA}/>
			<input type="number" value={b} onChange={handleChangeB}/>
>
			<p>{a} + {b} = {a + b}</p>
		</div>
	);
};
>```

>```Vue
<!-- Vue -->
<template>
	<div>
		<input type="number" v-model.number="a">
		<input type="number" v-model.number="b">
>
		<p>{{a}} + {{b}} = {{a + b}}</p>
	</div>
</template>
>
<script>
	export default {
		data: function() {
			return {
				a: 1,
				b: 2
			};
		}
	};
</script>
>```

**React**의 input 태그는 양방향 바인딩을 지원하지 않기 때문에 input 이벤트를 일일이 함수로 직접 반응해서 변수를 수정해주어야 합니다. 또한, React는 local component state를 update할 때, useState와 같은 hook을 사용함으로써 Svelte에 비해 훨씬 더 많은 코드를 요구하게 됩니다.

**Vue**의 경우, Svelte처럼 v-model을 사용해서 바인딩을 표현할 수 있지만, `<template>` 태그를 통해 내용을 감싸야하는 점과 객체 선언을 통한 데이터 초기화때문에 Svelte에 비해 코드가 길어집니다.

### No virtual DOM
가상 DOM을 사용하지 않는다. 처음 보기에 이것이 좋은 특징인지는 의문이 들 수 있습니다. 왜냐하면 프론트엔드를 공부하면서 가상 DOM이 빠르다고 많이 봐왔기 때문이죠. React의 대표적인 특징인 가상 DOM을 설명할 때, 직접 DOM을 조작하지 않고 데이터가 변경됐을 경우 실제 DOM과 가상 DOM을 비교하여 변경된 부분만을 적용하기 때문에 성능이 더 빠르다고 말합니다.

그런데 Svelte는 가상 DOM을 사용하지 않습니다. 그러면 Svelte는 가상 DOM을 사용하는 다른 프레임워크들에 비해 현저히 느린걸까요? 그렇지 않습니다. 가상 DOM을 사용하는 방식은 가상 DOM, 실제 DOM 두 스냅샷을 비교하여 실제 DOM을 업데이트하는데 이 과정에서 어느정도의 오버헤드가 발생할 수 있습니다. 반면, Svelte는 컴파일러로써의 역할을 하여 빌드할 때 Vanilla JS 코드로 변환하여 빠르게 실제 DOM에 반영을 합니다.

### Truly reactive

React와 같은 여러 프레임워크들은 반응성을 보이기 위해 hook과 같은 상태 처리 수단을 요구합니다. 그에 반해, Svelte는 컴파일러이기 때문에 이러한 요소를 사용하지 않고도 hook을 사용하는 것처럼 코드를 작성해줍니다. 그렇게 반응성을 제공함으로써, 상태를 수동으로 업데이트하는 것에 대한 걱정할 필요가 없도록 만들어 주었습니다.

----

### 끝으로
Svelte는 React나 Vue 등에 비해 나온지도 얼마 되지 않아 Usage가 높지 않고 그만큼 reference도 부족해 개발 과정에서 막히는 부분이 있으면 검색을 통해 해결하기 쉽지 않다는 단점도 있습니다. 하지만 점점 각광받고 있는 만큼 이는 시간이 지나면 충분히 해결될 문제일 것이라 생각합니다. 아직 사용하는 기업이 찾기 힘들기 때문에 배워야할 필요성은 떨어질 수 있지만, 간단한 토이 프로젝트정도라면 시작해보는 것도 괜찮을 것 같습니다!
