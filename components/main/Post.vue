<template>
  <div class="post">
<span class="post__title">
    <h3>Post header</h3>
    <small>{{ new Date().toLocaleString() }}</small>
</span>

  <div class="post__body">
    <img 
    class="post__img"
    src="https://i2.wp.com/itc.ua/wp-content/uploads/2017/11/Justice-League.jpg?"
    alt="Kyiv img"
     >
  </div>
  <footer class="post__footer">
    <button class="post__btn" round @click="openPost">Открыть</button>
    <span>
      <i class="el-icon-messege">22</i>
    </span>
  </footer>
  </div>
</template>

<script>
export default {
  methods: {
    openPost(){
      const id = 'test-id'
      this.$router.push(`/post/${id}`)
    }
  }
}
</script>

<style lang="scss" scoped>
.post {
    display: grid;
    grid-template-rows: 50px 320px 50px;
    grid-template-columns: 50% 50%;

    max-width: 1200px;
    height: 400px;
    width: 450px;
    margin: auto;
    margin-bottom: 2rem;
    border: 1px solid rgba(235, 235, 235, 0.667);
    border-radius: 10px;
    box-shadow: 0 0 3px rgba(139, 139, 139, 0.5);
    

  &__title {
    display: grid;
    width: 100%;
    grid-template-columns: 225px 225px;
    justify-items: center;
    align-items: center;
  }

  &__img {
    height: auto;
    width: 100%;
    
  }

  &__body {
    grid-column: 1/3;
  }

  &__btn {
    width: 100px;
    height: 25px;
    margin: -5px 10px 0px 10px;
    

    border: 1px solid rgb(167, 167, 167);
    border-radius: 40px;

    background-color: rgb(255, 255, 255);
    cursor: pointer;
  }

  &__btn:hover {
    opacity: .8;
    background-color: #4CAF50;
    color: white;
}

}

.post:hover {
  opacity: .9;
}
</style>