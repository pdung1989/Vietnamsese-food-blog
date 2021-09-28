<template>
  <header class="main-header">
    <nav class="main-nav">
        <nuxt-link to="/" class="nav-link"><a>All Posts</a></nuxt-link>
        <nuxt-link to="/about" class="nav-link"><a>About</a></nuxt-link>
    </nav>
  </header>
</template> 


<style scoped>
  .main-header {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    background: rgb(136, 233, 225);
    height:70px;
  }

  .main-nav {
    list-style: none;
    margin: 0;
    padding: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
  }

  .nav-link {
    display: block;
    text-decoration: none;
    color: rgb(8, 62, 59);
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 0 10px;
    padding: 10px;
    font-size: 1.2rem;
  }

  .nav-link a:hover,
  .nav-link a:active,
  .nav-link.nuxt-link-exact-active a {
    color: rgb(150, 12, 122);
  }

.nav-link.nuxt-link-exact-active {
  border-bottom: 3px solid rgb(150, 12, 122);
}

</style>