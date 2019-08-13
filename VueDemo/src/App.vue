<template>
  <div id="app">
    <!--<router-view/>-->

    <div style="background: dodgerblue;text-align: center;color: white;padding: 5px;">快速支付</div>

    <transition :name="transitionName">
      <keep-alive :include="keepAlive">
        <router-view class="Router"></router-view>
      </keep-alive>
    </transition>

  </div>


</template>


<script>
  export default {
    name: 'App',
    components: {},
    data() {
      return {
        keepAlive: 'main-keep-alive',  //需要缓存的页面 例如首页
        transitionName: 'slide-right', //初始过渡动画方向
      }
    },
    watch: {
      $route(to, from) {
        // 切换动画
        let isBack = this.$router.isBack // 监听路由变化时的状态为前进还是后退
        if (isBack) {
          this.transitionName = 'slide-left'
        } else {
          this.transitionName = 'slide-right'
        }
        this.$router.isBack = false
      }
    },
    methods: {}
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    width: 100%;
    height: 100%;
    max-width: 25rem;
    margin: auto;
    position: relative;
  }

  body{
    margin: 0px;
    padding: 0px;
  }

  .Router {
    position: absolute;
    transition: all .377s ease;
    will-change: transform;
    backface-visibility: hidden;
    perspective: 1000;
  }

  .slide-left-enter,
  .slide-right-leave-active {
    opacity: 0;
    transform: translate3d(-100%, 0, 0);
  }

  .slide-left-leave-active,
  .slide-right-enter {
    opacity: 0;
    transform: translate3d(100%, 0, 0);
  }

  /*链接：https://www.jianshu.com/p/7a35ec0df01e*/
  /*来源：简书*/
  /*简书著作权归作者所有，任何形式的转载都请联系作者获得授权并注明出处。*/
</style>
