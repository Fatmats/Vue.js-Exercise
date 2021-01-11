<template>
  <div class="tag-container">
      <Tag 
      v-for="(tag,index) in tags" 
      :key="tag"
      :tag='tag'
      :index='index'
       @yolla="delet($event)"
      > </Tag>
    <input type="text" @keyup.enter="addTags"  />
    <p>{{tags}}</p>
    <div class="eror" v-if="error">Tanımlı Değişken</div>
  </div>
  
</template>

<script>
import Tag from './tag'
export default {
  components:{
        Tag,
    },
  data() {
    return {
      tags: [],
      error: false,
    }},
    
  methods: {
    addTags(event) {
      var text = event.target;
      let yazdir = false;

      if (text.value.length > 0) {
        this.tags.forEach(tag => {
          if (tag === text.value) {
            yazdir = true;
            this.error = true;
          }
        });

        if (!yazdir) {
          this.tags.push(text.value);
          text.value = '';
        }
      }
    },
    delet(index) {
      this.tags.splice(index,1);
    }, 
  },
  props:{
      value :{
        required:false
      }
    },
  created(){
    if(this.value){
      if(this.value.length>0){
        this.tags=this.value.split(',')
      }
    }
  },
  watch:{
    tags(){
        this.$emit('input',this.tags.join(","))
      }
      
    }
  }

  
    

</script>

<style>
.tag-container {
  border: 1px solid #cccccc;
  padding: 20px;
}

.eror {
  margin-top: 10px;
  font-size: 15px;
  color: brown;
}
input {
  width: 70px;
}
</style>