<template>

  <div v-if="post">
      <h2>{{post.title}}</h2>
      <p>{{post.body}}</p>
  </div>
</template>

<script>
import getPost from "../composables/getPost.js"
export default {
    props:["id"],
    setup(props){
        let {post,error,load}=getPost(props.id);
        load();
        return{post,error}
    }
}
</script>

<style>

</style>