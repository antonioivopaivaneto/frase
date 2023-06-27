<template>
  <div class="frase">
    {{ frase }}
  </div>

  <button @click="getFrase" class="btn">ver mais</button>

</template>

<script lang="ts">
import { defineComponent, onMounted, ref } from 'vue';
import axios from 'axios';
export default defineComponent({
  name: 'HelloWorld',
  props: {
    msg: String,
  },

 


 setup(){
  const frase = ref('');


  async function  getFrase(){
    let res = await axios.get('https://frases.onrender.com/frase');
    let ramdom = Math.floor(Math.random() * 300) + 1
    frase.value = res.data[ramdom].frase;


  }

  onMounted(() => {
    getFrase();
  })

  return{
    frase,
    getFrase
  }
  
 },
 

  
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.frase{
  margin-top: 150px;
  font-size: 50px;
  color: #ffe600;}
  .btn{
    margin-top: 50px;
    background-color: #ffe600;
    color:rgb(40, 40, 40);
    padding: 10px;
    border:0;
    border-radius: 5px;
    width: 200px;

  }


</style>
