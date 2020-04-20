<template>
  <div class="bg">
    <div class="login-card">
      <h1>音乐登录</h1>
      <el-input placeholder="请输入内容" class="login-input" v-model="mobileInput" clearable></el-input>
      <el-input placeholder="请输入密码" class="login-input" v-model="passwordInput" show-password></el-input>
      <el-switch
  v-model="value"
  active-color="#13ce66"
  inactive-color="#ff4949"
   active-text="记住密码"
   class="cc-mtop"
   style="margin-left:-52%"
   >
</el-switch>
      <div class="cc-df cc-mtop">
           <el-button type="primary" plain class="btn-login" @click="submit()">登录</el-button>
           <el-button type="primary" plain class="btn-login address" @click="clear">重置</el-button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Login",
  data() {
    return {
      mobileInput:'',
      passwordInput:'',
      value: true
    };
  },
  components: {},
  created() {},
  mounted() {},
  methods: {
        openSimpleDialog() {
      this.openSimple = true
    },
    closeSimpleDialog() {
      this.openSimple = false
    },
    submit() {
        //模拟后端接口数据
        let user = {
          userId: '2000100193',
          username: 'cmj',
          userRole: '超管',
          avatar: 'https://public-cdn-oss.mosoteach.cn/avatar/2019/65/a8423b81c3b1442d7fcea9f80d92e98c.jpg?v=1552961440&x-oss-process=style/s100x100'
        }
        menuList1: [
      { title: '主页', icon: 'el-icon-s-home', url: '/index', isshow:false, subMenus: [] },
      {
        title: '音乐管理',
        icon: 'el-icon-headset',
        url: '',
        isshow:false,
        subMenus: [
          {
            title: '歌单管理',
            icon: 'el-icon-headset',
            url: '/music-list',
            permissions: []
          },
          {
            title: '歌曲管理',
            icon: 'el-icon-s-data',
            url: '/music',
            permissions: ['music:add', 'music:edit']
          }
        ]
      },
      {
        title: '权限管理',
        icon: 'el-icon-s-grid',
        url: '',
        isshow: false,
        subMenus: [
          {
            title: '角色管理',
            icon: 'el-icon-s-custom',
            url: '/role',
            permissions: ['role:add', 'role:delete']
          },
          {
            title: '菜单管理',
            icon: 'el-icon-s-unfold',
            url: '/menu',
            permissions: ['menu:add', 'menu:edit', 'menu:delete']
          }
        ]
      },
      { title: 'Help', icon: 'el-icon-help', url: '/about', isshow: false, subMenus: [] }
    ]
        localStorage.setItem('token', 'EcIHTAWoGrmMVvTu2LPvuL-siq6hAfieVeehl-HTe_M')
        localStorage.setItem('user', JSON.stringify(user))
        localStorage.setItem('menuList', JSON.stringify(this.menuList1))
        this.$store.commit('setToken', 'EcIHTAWoGrmMVvTu2LPvuL-siq6hAfieVeehl-HTe_M')
        this.$store.commit('setUser', user)
        this.$store.commit('setMenuList', this.menuList1)
        this.$router.push('/')
    },
    clear() {
      this.$refs.form.clear()
      this.validateForm = {
        username: '',
        password: '',
        isAgree: false
      }
    }
  },
  computed: {}
};
</script>

<style scoped lang="scss">
.bg {
  background: -webkit-linear-gradient(to bottom, #7bc6cc, #be93c5);
  background: linear-gradient(
    to bottom,
    #7bc6cc,
    #be93c5
  ); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
  opacity: 0.8;
  height: 100vh;
  display: flex;
  justify-content: center;
}
.login-card {
  background-color: whitesmoke;
  width: 30%;
  height: 45%;
  margin-top: 12%;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 15px;
}
.login-input{
  width: 80%;
  margin-top: 5.5%;
}
.btn-login{
  width: 100px;
  height: 40px;
}
.address{
  margin-left: 100px;
}
</style>
