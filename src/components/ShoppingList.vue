<template>
  <section id="shopping-app">
    <div class="shopping-app">
      <div class="container-text">
        <div class="text">
          <h1>Shopping List</h1>

          <span
            ><svg
              xmlns="http://www.w3.org/2000/svg"
              class="h-6 w-6"
              fill="none"
              viewBox="0 0 24 24"
              stroke="#fca954"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M16 11V7a4 4 0 00-8 0v4M5 9h14l1 12H4L5 9z"
              /></svg
          ></span>
        </div>
        <div>
          <DateData />
        </div>
      </div>
      <div class="list">
        <li
          v-for="(list, index) in lists"
          :key="index"
          :class="{ removed: list.checked }"
        >
          <div class="form-box">
            <input type="checkbox" v-model="list.checked" class="input-box" />

            <label class="label">
              {{ list.text }}
            </label>
            <i
              class="fa fa-trash icon-mouse"
              aria-hidden="true"
              v-on:click="removeList(index)"
            ></i>
          </div>
        </li>
      </div>
      <div class="container">
        <input
          type="text"
          placeholder="Add new item"
          v-model="currentList"
          v-on:keyup.enter="addList"
        />
        <span><i class="fa fa-plus" aria-hidden="true"></i></span>
      </div>
      <p class="footer">Made With ❤ ❤ ❤ By Emilson</p>
    </div>
  </section>
</template>

<script>

export default {
  name: "ShoppingList",
  data() {
    return {
      lists: [
        { text: "Surface Laptop 2", checked: false },
        { text: "GooglePixel 4xl", checked: false },
        { text: "Sony 1000xm4", checked: false },
      ],
      currentList: "",
    };
  },
  methods: {
    addList() {
      this.lists.push({ text: this.currentList, checked: false });
      this.currentList = "";
    },
    removeList(index) {
      this.lists.splice(index, 1);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.form-box > .input-box > .label > .icon-mouse {
  /* padding:0px 20px; */
}
.form-box {
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: #aaaaaa;
  margin: 10px 0px;
}
li {
  list-style-type: none;
}
.removed {
  color: #fca954;
}

.removed label {
  text-decoration: line-through;
}
#shopping-app {
  display: flex;
  justify-content: center;
}

.fa-plus {
  background-color: #fca954;
  color: #ffffff;
  width: 40px;
  height: 40px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 30px;
}
.icon-font {
  font-size: 40px;
  color: #fca954;
}
.icon-font:hover {
  transition: all 0.3s ease-in-out;
}

.btn {
  color: green;
}
.list {
  width: 300px;
  /* border: 1px solid black; */
  display: flex;
  flex-direction: column;
  padding: 20px;
  background: #444444;
}

.container {
  width: 300px;
  /* border: 1px solid black; */
  display: flex;
  /* flex-direction: column; */
  justify-content: space-between;
  align-items: center;
  padding: 20px;
  margin: 10px 0px;
  background: #444444;
  color: #aaaaaa;
}

.container input {
  width: 80%;
  padding: 8px 0px;
  outline: none;
  background: transparent;
  border: none;
  color: #aaaaaa;
  font-size: 17px;
}

::placeholder {
  color: #aaaaaa;
}

.container-text {
  width: 300px;
  /* border: 1px solid black; */
  padding: 20px;
  margin: 20px 0px;
  background: #444444;
  color: #aaaaaa;
}
.text {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

/* li {
  margin: 20px 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: #aaaaaa;
} */
.footer {
  color: #aaaaaa;
  padding: 10px 0px;
  text-align: center;
}
.icon-mouse {
  cursor: pointer;
}

@media (max-width: 332px) {
  .list,
  .container-text,
  .container {
    width: 270px;
    max-width: 250px;
  }
}
</style>
