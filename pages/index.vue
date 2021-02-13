<template>
 <div>
   <app-post
   v-for="post in 3"
   :key="post"
    />
 </div>
</template>

<script>
import AppPost from '../components/main/Post'

export default {

  components: {
    AppPost
  }
}
</script>

<style>

</style>
