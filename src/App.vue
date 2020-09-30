<template>
  <div class="container" id="app">
    <div class="row">
        <div class="col-12"><teg-user-profile></teg-user-profile></div>               
    </div>    
    <div class="row">
      <div class="col-12">
          <teg-blog-list></teg-blog-list>
        </div>
    </div>
  </div>
</template>

<script>

import UserProfile from './components/UserProfile.vue'
import BlogList from './components/BlogList.vue'

export default {
  name: 'app',
  data () {
      return {
      
      }
    },
    components: {
      'teg-user-profile': UserProfile,
      'teg-blog-list': BlogList
    }
  }

</script>