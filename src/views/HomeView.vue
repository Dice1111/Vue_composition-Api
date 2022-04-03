<template>
  <div class="home">
  <h1>Person One.</h1>
  <p>{{personOne.name}}-{{personOne.age}}</p>
  <button @click="changeOne">Change One</button>
  <h1>Person Two</h1>
  <p>{{personTwo.name}}-{{personTwo.age}}</p>
  <button @click="changeTwo">Change Two</button>
  </div>
</template>

<script>
import { reactive, ref } from '@vue/reactivity'



export default {
  setup(){
    let personOne=ref({name:"kyawkyaw",age:30});
    let changeOne=()=>{
      personOne.value.name="Change KyawKyaw";
    }

    let personTwo=reactive({name:"MgMg",age:30});
    let changeTwo=()=>{
      personTwo.name="change MgMg";
    }
    return {personOne,changeOne,personTwo,changeTwo};
  }
}
</script>
