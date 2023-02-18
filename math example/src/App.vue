<template>
  <div id="list-demo">
    <div>
      <transition-group>
        <ol>
          <li v-for="item in items" :key="item.id" class="list-item">
            Example:
            <p>
              {{ item }} {{ randomNumber }}
              {{ Math.floor(Math.random() * item) }} =
            </p>
          </li>
        </ol>
      </transition-group>
      <div class="btnGroup">
      <button @click="remove">Remove example</button>
        <button @click="add">Add example</button>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  data() {
    return {
      items: [1, 2, 3],
      nextNum: 5,
    };
  },
  methods: {
    randomItem() {
      return Math.floor(Math.random() * this.items.length);
    },
    add() {
      this.items.splice(this.randomItem(), 0, this.nextNum++);
      this.randomNumber = ["+", "-", "*", "/"][Math.floor(Math.random() * 4)];
    },
    remove() {
      this.items.splice(this.randomItem(), 1);
      this.randomNumber = ["+", "-", "*", "/"][Math.floor(Math.random() * 4)];
    },
  },
};
</script>


<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: sans-serif;
  background-image: linear-gradient(
    68.4deg,
    rgba(99, 251, 215, 1) -0.4%,
    rgba(5, 222, 250, 1) 100.2%
  );
}

#list-demo {
  display: grid;
  place-items: center;
  height: 100vh;
}

ol {
  width: 650px;
  height: 300px;
  overflow-y: auto;
}

li {
  display: flex;
  font-size: 60px;
  font-weight: bold;
  color: #fff;
}

p {
  margin-left: 20px;
  color: crimson;
}

.btnGroup {
  display: flex;
  justify-content: space-between;
}

button {
  font-size: 20px;
  border: none;
  margin-top: 25px;
  padding: 12px 18px;
  border-radius: 12px;
}

button:hover {
  box-shadow: rgba(50, 50, 93, 0.25) 0px 13px 27px -5px, rgba(0, 0, 0, 0.3) 0px 8px 16px -8px;
}

button:active {
  transform: scale(.95);
}
</style>
