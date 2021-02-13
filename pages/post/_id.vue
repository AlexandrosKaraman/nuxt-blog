<template>
  <article class="post">
    <header class="post__header">
      <div class="post__title">
        <h1>Post title</h1>
        <nuxt-link to="/">
          <i class="el-icon-back"></i>
        </nuxt-link>
      </div>
      <div class="post__info">
        <small>
          <i class="el-icon-time"></i>
          {{ new Date().toLocaleString() }}
        </small>
        <small>
          <i class="el-icon-view"></i>
          42
        </small>
      </div>
    <div class="post__image">
      <img src="https://i2.wp.com/itc.ua/wp-content/uploads/2017/11/Justice-League.jpg?" alt="post img">
    </div>
    </header>

    <main class="post__content">
      <p>Первый уикэнд проката «Лиги справедливости» / Justice League оказался худшим 
        стартом среди всех пяти фильмов киновселенной DC Extended Universe. Фильм с 
        бюджетом $300 млн, впервые собравший вместе главных супергероев DC, получил всего
         $94 млн на основном для себя рынке США, впервые для серии не преодолев отметку
          в $100 млн. Несмотря на надежды студии Warner Bros. получить как минимум $110 млн,
           фильм показал только восьмой лучший старт в текущем году и 56-ое месте в аналогичном
            рейтинге за все годы.</p>
            <br>
      <p>Если сравнивать с собратьями по DC Extended Universe, то по старту в США «Лига
        справедливости» не смогла превзойти даже «Чудо-Женщину» / Wonder Woman 
        ($103,3 млн) и «Человека из стали» / Man of Steel ($116,6 млн), не говоря уже о
         достаточно коммерчески успешных «Отряде самоубийц» / Suicide Squad ($133,7 млн) и
          «Бэтмен против Супермена: На заре справедливости» / Batman v Superman: Dawn of
           Justice ($166 млн). Интересно, что ситуация по итогам проката для четверки DC 
           поменялась, первое место в итоге взяла «Чудо-Женщина» с показателем $412 млн, 
           хотя ее старт был самым слабым до выхода «Лиги справедливости».</p>

   </main>
   <footer>
     <app-comment-form
     v-if="canAddComment"
     @created="createCommentHandler"

     />

     <div class="post__comments" v-if="true">
       <app-comment
       v-for="comment in 4"
       :key="comment"
       :comment="comment"
        />
     </div>
     <div class="text-center" v-else>Коментариев нет</div>
   </footer>
  </article>
</template>

<script>
import AppComment from '../../components/main/Comment'
import AppCommentForm from '../../components/main/CommentForm'

export default {
  data() {
    return{
      canAddComment: true
    }
  },
  methods: {
    createCommentHandler() {
      this.canAddComment = false
    }
  },
  validation({params}) {
    return Boolean(params.id)
  },

  components: {
    AppComment,
    AppCommentForm,

  }
}
</script>

<style lang="scss" scoped>
  .post {
    max-width: 600px;
    margin: 0 auto;

    &__title {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 1rem;
    }

    &__info {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: .5rem;
    }

    &__image img {
      height: auto;
      width: 100%;
    }

    &__header {
      padding-bottom: 1.5rem;
    }

    &__content {
      padding-bottom: 2rem;
    }
  }
</style>