<template>
  <main class="main-content">
    <UserPanel />
  </main>
</template>

<script>
import UserPanel from './components/User/UserPanel.vue';
export default {
  name: 'App',
  components: {
    UserPanel
  }
}
</script>

<style>
  .main-content {
    background-color: whitesmoke;
    }
    
    @media only screen and (min-width: 768px) {
      .main-content {
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 0 4%;
      }
    }
  
</style>
