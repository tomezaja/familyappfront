<template>
  <div class="about">
    <h1>This is an about page</h1>
    <button @click="proba">try</button>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>

<script>
console.log("mrmrmr")
export default{
methods: {
    proba(e){
      console.log("ide")
    }
}
}
</script>
