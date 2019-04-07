<template lang="pug">
  .sidebar(:style='sidebarStyle', :data-color='backgroundColor', :data-image='backgroundImage')
    .sidebar-wrapper
      .logo
        a.simple-text.logo__container(href='#')
          .logo-img
            img(src='img/logo.png', alt='')
          | {{title}}
      slot(name='content')
      ul.nav.nav-main__links
        // By default vue-router adds an active class to each route link. This way the links are colored when clicked
        slot
          sidebar-link(v-for='(link,index) in sidebarLinks', :key='link.name + index', :to='link.path', @click='closeNavbar', :link='link')
            i(:class='link.icon')
            p {{link.name}}
  
</template>

<script>
  import SidebarLink from './SidebarLink.vue'

  export default {
    components: {
      SidebarLink
    },
    props: {
      title: {
        type: String,
        default: 'Eu tenho futuro?'
      },
      backgroundColor: {
        type: String,
        default: 'black',
        validator: (value) => {
          let acceptedValues = ['', 'blue', 'azure', 'green', 'orange', 'red', 'purple', 'black']
          return acceptedValues.indexOf(value) !== -1
        }
      },
      backgroundImage: {
        type: String,
        default: 'https://guia-static.gazetadopovo.com.br/fichas/9728/9728-a67f0d39a6801727948ef2920417bc6e-6868f8c335e457dd2af0a1332de903f1.jpg'
        // default: 'img/sidebar-5.jpg'
      },
      activeColor: {
        type: String,
        default: '#ff0000'
        
      },
      sidebarLinks: {
        type: Array,
        default: () => []
      },
      autoClose: {
        type: Boolean,
        default: true
      }
    },
    provide () {
      return {
        autoClose: this.autoClose
      }
    },
    computed: {
      sidebarStyle () {
        return {
          backgroundImage: `url(${this.backgroundImage})`
        }
      }
    }
  }

</script>
<style>
  .sidebar .sidebar-wrapper {
    display: flex;
    flex-direction: column;
  }
 .sidebar .nav-main__links {
   flex: 1;
 }
 .sidebar .sidebar-wrapper .logo .logo__container {
   padding-left: 10px;
 }
</style>
