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
import {  computed, ref } from '@vue/runtime-core'
import PostsListVue from '@/components/PostsList.vue';



export default {
  components: { PostsList },
  setup(){

    let posts=ref([]);
    let error=ref("");

    let load=async()=>{
      try{
        let response= await fetch("http://localhost:3000/posts")
        if(response.status===404){
          throw new Error("not found url");
        }
        let datas=await response.json();
        posts.value=datas;
      }catch(err){
        error.value=err.message;
      }
    }

    load();

    return {posts,error};
  }
}
</script>
