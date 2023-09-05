<template>
  <div>
    <nav v-if="$route.name=='home'|| $route.name =='about'">
      <div>
      <h1 style="font-size: 20px; font-family:'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif">Online store</h1>
    </div>
    <div>
      <router-link style="font-size: 18px" to="/">Products</router-link> |
      <router-link style="font-size: 18px" to="/about">About</router-link>
    </div>
    </nav>
    <router-view />
</div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
button {
  background-color: #42b983;
  color: #fff;
  border: none;
  font-weight: 600;
  border-radius: 3px;
  padding: 10px 25px;
  font-size: 14px;
  height: 40px;
  white-space: nowrap;
  
}
a{
  outline: none; 
  text-decoration: none; 
  color: #fff;
  font-size: 14px; 
  font-family:'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
}
nav {
  display: flex;
  padding: 150px;
  padding-top: 30px;
  justify-content: space-between;
  align-items: center;
  padding-bottom: 30px;
}
@media only screen and (max-width: 750px){
  nav {
    display: flex; 
    flex-direction: column;
    padding: 30px;
  }
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
