<template>
  <div class="container">
    <Tags v-model="tags" :tags='tags'/>

  </div>
</template>

<script>
import Tags from "./components/tags";
export default {
  components: {
    Tags,
  },
  data() {
    return {
      tags:"deneme,test",
    };
  },
 }
</script>
<style>
</style>