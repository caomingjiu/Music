<template>
  <div class="card cc-df cc-mbottom">
    <div style="width:20px"><p>{{item.id}}</p></div>
    <div style="width:200px" class="cc-btn"><p>{{item.name}}</p></div>
    <div style="width:200px; margin-left:-30px"><p>{{item.author}}</p></div>
    <p style="margin-left:-50px">流行</p> 
    <el-button class="cc-btn del-btn"><p style="margin-top:-7px">删除</p></el-button>
  </div>
</template>

<script>
export default {
 name: 'MyMusic',
 props: ['item'],
  data() {
    return {

    }
  },
  components: {},
  created() {},
  mounted() {},
  methods: {},
  computed: {}
}
</script>

<style scoped lang="scss">
.card{
    width: 500px;
}
.img{
    width: 30px;
    height: 30px;
    margin-top: -5px;
    margin-left: 45px;
}
.del-btn{
  width: 70px;
  height: 20px;
  margin-left: 25px;
  margin-top: -3px;
}
</style>
