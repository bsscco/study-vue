# 참고

[[1편]](https://velopert.com/3044), [[2편]](https://velopert.com/3095), [[3편]](https://velopert.com/3118), [[4편]](https://velopert.com/3136), [[5편]](https://velopert.com/3148)

# 설명

**v-text**

태그 content를 Vue 인스턴스의 data로 설정한다. 

**v-html**

태그 content를 Vue 인스턴스의 data로 설정한다. v-text와 다른 점은 content를 raw-html로 인식하게 한다는 것이다.

**v-show**

태그를 보여줄지 말지를 Vue 인스턴스의 data로 결정한다. html의 display속성고 같은 기능

**v-if**

태그를 생성할지 말지를 Vue 인스턴스의 data로 결정한다. v-show와 달리 태그를 조건에 따라 생성하거나 생서하지 않는다.

**v-else-if**

v-if 조건이 false이면 v-else-if 조건이 평가된다. 같은 형제태그 사이에서 사용된다.

**v-else**

v-if, v-else-if의 조건이 false이면 v-else 조건이 평가된다.

**v-pre**

디렉티브를 무시고, 머스태쉬{{}} 구문을 raw하게 보여준다.

**v-cloak**

Vue 인스턴스가 제대로 준비될 때까지 태그를 숨겨준다.

**v-once**

태그가 딱 한 번만 렌더링 되도록 한다.

**v-bind**

태그 property를 Vue 인스턴스의 data로 설정한다.

**v-for**

태그를 반복적으로 생성해준다.

**v-model**

form과 관련된 입력 태그의 입력값을 Vue 인스턴스의 data로 설정한다. 또는 입력값이 바뀌면 Vue 인스턴스의 data도 바뀐다. 양방향 데이터 바인딩

**v-on**

태그 이벤트의 리스너를 Vue 인스턴스의 methods로 설정한다. 


