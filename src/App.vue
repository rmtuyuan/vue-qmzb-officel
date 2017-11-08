<template>
  <div id="app">
    
    <img src="./assets/logo.png" alt="全民直播－看直播,玩直播,尽在全民APP" style="position:absolute;left:-10000px">
    <video id="bgvideo" width="100%" height="100%" autoplay  src="http://content.rolex.com/is/content/Rolex/rolex_and_national_geographic_000117310152514447Mgq_iPad_640x360_800K"
      loop="" v-bind:style="styleObject">您的浏览器不支持video标签，建议更新浏览器版本</video>
    <div class="mask"></div>
    <div id="wrapper">
      <div class="header clearfix">
        <p class="logo fl"><img src="./assets/logo.png" alt="全民直播"></p>
        <ul class="nav fr clearfix">
        </ul>
      </div>
      <div class="cont">
        <p><img src="./assets/slogan.png" alt="上全民 直播我"></p>
        <ul>
          <li><a :href="appstoreid">IOS下载</a></li>
          <li><a :href="apkurl">Android下载</a></li>
          <li class="code pr s-qrcode"><span>扫码下载</span>
            <p id="qrcode"> <img src="./assets/down_qrcode.png" alt=""> </p>
          </li>
        </ul>
      </div>
      <div class="footer">
        <p class="doc"><a target="_blank" href="private.html">隐私政策</a> <a target="_blank" href="server.html">服务条款</a> <a target="_blank"
            href="contact.html">联系我们</a></p>

      </div>
     
    </div>
     
  </div>
</template>

<script>
import './css/normalize.min.css';
import './css/index.css'

  export default {
    name: 'app',
    data(){
      return {
        appstoreid:'',
        apkurl:'',
        styleObject: {
          width:'',
          height:''
        }
      }
    },
    created(){
      let url='http://139.199.23.160:8080/qmzb/script/getApk';
		  let appstore='https://itunes.apple.com/cn/app/id';
      let vw=this;
      let w = window.innerWidth || document.documentElement.clientWidth || document.body.clientWidth;
      let h = window.innerHeight || document.documentElement.clientHeight || document.body.clientHeight;
      this.styleObject.width=w+'px';
      this.styleObject.height=w/(16/9)+'px';
      this.$http.post(url).then(function (response) {                    
              vw.appstoreid= appstore+response.data.data[0].appStoreId;    
              vw.apkurl=response.data.data[0].apkUrl;   
        }).catch(function (erro) {
          //失败
        });
    },
    methods: {
      setVUEx: function () {
        // this.$store.commit('newAuthor', this.msg);
      }
    }
  }

</script>

<style>
  
</style>
