<template>
  <div>
    CompositionTest
    <p>{{ name }}</p>
    <p>{{ age }}</p>
    <p>{{ nameRef }}</p>
    <p>{{ book.title }}</p>
    <p>{{ book.author[0] }}</p>
    <p>{{ titleRef }}</p>
    <p>{{ authorRef[1] }}</p>
  </div>
</template>

<script>
import { reactive, ref ,toRefs } from 'vue'
  export default {
    setup() {
      let name = 'otani'
      const age = 27
      const nameRef = ref('nishikori')
      const book = reactive({
        title: 'title 1',
        author: ['otani 1', 'ito 1']
      })
      const booktoRefs = reactive({
        titleRef: 'title 2',
        authorRef: ['otani 2', 'ito 2']
      })

      console.log('setup');
      console.log(this);
      console.log(nameRef.value);

      return {
        name: name,
        age: age,
        nameRef,
        book,
        ...toRefs(booktoRefs)
      }
    },
    data() {
      return {
        number: 1,
        sports: 'soccer'
      }
    },
    created() {
      console.log('created');
      console.log(this);
    },
    mounted() {
      console.log('mounted');
    }
  }
</script>

<style>

</style>