# 🐫 뷰 객체 만들기

## 🐫 뷰 설치

* [kr.vuejs.org](https://kr.vuejs.org/v2/guide/index.html) 에서 CDN소드 가져오기

* html에 로딩


---


## 🐫 뷰 객체 만들기 (1. 뷰 인스턴스 생성하기)

* Vue객체는 ``<script>``에서 생성하여 사용할 수 있다.

  ```javascript
    <body>
      <div id="app">
        이름 : {{ name }}
      </div>
    
      <script src="https://cdn.jsdelivr.net/npm/vue"></script>
      <script>
        new Vue({
          el: "#app",
          data: {
            name: "코지 코더"
          }
        });
      </script>
    </body>
  ```


  ---


## 🐫 뷰객체의 프로퍼티 (2. 뷰 데이터와 메서드)

* 뷰 객체의 프로퍼티는 **data: { }** 에 작성할 수 있다.

* 뷰 객체의 프로퍼티를 html에서 사용하기 위해서는, **el** 에 해당하는 (DOM)요소 안에서 **{{ 프로퍼티명 }}** 로 가져올 수 있다.

* 뷰 객체의 프로퍼티는 내부에 또다른 프로퍼티를 가질 수 있다. (``data: { person: { name: "코지코더" }}``)

  ```javascript
    <body>
      <div id="app">
        이름 : {{ person.name }}
        나이 : {{ person.age }}
      </div>
    
      <script src="https://cdn.jsdelivr.net/npm/vue"></script>
      <script>
        new Vue({
          el: "#app",
          data: {
            person: {
              name: "코지코더",
              age: 34
            }
          }
        });
      </script>
    </body>
  ```


  ---


  ## 🐫 메서드 만들기  (2. 뷰 데이터와 메서드)

* 뷰 객체는 메서드(함수)를 가질 수 있다.

* 뷰 객체의 메서드는 **methods: { }** 에 작성할 수 있다.

* 작성한 메서드를 html에서 사용하기 위해서는, **el** 에 해당하는 (DOM)요소 안에서 **{{ 메서드명(인자) }}** 로 사용할 수 있다.

  * ``{{ 메서드명() }}``의 형식에서 ``()``를 사용하지 않으면, 메서드의 동작이 아닌, 구현내용이 출력된다. (callback함수 호출과 유사)
  
  ```javascript
    <body>
      <div id="app">
        이름 : {{ person.name }}
        나이 : {{ person.age }}
      </div>
    
      <script src="https://cdn.jsdelivr.net/npm/vue"></script>
      <script>
        new Vue({
          el: "#app",
          data: {
            person: {
              name: "코지코더",
              age: 34
            }
          },
          methods: {
            nextYear: function() {
              // "this"키워드를 사용해야지만 뷰객체의 프로퍼티에 접근할 수 있다.
              return this.person.age + 1;
            },

            // function키워드는 생략할 수 있다.
            otherMethod() {
              return "Called method";
            }
          }
        });
      </script>
    </body>
  ```


---


## 🐫 html 요소(Element)의 속성에 데이터 바인딩 하기 (3. 데이터 바인딩)

* html 요소(Element)의 몸체(body)부분에 Vue객체 프로퍼티를 바인딩 할 때는, **{{ 프로퍼티명 }}** 형식으로 사용한다.

* html 요소(Element)의 속성(attribute)에 Vue객체 프로퍼티를 바인딩 할 때는, 속성명을 **Vue방**식으로 작성해야 한다.
  
  ```javascript
    <body>
      <div id="app">
        <input v-bind:type="type" v-bind:value="config.inputValue">
        <input :type="type" :value="config.inputValue">
      </div>
    
      <script src="https://cdn.jsdelivr.net/npm/vue"></script>
      <script>
        new Vue({
          el: "#app",
          data: {
            type: "text",
            config: {
              inputValue: "Hello Vue"
            }
          }
        });
      </script>
    </body>
  ```
  
* ``v-bind:태그의속성명="뷰객체의 프로퍼티명"`` 형식으로 사용할 수 있다.

* ``v-bind:태그의속성명="뷰객체의 프로퍼티명"`` 형식을 축약하면, ``:태그의속성명="뷰객체의 프로퍼티명"`` 형식으로 사용할 수 있다.

  > html 요소(Element)의 몸체(body)와 속성(attribute)에 바인딩하는 방식이 다르다.


---


## 🐫 (4. 이벤트)

* 이벤트란, 어떤 트리거(동작)이 발생하였을 때 취할 동작을 말한다.

* html의 요소(Element)의 이벤트를 설정할 때는 ``<태그 onclick="메서드();">``의 형식으로 사용했다.

* Vue에서는 ``<태그 v-on:click="메서드();">``의 형식으로 사용할 수 있다.

  ```javascript
    <body>
      <div id="myApp">
        <button v-on:click="myMethod();">버튼</button>
      </div>

      <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
      <script type="text/javascript">
        new Vue({
          el: "#myApp",

          data: {
            year: 2020
          },

          methods: {
            myMethod() {
              alert("Hello Vue~~~");
            }
          }
        });
      </script>
    </body>
  ```

* 기존 html의 ``<form>``태그에는 ``submit``이라는 속성이 없지만, Vue에서는 ``<태그 v-on:submit="메서드();">`` 형식으로 submit동작을 script 메서드로 **대체**할 수 있다.

  ```javascript
    <body>
      <div id="myApp">
        <p>Year값: {{ year }}</p>
        <button v-on:click="plus();">더하기</button>
        <button v-on:click="minus();">빼기</button>

        <form v-on:submit="mySubmit();">
          <button type="submit">전송</button>
        </form>
      </div>

      <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
      <script type="text/javascript">
        new Vue({
          el: "#myApp",

          data: {
            year: 2020
          },

          methods: {
            plus() {
              this.year++;
            },
            minus() {
              this.year--;
            },
            mySubmit() {
              alert("제출합니다");
            }
          }
        });
      </script>
    </body>
  ```

* ``<form>``태그의 ``submit``동작은 기본적으로 페이지를 리로드 하는데, 리로드를 하지 않기 위해서는 javascript의 ``event.preventDefault();``를 호출해야 한다.

* Vue에서는 호출하는 이벤트에 **수식어** 를 사용하여, 이벤트에 대한 처리방식을 설정할 수 있다.

  ```javascript
    <form v-on:submit.prevent="my메서드();">
  ```