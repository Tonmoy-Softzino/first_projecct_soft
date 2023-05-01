<template>
  <div>
    <!-- <p>Count: {{ count }}</p>
    <button @click="incrementCount">Increment</button> -->

    <input :value="text" @input="formFill" placeholder="type here" />
    <h1>{{ text }}</h1>
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  setup() {
    // const count = ref(0);
    const text = ref("");
    const formFill = (event) => {
      text.value = event.target.value;
    };
    const added = 10;
    const new_var = 100;

    // const incrementCount = () => {
    //   count.value++;
    // };

    return {
      // count,
      text,
      formFill,
      // incrementCount,
    };
  },
};
</script>

<style>
.text-green {
  color: green;
}
.text-red {
  color: red;
}
</style>
