<template lang="pug">
  .wrapper
    side-bar
      mobile-menu(slot='content')
      sidebar-link(to='/admin/overview')
        img(src='https://img.icons8.com/dusk/64/000000/home-page.png')
        p HOME
      sidebar-link(to='/admin/user')
        img(src='https://img.icons8.com/dusk/64/000000/for-experienced.png')
        p DESAFIOS
    .main-panel
      top-navbar
      //- dashboard-content(@click='toggleSidebar')
  
</template>


<style lang="scss">
p{
  padding-left: 2vw;
}
</style>
<script>
  import TopNavbar from './TopNavbar.vue'
  import ContentFooter from './ContentFooter.vue'
  import DashboardContent from './Content.vue'
  import MobileMenu from './MobileMenu.vue'
  export default {
    components: {
      TopNavbar,
      ContentFooter,
      DashboardContent,
      MobileMenu
    },
    methods: {
      toggleSidebar () {
        if (this.$sidebar.showSidebar) {
          this.$sidebar.displaySidebar(false)
        }
      }
    }
  }

</script>
