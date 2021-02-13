<template>
  <div class="comment">
    <div class="comment__header">
      <span>Person name</span>
      <span>
        <i class="el-icon-time"></i>
        {{ new Date().toLocaleString() }}
      </span>
    </div>
    <div class="comment__text">
      Lorem ipsum dolor sit amet consectetur
    </div>
  </div>
</template>

<script>
export default {
  props: ['comment']
}
</script>

<style lang="scss" scoped>
.comment {
  margin-bottom: 1rem;

  border: 1px solid rgb(255, 255, 255);
  border-radius: 10px;
  padding: 10px;
  box-shadow: 0 0 3px rgb(88, 88, 88);
  cursor: pointer;


  &__header {
    display: flex;
    justify-content: space-between;
    margin-bottom: 0.5rem;
    font-size: .8rem;
  }

  &__text {
    white-space: pre-line;
  }
}
</style>