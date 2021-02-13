<template>
  <el-card
    shadow="alwas"
    :style="{width: '500px'}"
  >
    <el-form 
      :model="controls" 
      :rules="rules" 
      ref="form"
      @submit.native.prevent="onSubmit"
      >
      <h2 class="tc">Войти в панель Администратора</h2>
      <el-form-item label="Логин" prop="login">
        <el-input v-model.trim="controls.login" />
      </el-form-item>

      <div class="mb2">
      <el-form-item label="Пароль" prop="password">
        <el-input v-model.trim="controls.password" type="password" />
      </el-form-item>
      </div>

      <el-form-item>
        <el-button 
        type="primary" 
        native-type="submit"
        round
        :loading="loading"
        >Войти</el-button>
      </el-form-item>
    </el-form>
  </el-card>
</template>

<script>
export default {
  layout: 'empty',
  data() {
    return{
      loading: false,
      controls: {
        login: '',
        password: '',
      },
      rules: {
         login: [
           { required: true, message: 'Тут должен быть логин', trigger: 'blur' },
        ],
         password: [
           { required: true, message: 'Незаметно введите пароль :)', trigger: 'blur' },
           { min: 6, message: 'Пароль должен быть не менее 6 символов',
           trigger: 'blur' }
        ]
      }
    }
  },
  mounted() {
    const {message} = this.$route.query
    switch (message) {
      case 'login':
        this.$message.info('Для начала ввойдите в систему')
        break
      case 'logout':  
        this.$message.success('Вы вышли из системы!')
        break
    }
  },
  methods: {
    onSubmit(){
      this.$refs.form.validate(async valid =>{
        if (valid) {
          this.loading = true

          try {
            const formData = {
              login: this.controls.login,
              password: this.controls.password,
            }
            // вызов токена action
            await this.$store.dispatch('auth/login', formData)
            this.$router.push('/admin')

          } catch(e) {
            this.loading = false
          }
        }
      })
    }
  }
  
}
</script>

<style>

</style>