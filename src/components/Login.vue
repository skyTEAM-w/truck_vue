<script setup>
export default {
  name: 'Login',
  data() {
    return {
      loginForm: {
        username:'',
        password:''
      },
      respondResult: []

    }
  },
  methods: {
    login () {
      this.$axios
          .post('/login', {
            username: this.loginForm.username,
            password: this.loginForm.password
          })
          .then(successResponse => {
            if (successResponse.data.code === 200) {
              this.$router.replace('/hall')
            }
          })
          .catch(failResponse => {

          })
    }
  }
}
</script>

<template>
  <div class="login-container">
    <h2>登录</h2>
    <form>
      <input type="text" placeholder="用户名" name="user_name" required>
      <input type="password" placeholder="密码" name="password" required>
      <button id="Login-btn" type=submit>登录</button>
      <button id="Register-btn" onclick="Register()">注册</button>
    </form>
  </div>

  <button id="Hall-btn" onclick="BackToHall()">
    返回大厅!
  </button>
</template>

<style scoped>

</style>