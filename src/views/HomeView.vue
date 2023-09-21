<template>
  <span>{{helloInfo}}</span>
</template>

<script setup>

import {onMounted, ref} from "vue";
import axios from "axios";

let helloInfo = ref()

const getHelloInfo =async function() {
  await axios.get('http://localhost:8080/hello').then(res => {
    helloInfo.value = res.data
  }).catch(err => {
    console.log(err)
  })
}

onMounted(()=>{
  getHelloInfo()
})

</script>
