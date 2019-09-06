<template>
  <div class="error">
    <h2> 404 搜索页面不存在</h2>
<!--    <el-button type="success" @click="startDivi()"></el-button>-->
    <el-button
      type="primary"
      @click="openFullScreen"
      v-loading.fullscreen.lock="fullscreenLoading">
      返回home页面
    </el-button>
  </div>
</template>

<script>
  export default {
      data() {
          return {
              // count:"",//倒计时
              fullscreenLoading: false
          }
      },
      // methods: {
      //     startDivi(){
      //         const TIME_COUNT = 3;
      //         if(!this.timer){
      //             this.count = TIME_COUNT;
      //             this.show = false;
      //             this.timer = setInterval(()=>{
      //                 if(this.count > 0 && this.count <= TIME_COUNT){
      //                     this.count--;
      //                 }else{
      //                     this.show = true;
      //                     clearInterval(this.timer);
      //                     this.timer = null;
      //                     //跳转的页面写在此处
      //                     this.$router.push({
      //                         path: '/'
      //                     });
      //                 }
      //             },1000)
      //         }
      //     },
      // }

      methods: {
          openFullScreen() {
              const loading = this.$loading({
                  lock: true,
                  text: '拼命加载中',
                  spinner: 'el-icon-loading',
                  background: 'rgba(0, 0, 0, 0.7)'
              });
              setTimeout(() => {
                  this.$router.push({path: "/"}); // 强制切换当前路由 path
                  loading.close();
              }, 1000);
          }
      }

  }
</script>

<style scoped>

</style>
