<template>
  <div class="cc-df-warp">
    
    <div v-for="(item,index) in items" :key="index">
     <md-card>
      <md-card-media-cover md-solid>
        <md-card-media md-ratio="4:3">
          <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcQt7oqzyglV158gzNlhn-KRU1qQHs8_c-2-_s8B0rwffoWC_lD2&usqp=CAU" alt="Skyscraper">
        </md-card-media>

        <md-card-area>
          <md-card-header>
            <button class="cc-btn del-btn" @click="dele(index)">删除</button>
            <span class="font">音乐分区管理</span>
          </md-card-header>
        </md-card-area>
      </md-card-media-cover>
    </md-card>
    </div>
  </div>
</template>

<script>
export default {
 name: 'Index',
  data() {
    return {
     items:[1,2,3]
    }
  },
  components: {},
  created() {},
  mounted() {},
  methods: {
    dele(index){
        this.items.splice(index,1)
    }
  },
  computed: {}
}
</script>

<style scoped lang="scss">
    .md-card {
    width: 320px;
    margin: 4px;
    display: inline-block;
    vertical-align: top;
  }
  .del-btn{
    width: 50px;
    height: 20px;
  }
  .font{
    color: white;
    margin-top: 20px;
  }
</style>
