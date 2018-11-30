<template>
    <div>
      <button @click="provinceClick">点击console.log</button>
    </div>
</template>

<script>
    export default {
        name: "province",
      methods:{
        provinceClick() {
          var url = this.host + '/common/postcode/getAddrs?apiKey=kdsX4Bb92a9cfe7d3595e9cb439df676f89800e376f9768';
          /*this.axios.post(url,{
            apiKey: "kdsX4Bb92a9cfe7d3595e9cb439df676f89800e376f9768"
          })*/
          this.axios.get(url)
            .then(function (res) {
              console.log(res);
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
