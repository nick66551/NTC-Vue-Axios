<template>

  Name: <input type="text" v-model="name">
  Job: <input type="text" v-model="job">
  <button @click="updateTitle">Update Title</button>
  <hr>
  id: <input type="text" v-model="id">
  <button @click="updateTitleByApi">Update Title By Api</button>
  <h3>{{ fullTitle }}</h3>

  <nav>
    <li v-for=" i in 10" :key="i">
      <router-link :to="`/users/${i}`">使用者: {{ i }}</router-link>
    </li>
  </nav>
  <router-view/>
</template>
<script>
export default {
  name: 'App',
  computed:{
    fullTitle(){
      return this.$store.getters.fullTitle;
    }
  },
  methods:{
    updateTitle(){
      this.$store.commit('setTitle', {
        name: this.name,
        job: this.job
      })
    },
    updateTitleByApi(){
      this.$store.dispatch('setTitleByApi', { id: this.id })
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
