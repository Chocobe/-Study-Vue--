# 🐫 7. Vue객체의 watch 속성

* Vue객체의 ``watch`` 속성은, Vue객체의 프로퍼티의 변경을 감지하여 동작한다.

* 프로퍼티의 변경감지 대상의 이름과 동일한 **메서드형식**으로 작성한다.

* 해당 프로퍼티의 값이 변경되면, 해당 ``watch``가 동작된다.

* 공식홈페이지에서는 ``watch``는 ``computed``를 사용할 수 없을때만 사용하길 권장한다.

  ```html
    <body>
      <div id="myApp">
        <p>{{ message }}</p>

        <button @click="changeMessage()">값변경</button>

        <p>{{ updated }}</p>
      </div>
    </body>
  
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    <script type="text/javascript">
      new Vue({
        el: "#myApp",

        data: {
          message: "Hello",
          updated: "아니요"
        },

        methods: {
          changeMessage() {
            this.message = "코지코더";
          }
        },

        watch: {
          // property명과 동일한 이름으로 만들어야 한다.
          // 해당 프로퍼티가 변경되면, 해당 메서드를 callback으로 호출한다.
          message(newValue, oldValue) {
            this.updated = "네";
            console.log(`newValue: ${newValue}, oldValue: ${oldValue}`);
            alert(`newValue: ${newValue}, oldValue: ${oldValue}`);
          }
        }
      });
    </script>
  ```