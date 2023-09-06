<template>
  <div class="knob">
    <input type="range" min="-360" max="360" v-model="degrees" @change="sendValue">
    <input type="text" :value="degrees" readonly>
    <form>

    </form>

  </div>
</template>

<script setup>
import { ref } from 'vue'
import axios from 'axios'

const degrees = ref(0)

const sendValue = async () => {
  console.log("Updaing");
  let data = await axios.post("http://192.168.29.183/settarget", {
    target: degrees.value
  }, {
    headers: {
      "Content-Type": "application/x-www-form-urlencoded"
    }
  });
  console.log(await data);

}
</script>

<style lang="scss" scoped></style>