<template>    
  <div class="card mb-3" style="max-width: 540px;">
      <div class="row no-gutters" v-if="!show" style="">
        <div class="col-md-4">
          <img :src="content.images" class="card-img" alt="..." width="250px">
        </div>
        <div class="col-md-8">
          <div class="card-body">
            <h5 class="card-title">{{content.heading}}</h5>
            <p>
              {{content.text}}
            </p>
        
          
          </div>
        </div>
      </div>
      <div>
            <button v-on:click="show = !show" >Подробнее</button>
            <button @click="$emit('removePost', index)">Удалить</button>
            <transition name="fade">
              <teg-read-post v-if="show" :content="content"></teg-read-post>
            </transition>           
      </div>
  </div>
</template>

<script>
import ReadPost from './ReadPost.vue'

export default {
    props: ["content", "index"],
    data () {
      return{
        show: false
        
      }
    },
    components:{
      'teg-read-post': ReadPost
    }
    
}
</script>

<style>
.fade-enter-active, .fade-leave-active {
  transition: opacity 1.5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
  
}
</style>