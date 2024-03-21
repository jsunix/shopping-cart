<template>
    <router-view/>
</template>




<script>
export default {
  name: 'App',
  created() {
    localStorage.setItem('authToken', 'false');

    this.$router.beforeEach((to, from, next) => {
      if (to.meta.requiresAuth && localStorage.getItem('authToken') !== 'true') {
        next('/');
      } else {
        next();
      }
    });
  }
};
</script>

