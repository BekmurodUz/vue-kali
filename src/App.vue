<template lang="">
<div class="senter">
  <button class="btn" @click="increment">Counter</button>
  <div>{{counter}}</div>
  <div>{{arrayOfEmoji}}</div>
</div>
</template>

<script>
import {ref, onMounted, watch, computed} from 'vue'

export default {
  props: {
    emoji: {type: String, default: '💩'}
  },

  setup(props){
    console.log(props.emoji);

    onMounted(() => {
      console.log("Counter component has been mounted!");
    })

    const counter = ref(0)
    const increment = () => counter.value++

    watch(counter, counter=> {
      if (counter === 5) console.log("You have clicked five times");
    })

    const arrayOfEmoji = computed(() => 
      Array.from(new Array(counter.value), () => props.emoji).join('')
    )

    return{counter, increment, arrayOfEmoji}
  }
}
</script>


<style>
.senter{
  background-color: black;
  color: aliceblue;
  text-align: center;
}
.btn {
  background-color:aqua;
  box-sizing: border-box;
  border: none;
  border-radius: 10%;
  margin: 10px;
  color: green;
}

.btn:hover {
  width: 100px;
  height: 80px !important;
}
</style>