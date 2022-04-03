<template>
  <div class="home">
    <div v-if="showPosts">
      <PostsList :posts="posts"></PostsList>
    </div>
    <button @click="showPosts=!showPosts">toggle post lists</button>
    <button @click="posts.pop()">delete post lists</button>

  </div>
</template>

<script>
import PostsList from '../components/PostsList'
import {  computed, ref } from '@vue/runtime-core'



export default {
  components: { PostsList },
  setup(){
    let showPosts=ref(true);
    let posts=ref([
      {title:"post title 1",body:"    Lorem ipsum dolor sit amet consectetur adipisicing elit. Deleniti, sequi dolor aperiam minima saepe dolores exercitationem reiciendis id consectetur impedit, tenetur vero ratione atque voluptate placeat voluptatibus eaque, similique illum.",id:1},
      {title:"post title 2",body:"Lorem ipusm",id:2},
    ])
    return {showPosts,posts};
  }
}
</script>
