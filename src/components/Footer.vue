<template>
  <footer>
      <p>Copyright &copy; 2021</p>
      <!-- <a href="/about">About us</a> -->
      <router-link to="/about"><strong><u>About us</u></strong></router-link>
  </footer>
</template>

<script>
export default {
    name: 'Footer',
}
</script>

<style scoped>
    a{
        color: green;
    }
    footer{
        margin-top: 10%;
        text-align: center;
    }
</style>