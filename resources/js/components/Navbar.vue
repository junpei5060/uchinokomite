<template>
  <nav class="navbar">
    <RouterLink class="navbar__brand" to="/">
      <img src="./3.png" alt="" class="log">
    </RouterLink>
    <div class="navbar__menu">
      <div v-if="isLogin" class="navbar__item">
        <div class="btn-cross" @click="showForm = ! showForm">
          <i class="icon ion-md-add"></i>
          うちの子をアップする
        </div>
      </div>
      <span v-if="isLogin" class="navbar__item">
        {{ username }}
      </span>
      <div v-else class="navbar__item">
        <RouterLink class="button button--link" to="/login">
          ログイン / 会員登録
        </RouterLink>
      </div>
    </div>
    <PhotoForm v-model="showForm" />
  </nav>
</template>

<script>
import PhotoForm from './PhotoForm.vue'

export default {
    components: {
    PhotoForm
  },
  data () {
    return {
      showForm: false
    }
  },
  computed: {
    isLogin () {
      return this.$store.getters['auth/check']
    },
    username () {
      return this.$store.getters['auth/username']
    }
  }
}
</script>

<style scoped>
  .navbar{
    background-color:#E2DFD7;
  }

  .log{
    width: 400px;
  }
  .navbar__menu{
    color:#ffa374;
    font-weight: bold;
  }

  .btn-cross {
  display: inline-block;
  position: relative;
  padding: 0.25em 1em;
  border-top: solid 2px #ffa374;
  border-bottom: solid 2px #ffa374;
  text-decoration: none;
  font-weight: bold;
  color: #ffa374;
}
.btn-cross:before, .btn-cross:after {
  content: '';
  position: absolute;
  top: -7px;
  width: 2px;
  height: -webkit-calc(100% + 14px);
  height: calc(100% + 14px);
  background-color: #ffa374;
  transition: .3s;
}
.btn-cross:before {
  left: 7px;
}
.btn-cross:after {
  right: 7px;
}
.btn-cross:hover:before {
  top: 0px;
  left:0;
  height: 100%;
}
.btn-cross:hover:after {
  top: 0px;
  right: 0;
  height: 100%;
}
</style>