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