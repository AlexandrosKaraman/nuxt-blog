<template>
  <div class="error">
    <div class="error__layout">
      <h1 class="error__title">Ошибка 404</h1>
      <nuxt-link class="error__link" to="/">Вернуться на главную страницу</nuxt-link>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.error {

  &__layout {
    display: grid;
    justify-items: center;
    grid-gap: 20px;

    padding-top: 100px;

  }

  &__title {
    color: rgb(197, 5, 5);
  }

  &__link {
    text-decoration: none;
  }

  &__link:hover {
    opacity: .8;
    cursor: pointer;
  }
}
</style>