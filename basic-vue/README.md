# 🐫 뷰 객체 만들기

## 🐫 뷰 설치

* [kr.vuejs.org](https://kr.vuejs.org/v2/guide/index.html) 에서 CDN소드 가져오기

* html에 로딩


---


## 🐫 뷰 객체 만들기 (01 뷰 인스턴스 생성하기) 

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


## 🐫 뷰객체의 프로퍼티

* 뷰 객체의 프로퍼티는 **data: { }** 에 작성할 수 있다.

* 뷰 객체의 프로퍼티를 html에서 사용하기 위해서는, **el** 에 해당하는 (DOM)요소 안에서 사용할 수 있다.

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


  ## 🐫 메서드 만들기

