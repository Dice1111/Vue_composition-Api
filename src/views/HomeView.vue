<template>
  <div class="home">
    <div v-if="error">
      {{error}}
    </div>
    <div v-if="posts.length>0">
      <PostsList :posts="posts"></PostsList>
    </div>
    <div v-else>Loading</div>  



  </div>
</template>

<script>
import PostsList from '../components/PostsList'
import { ref } from '@vue/runtime-core'
import PostsListVue from '@/components/PostsList.vue';
import getPosts from "../composables/getPosts"



export default {
  components: { PostsList },
  setup(){
    let {posts,error,load}=getPosts()
    load();
    return {posts,error};
  }
}
</script>
