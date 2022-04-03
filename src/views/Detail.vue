<template>

  <div v-if="post">
      <h2>{{post.title}}</h2>
      <p>{{post.body}}</p>
  </div>
  <div v-else>
      <Spinner></Spinner>
  </div>
</template>

<script>
import Spinner from '../composables/spinner'
import getPost from "../composables/getPost.js"
export default {
  components: { Spinner },
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