<script setup>
import {ref} from 'vue'
import { AutoComplete, Input } from 'ant-design-vue'

const keyword = ref('');
const options = ref([]);
function handleSearch(value){
  options.value = !value
    ? []
    : [{ value }, { value: value + value }, { value: value + value + value }];
}

function onSelect(value){
  console.log('onSelect', value);
  options.value = []
}
</script>

<template>
  <main>
    <div>
      搜索值： {{ keyword }}
    </div>
    <br>
    <br>
    <AutoComplete 
      v-model:value="keyword"
      :options="options"
      @search="handleSearch"
      @select="onSelect"
    >
      <Input placeholder="请输入" />
    </AutoComplete>
  </main>
</template>

<style scoped>
main{
  width: 300px;
  margin: 20px auto;
}
</style>
