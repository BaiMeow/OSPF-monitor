<script lang="ts" setup>
import {ref} from 'vue';
interface selectItem {
    value: string;
    label: string;
    selectcb: () => void;
  }

const props = defineProps<{
  data: Array<selectItem>
}>();
const value = ref('');

const onchange = (value:string)=>{
  props.data.find((v)=>{
    return v.value === value
  })?.selectcb()
}

</script>

<template>
  <div style="display:flex;align-items: center">
    <el-icon color="#409EFF" style="margin-right:.5rem">
      <i-ep-search />
    </el-icon>
    <el-select v-model="value" filterable placeholder="Search" @change="onchange" >
      <el-option v-for="item in data" :key="item.value" :label="item.label" :value="item.value" />
    </el-select>
  </div>

</template>

<style scoped></style>