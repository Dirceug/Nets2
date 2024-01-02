<template>
  <div>
    <NavBar 
      :logo="logo_src" 
      :alt="app_name" 
      :user="user_svg" 
      :heart="heart_svg" />   
    <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/desejos">Lista de desejos</router-link>
    </nav>
    <router-view />
  </div>
</template>

<script>
  import NavBar from "./components/navbar/NavBar.vue"
  // import router from './router';

  

  export default {
    components: {
      NavBar, 
    }, 
    data(){
      return {
        logo_src: "images/netshoes.jpg",
        app_name: "Netshoes",
        user_svg: "images/circle-user-solid.svg",
        heart_svg: "images/heart-regular.svg",
        cancel_svg: "images/x-solid.svg",
      }
    },
    methods: {
      handleView() {
        this.mobileView = window.innerWidth <=990;
      }
    },
    created() {
      this.handleView();
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
  text-decoration: none;
  margin: 20px;
  flex-wrap: nowrap;
}

nav:hover {
  color: white;
}

#navigation-icon{
  padding: 10px 10px 20px;
  margin-right: 10px;
  cursor: pointer;


}
i {
    font-size: 2rem;
    border: 2px solid black;
  }


</style>
