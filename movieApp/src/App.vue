<script setup>
  import movieData from './data.js';
  import {ref} from 'vue';

  let text = ref("");
  let arr = ref([]);
  function pu(){
    arr.value = movieData.filter((ele)=>{
      return ele.name.toLowerCase().indexOf(text.value.toLowerCase()) !== -1;
    });
  }
</script>

<template>
  <h1>The Marvel Cenematic Universe</h1>
  <input type="text" placeholder="Search the Movie" v-model="text" @input="pu"/>
  <ul>
    <li v-for="i in arr">
      <div>
        <img :src="`${i.url}`" :alt="`${i.name}`"/>
      </div>
      <div class="details">
        {{ i.name }} 
        <div class="year">{{ i.year }}</div>
      </div>
    </li>
  </ul>
</template>

<style scoped>
*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: Georgia, 'Times New Roman', Times, serif;
}

  ul{
    width: 100%;
    height: 100%;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 20px;
    margin-top: 20px;
  }

  li{
    list-style: none;
    border-radius: 10px;
    cursor: pointer;
    width: 180px;
    box-shadow: 0px 3px 3px 2px rgba(0,0,0,0.5);
    transition: all 0.2s linear;

    & img{
      border-radius: 10px 10px 0 0;
      height: 240px;
      width: 100%;
    }

    &:hover{
      box-shadow: none;
     border:1px solid gray;
    }
  }

  .details{
    padding-left: 10px; 
  }

  input{
    width: 400px;
    height: 50px;
    border: 3px solid #892ad2;
    padding: 5px;
    outline: none;
    border-radius: 10px;
    display: block;
    margin: 20px auto;
  }
  h1{
    text-align: center;
  }
</style>
