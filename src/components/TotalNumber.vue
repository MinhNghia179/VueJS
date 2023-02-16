<template>
  <div :id="dynamicId">
    <span>Total Number {{ count }} {{ messenger }} </span>
    <button @click="increment">Increment</button>
    <button @click="decrement">Decrement</button>
    <button @click="doSyncData" :disabled="isLoading">
      {{ publishedBooksMessage }}
    </button>
    <p v-show="isVisible">Now you see me</p>
    <a :href="pageUrl">Here</a>
    <p>Hello v-show {{ messenger }}</p>

    <form @submit.prevent="onSubmit">
      <input v-model="messenger" />
      <div>
        <input type="checkbox" v-model="isChecked" />
        <label for="checkbox">{{ isChecked }}</label>
      </div>
    </form>
    <ul>
      <li
        v-for="({ label, id, purchased, danger }, index) in items"
        :key="id"
        :class="{ strikeout: purchased, 'text-danger': danger }"
      >
        {{ label }} + {{ index }}
      </li>
    </ul>
    <ul>
      <li v-for="number in evenNumbers" :key="number">
        {{ number }}
      </li>
    </ul>
  </div>
</template>

<script>
import { debounce } from 'lodash';
import { nextTick } from 'vue';

export default {
  name: 'TotalNumber',
  props: {},
  data() {
    return {
      count: 1,
      messenger: 'Messenger total number',
      searchName: '',
      isVisible: true,
      isChecked: false,
      pageUrl: 'https://viblo.asia/p/mot-so-kien-thuc-co-co-ban-ve-vuejs-yMnKMjpgZ7P',
      books: ['Vue 2 - Advanced Guide', 'Vue 3 - Basic Guide', 'Vue 4 - The Mystery'],
      items: [
        { id: 1, label: '10 party', purchased: true, danger: false },
        { id: 2, label: '15 party', purchased: false, danger: true },
        { id: 3, label: '20 party', purchased: false, danger: false },
        { id: 4, label: '25 party', purchased: false, danger: true },
      ],
      numbers: [1, 2, 3, 4, 5],
    };
  },
  computed: {
    publishedBooksMessage() {
      return this.books.length > 1 ? 'Yes' : 'No';
    },
    now() {
      return Date.now();
    },
    evenNumbers() {
      return this.numbers.filter((n) => n % 2 === 0);
    },
  },
  methods: {
    increment() {
      this.count += 1;
      nextTick(() => {
        console.log('Vue JS');
      });
    },
    decrement() {
      this.count -= 1;
    },
    enterSearchName: debounce(() => {}, 500),
    doSyncData: async () => {
      await fetch('https://61aadfdabfb110001773f328.mockapi.io/users');
    },
    onSubmit() {
      console.log('Submit Form');
    },
    onToggle() {
      this.isVisible = !this.isVisible;
    },
  },
};
</script>

<style>
#dynamicId {
  display: flex;
  flex-direction: column;
  width: 400px;
  align-items: center;
  justify-content: center;
}
.strikeout {
  text-decoration: line-through;
}
.text-danger {
  color: red;
}
</style>
