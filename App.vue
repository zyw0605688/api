<template>
  <div id="app">
    <h3>在线查询手机号码归属地</h3>
    <input type="text" placeholder="请输入手机号码" v-model="num">
    <button @click="chaxun">查询</button>
    <p>归属地是：<span v-model="out">{{out}}</span></p>
    <hr>
    <jiazhao></jiazhao>
    <hr>
    <province></province>
  </div>
</template>
<script>
  import jiazhao from '@/components/jiazhao'
  import province from '@/components/province'
export default {
  name: 'App',
  components:{
    jiazhao,province
  },
  data:function(){
    return{
      num:"1556563",
      out:"",
    }
  },
  methods:{
    chaxun:function () {
      this.axios.get('http://api.apishop.net/communication/phone/getLocationByPhoneNum?apiKey=kdsX4Bb92a9cfe7d3595e9cb439df676f89800e376f9768&phoneNum='+this.num)
      /*this.axios.post('/communication/phone/getLocationByPhoneNum', {
        apiKey: "kdsX4Bb92a9cfe7d3595e9cb439df676f89800e376f9768",
        phoneNum: this.num
      })*/
        /*.then(function (res) {
          console.log(res.data.result.province+"省"+res.data.result.city+"市");
          this.dayinjieguo=res.data.result.province;
        })
        .catch(function (err) {
          console.log(err);
        });*/
        .then((res)=>{
          console.log(res.data.result.province+"省"+res.data.result.city+"市");
          this.out=res.data.result.province+"省"+res.data.result.city+"市";
        })
        .catch((ero)=>{
          console.log(err);
        })
    },//chaxun结束
  }//methods结束
}
</script>

<style>
  #app{
    width: 300px;
    margin: 0 auto;
    padding-top: 100px;
  }
h3 {
  color:lightskyblue;
}
</style>
