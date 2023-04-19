<template>
  <div>
    <h2 class="">List of Users</h2>
    <button class="btn btn-dark" @click="changed()">New</button>
    <button class="btn btn-dark">Popular</button>
    <div v-if="score">
      <div class="card shadow-sm m-2" v-for="user in allUsers" v-bind:key="user.id">
        <p>{{ user.name }}</p>
      </div>
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import axios from 'axios'


export default {
    name: "App",
    data() {
        return {
            allUsers: [],
            score: true,
        };
    },
    beforeCreate() {
      console.log("Before Create")
    },
    created () {
      console.log("Created");
    },
    beforeMount () {

    },
    mounted() {
      this.getUsers();
    },
    
    methods: {
        getUsers() {
            let url = "https://jsonplaceholder.typicode.com/users";
            axios.get(url).then((response) => {
                this.allUsers = response.data;
            });
        },
        changed () {
          if (this.score == true) {
            this.score = false;
          } else if (this.score == false) {
            this.score = true
          }
        }
    },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
