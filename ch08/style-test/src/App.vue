<template>
  <div>
    <Child1/>
    <Child2/>
    <Child3/>
  </div>
</template>

<script>
  //yellow
  import Child1 from './components/Child1.vue';
  //blue
  import Child2 from './components/Child2.vue';
  //orange
  import Child3 from './components/Child3.vue';
  
  export default {
    name : "App",
    components : {
      Child1,
      Child2,
      Child3
    }
  }
</script>

<style>

</style>