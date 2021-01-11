<template>
  <span class="tag" >
    <span class="content">{{ tag }} </span>
    <span class="closed" @click="$emit('yolla', index)" > X</span>
  </span>
</template>

<script>

export default {
    props:["tag","index"]
}
</script>

<style>
.tag {
  background-color: rgb(243, 210, 167);
  padding: 10px;
  color: brown;
  font-size: 14px;
  cursor: default;
  margin-left: 10px;
}
.tag .closed {
  font-size: 12px;
  cursor: pointer;
}
</style>