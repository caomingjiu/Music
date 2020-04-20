<template>
  <div>
    <div class="index-header cc-shadow">
      <div class="cc-df-between">
        <div class="left"><i class="iconfont cc-btn">&#xe610;</i></div>
        <div class="right">
        <i class="iconfont cc-btn">&#xe6e4;</i>
        <i class="iconfont cc-btn">&#xe611;</i>
        <i class="iconfont cc-btn" @click="logout()">&#xe603;</i>
      </div>
      </div>
    </div>
     <!-- <router-link :to="menu.url"> -->
    <div class="cc-df">
        <div class="person-card">
          <div class="person-card-header cc-df">
              <img :src="user.avatar" alt="头像">
              <div class="cc-col cc-mleft">
                <p>昵称：{{user.username}}</p>
                <p class="cc-mtop">职位：{{user.userRole}}</p>
              </div>
          </div>
          <div class="person-card-body cc-col">
              <div v-for="(item,index) in items" :key="index">
                <div @click="show(item.isshow,index)" class="cc-btn">
                  <MenuCard :item="item"></MenuCard>
                </div>
                <div v-for="(item1,index1) in item.subMenus" :key="index1" >
                  <SubMenuCard :item1="item1" v-if="item.isshow"></SubMenuCard>
                </div>
              </div>
          </div>
        </div>
        <div class="index">
          <router-view />
        </div>
    </div>
    
  </div>
</template>

<script>
export default {
 name: 'Layout',
  data() {
    return {
      user: this.$store.state.user,
      items: this.$store.state.menuList1,
      icon:'el-icon-delete'
    }
  },
  components: {
    MenuCard: require('../components/MenuCard.vue').default,
    SubMenuCard: require('../components/SubMenuCard').default
  },
  created() {},
  mounted() {},
  methods: {
    logout() {
      alert('logout')
      localStorage.removeItem('token')
      this.$store.commit('setUser', null)
      this.$router.push('/login')
    },
    show(isshow1,index){
        this.items[index].isshow=!isshow1
    }
  },
  computed: {}
}
</script>

<style scoped lang="scss">
.index-header{
  background: -webkit-linear-gradient(to bottom, #7bc6cc, #be93c5);
  background: linear-gradient(
    to bottom,
    #7bc6cc,
    #be93c5
  ); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
  opacity: 0.8;
  height: 7vh;
 
  padding-top: 10px;
}
.left i{
  font-size: 25px;
  margin-left: 15px;
}
.right i{
  font-size: 25px;
  margin-right: 15px;
}
.address{
  margin-left: 50px;
  margin-top: 60px
}
.person-card{
  width: 300px;
  height: 500px;
  border-radius: 10px;
  background-image:url('https://niit-student.oss-cn-beijing.aliyuncs.com/markdown/6QLLNY3GFWJCTU)Y~``BW8P.png');
  margin-left: 200px;
  margin-top: 30px;
}
.person-card-header{
  margin-left: 15px;
  margin-top: 25px;
}
.person-card-header img{
  border-radius: 50%;
  width: 70px;
  height: 70px;
  margin-top: -5px;
}
.index{
  margin-left: 120px;
  margin-top: 30px;
}
</style>
