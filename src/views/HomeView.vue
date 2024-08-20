<template>
  <div class="home">
    密碼輸入：<input type="text" v-model="textSearch">
    <span>
      {{ passwordChecking }}
    </span>
    <table>
      <tr>
        <th>userId</th>
        <th>id</th>
        <th>title</th>
        <th>completed</th>
      </tr>
      <tr v-for="item in dataList" :key="item.id">
        <td>{{ item.userId }}</td>
        <td>{{ item.id }}</td>
        <td>{{ item.title }}</td>
        <td>{{ item.completed }}</td>
      </tr>
    </table>
  </div>
</template>

<script setup>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import { ref, computed } from 'vue';
const dataList = ref([]);

fetch("https://jsonplaceholder.typicode.com/todos", {method: "GET"})
.then(res => { return res.json() })
.then(res => { dataList.value = res });

const textSearch = ref('');

const passwordChecking = computed(() =>{
  return /(([0-9]+[A-Z]+[0-9]){8,}$)/.test(textSearch.value);
});

// const regExp = new RegExp('/([a-z]+[A-Z]+[0-9]){8,}/');

</script>
<style>
table{
  margin: 0 auto;
}
</style>