<template>
  <div class="content">
    test
    <ul>
      <li v-for="(item, index) in $store.state.city.list" :key="index">{{item}}</li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  layout: "test",
  data() {
    return {
      list: []
    }
  },
  async asyncData() {
    let {status, data: {list}} = await axios.get('http://localhost:3000/city/list')
    if(status === 200) {
      return {list}
    }
  }
};
</script>

<style scoped>
</style>
