<template>
  <div>
    <input
      type="text"
      placeholder="Type to search"
      v-model="text"
      @input="pu"
    />
    <ul v-show="text.length > 0">
      <li v-for="i in newArr">
        {{ i.name }}
      </li>
    </ul>
  </div>
</template>

<script>
import { ref } from 'vue';
let newArr = ref([]);
let text = ref('');

async function pu() {
  let data = await fetch('https://jsonplaceholder.typicode.com/users');
  let newData = await data.json();

  newArr.value = newData.filter((ele) => {
    return ele.name.toLowerCase().indexOf(text.value.toLowerCase()) != -1;
  });
}

export default {
  name: 'searchbar',
  setup() {
    return { text, pu, newArr };
  },
};
</script>

<style>
* {
  font-family: georgia;
  box-sizing: border-box;
  padding: 0px;
  margin: 0px;
}
body {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

ul {
  max-height: 150px;
  overflow-y: scroll;
  margin-top: 20px;
  box-shadow: 0 3px 2px 1px rgba(0, 0, 0, 0.5);
  padding: 10px;
  border-radius: 10px;
}
li {
  display: block;
  list-style: none;
  margin-top: 10px;
}
input {
  width: 100%;
  height: 35px;
  border-radius: 20px;
  padding: 10px;
  outline: none;
  border: 1px solid #000;
}
</style>
