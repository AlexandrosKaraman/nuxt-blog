<template>
  <el-form 
        :model="controls" 
        :rules="rules" 
        ref="form"
        @submit.native.prevent="onSubmit"
        >

        <h1 class="tc">Создать новый пост</h1>

        <el-form-item label="Придумайте название поста" prop="title">
          <el-input
          v-model.trim="controls.title" 
          />
        </el-form-item>

        <el-form-item label="Текст в формате .md или html" prop="text">
          <el-input
          type="textarea"
          v-model.trim="controls.text" 
          resize="none"
          :rows="10"
          />
        </el-form-item>
        
        <el-form-item>
          <el-button 
          type="primary" 
          native-type="submit"
          round
          :loading="loading"
          >Создать пост</el-button>
        </el-form-item>
      </el-form>
  </template>

<script>
  export default {
    layout: 'admin',
    middleware: ['admin-auth'],
      data() {
    return{
      loading: false,
      controls: {
        title: '',
        text: ''
      },
      rules: {
         text: [
           { required: true, message: 'Поле не может быть пустым', trigger: 'blur' },
          ],
         title: [
           { required: true, message: 'Название поста не может быть пустым', trigger: 'blur' },
          ]
        }
      }
    },
    methods: {
      onSubmit() {
        this.$refs.form.validate(async valid => {
          if(valid){
            this.loading = true

            const formData = {
              title: this.controls.title,
              text: this.controls.text
            }

            try {
              await this.$store.dispatch('post/create', formData)
              this.controls.text=''
              this.controls.title =''
              this.$message.success("Пост успешно создан!")
              this.loading = false
            }catch(e){
              this.loading = false
            }
          }
        })
      }
    }
  }
</script>

<style lang="scss" scoped>
form {
  width: 600px;
}
</style>