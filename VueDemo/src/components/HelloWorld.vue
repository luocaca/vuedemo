<template xmlns:v-on="http://www.w3.org/1999/xhtml">
  <div class="hello">


    <div style="float: left;padding: 8px;">
      <span>会员账号</span>
      <input type="text" placeholder="会员账号">
    </div>

    <div style="float: left;padding: 8px;">
      <span>确认账号</span>
      <input type="text" placeholder="确认账号">
    </div>


    <div style="clear: both;"></div>


    <router-link to="/Login"><a href="Login.vue">aaaaaaaa</a></router-link>


    <a href="https://blog.csdn.net/Mr_dong_ya_yun/article/details/80732714">input 文档</a>

    <div> ===={{game}}====</div>


    <button v-on:click="btnClick('穿越火线')">穿越火线</button>


    <button v-on:click="btnClick('我的世界')">我的世界</button>


    <button v-on:click="btnClick('角地求生')">绝地求生</button>

    <button @click="btnClick('斗地主')">斗地主</button>

    <button @click="btnClick('恰代码')">恰代码</button>


    <button @click="btnClick('hello')">hello</button>

    <button v-on:click="btnClick('我写的点击时间')">我写的点击时间</button>


    <ul>
      <li class="liMenu"
          :class="idx==index?'hover':''" @click="son(item,idx)" v-for="(item,idx) in menu"
          :key="idx">{{item}}
      </li>
    </ul>


  </div>


</template>

<script>
  export default {
    name: 'HelloWorld',
    data() {
      return {
        msg: '大傻入门hello vue',
        game: 'name',
        menu: ['100元', '200元', '300元', '400元', '500元', '请输入'],
        index: 0
      }
    },
    methods: {
      btnClick: function (pname) {
        this.game = pname;
      }, son(item, idx) {
        this.index = idx;
      }
    },
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h1, h2 {
    font-weight: normal;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  li {
    display: inline-block;
    margin: 0 10px;
  }

  a {
    color: #42b983;
  }

  .liMenu {
    margin-right: 20px;
    cursor: pointer;
  }

  .liMenu.hover {
    color: red;
  }

</style>
