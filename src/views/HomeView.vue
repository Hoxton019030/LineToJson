<template>
  <div class="title">
    請在這邊匯入Line的資料123
  </div>
  <div>
    <input type="file" name="" id="" @change="parseLineToJson">
  </div>
  <div>
    <input type="text" name="" id="" v-model="lineContent" style="width: 300px; height: 400px;">
  </div>



</template>

<script setup>

import { ref } from 'vue';

let lineContent = ref('')

async function parseLineToJson(event){
  var a =await retriveLineContentFromUploadFile(event)
  lineContent.value.split('\n')
  console.log(a.value)
  // console.log(lineContent.value)
  // lines.forEach((line)=>{
  //   console.log(line)
  // })
}


async function retriveLineContentFromUploadFile(event){
  const file = event.target.files[0];
  if (!file) return;
  const reader = new FileReader();
  reader.onload = async () => {
    lineContent.value = reader.result
    // console.log(lineContent.value.split('\n'))
  };
  reader.readAsText(file);
  return lineContent
}
</script>
