<template>
  <div id="app">
    <h1>books library</h1>
    <button @click="showElemBtn" :class="active ? 'text-red' : 'text-green'">
      <span v-if="showElem">hide book</span>
      <span v-else>show book</span>
    </button>
    <h2>basket: {{ count }}</h2>
    <div v-if="showElem" id="list">
      <li v-for="book in filterBook" :key="book.id">
        {{ book.title }} - {{ book.author }} - {{ book.year }}
        <button v-on:click="subs">Subs</button>
        <button v-on:click="add">Add</button>
      </li>
    </div>
  </div>
</template>
<script>
export default {
  name: "App",
  data() {
    return {
      showElem: true,
      buttonClass: "text-green",
      active: true,
      books: [
        {
          id: 1,
          title: "Book title",
          author: "Book author",
          year: 987,
        },
        {
          id: 2,
          title: "Book title",
          author: "Book author",
          year: 988,
        },
        {
          id: 3,
          title: "Book title",
          author: "Book author",
          year: 989,
        },
        {
          id: 4,
          title: "Book title",
          author: "Book author",
          year: 990,
        },
        {
          id: 5,
          title: "Book title",
          author: "Book author",
          year: 990,
        },
        {
          id: 6,
          title: "Book title",
          author: "Book author",
          year: 990,
        },
      ],
      count: 0,
    };
  },
  methods: {
    showElemBtn() {
      this.showElem = !this.showElem;
      this.active = !this.active;
    },
    add() {
      this.count += 1;
    },
    subs() {
      this.count -= 1;
    },
  },
  computed: {
    filterBook: function () {
      return this.books;
    },
  },
};
</script>
<style>
span {
  font-size: 18px;
}
.text-red {
  color: red;
}
.text-green {
  color: green;
}
#list {
  display: flex;
  flex-direction: column;
  gap: 12px;
  max-height: 120px;
  overflow-y: auto;
  width: 350px;
}
</style>
