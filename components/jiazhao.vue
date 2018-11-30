<template>
  <div id="app">
    <h3>驾考题库在线查询</h3>
    <p>
      请选择考试科目：
      <select v-model="subject">
        <option value="1">科目一</option>
        <option value="2">科目二</option>
        <option value="3">科目三</option>
      </select>
    </p>
    <p>
      请选择驾照类型：
      <select v-model="model">
        <option value="c1">c1</option>
        <option value="c2">c2</option>
        <option value="b1">b1</option>
        <option value="b2">b2</option>
      </select>
    </p>
    <button @click="cha">查询</button>
  </div>
</template>

<script>
    export default {
        name: "jiazhao",
      data:function () {
        return{
          subject:1,
          model:"c1"
        }
      },
      methods:{
        cha:function () {
          this.axios.get('http://api.apishop.net/transport/exam/getQuestions?apiKey=kdsX4Bb92a9cfe7d3595e9cb439df676f89800e376f9768&subject='+this.subject+'&model='+this.model)
            .then(function (res) {
              console.log(res.data.result[0]);
              //res.data.result[0]
            })
            .catch(function (err) {
              console.log(err);
            });
        }
      }
    }
</script>

<style scoped>

</style>
