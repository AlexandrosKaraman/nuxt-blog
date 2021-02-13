<template>
  <h1>logout</h1>
</template>

<script>
export default {
  layout: 'admin',
  middleware: ['admin-auth'],
  beforeCreate() {
    this.$store.dispatch('auth/login')
    this.$router.push('/admin/login?message=logout')
  }
}
</script>

<style>

</style>