<template>

  <div id="nav">
    <router-link to="/" >Home</router-link> |
    <router-link to="/users" >Employees</router-link>
  </div>
  <router-view/>
  
</template>

<script>

export default {
  name: 'App',
  components: {
    
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
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #4e4e4e;
}

#nav a.router-link-exact-active {
  color: #1ba4ff;
}
</style>
