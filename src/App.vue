<template>

  <div id="login">
  <img src="./assets/logo.png" >
      <h1>Welcome to Your Vue.js App</h1>
      <h2>shangri-la tools</h2>
    <form>
      <label for="username">用户名</label><input type="text" v-model.trim="loginData.username" name="username">
      <label for="password">密码</label><input type="password" v-model.trim="loginData.password" name="password">
      <input type="button" value="登录" @click="doLogin">
    </form>
  </div>
</template>

<script>
import utils from "./utils/utils"
export default {
  name: 'login',
  data () {
    return {
      loginData: {
      username:"",
      password:""
      }
    }
  },
  methods:{
    doLogin(){
      let success=(response)=>{
        alert(response.data.msg);
      }
      utils.axiosMethod({
        method:"POST",
        url:"/user/login/",
        data:this.loginData,
        callback:success
      })
    }
  }
}
</script>


<style lang="scss">
#login {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
