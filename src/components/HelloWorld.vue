<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  data() {
    return {
      objectOfAttrs: {
        id: 'container',
        class: 'wrapper',
      },
    };
  },
};
</script>
