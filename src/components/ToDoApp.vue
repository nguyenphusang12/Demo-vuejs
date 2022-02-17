<template>
  <div class="container">
    <div class="formGroup">
      <input
        class="formInput"
        v-model="title"
        @keyup="handleAddWork"
        type="text"
      />
    </div>
    <div class="box-work">
      <h2 class="task">Task</h2>
      <ul>
        <li
          class="listItem"
          v-for="(item, index) in works"
          :key="index"
          :class="{ test: item.status }"
        >
          <span class="listWork"> {{ index + 1 }}. {{ item.title }}</span>
          <span class="listIcon" @click="() => handleClickCheck(index)">
            <i class="fa-solid fa-check"></i>
          </span>
          <span class="listIcon" @click="() => handleClickDelete(index)">
            <i class="fa-solid fa-ban"></i>
          </span>
          <span class="listIcon" @click="() => handleClickEdit(index)">
            <i class="fa-solid fa-pen"></i>
          </span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "ToDoApp",
  data() {
    return {
      title: "",
      edit: null,
      works: [],
    };
  },
  methods: {
    handleClickCheck(index) {
      this.works[index].status = !this.works[index].status;
    },
    handleClickDelete(index) {
      this.works.splice(index, 1);
    },
    handleAddWork(e) {
      if (e.key === "Enter") {
        if (this.edit !== null) {
          this.works[this.edit].title = this.title;
          this.edit = null;
        } else {
          this.works.push({
            title: this.title,
            status: false,
          });
        }
        this.title = "";
      }
    },
    handleClickEdit(index) {
      this.edit = index;
      this.title = this.works[index].title;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.box-work {
  height: 100%;
  overflow-y: auto;
}
.container {
  width: 600px;
  margin: 0 auto;
  height: 800px;
  background-image: url(../assets/istockphoto-1307266490-612x612.jpg);
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  padding: 100px 140px;
}
.formGroup {
  width: 100%;
  margin: 0 auto;
}
.formInput {
  display: block;
  margin: 0 auto;
  width: 80%;
  height: 40px;
  font-size: 1.6rem;
  padding: 8px;
}
.task {
  margin-top: 16px;
  font-weight: 500;
}
.listWork {
  font-size: 1.2rem;
  display: inline-block;
}
.listIcon {
  display: inline-block;
  margin: 0 10px;
  cursor: pointer;
}
.listItem {
  margin: 20px 0;
}
.test {
  background-color: #00ff1f;
}
</style>
