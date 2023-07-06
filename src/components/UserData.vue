<template>
  <form @submit.prevent="submitData">
    <div>
      <label>Name</label>
      <input type="text" v-model="name" />
    </div>
    <div>
      <label>Age</label>
      <input type="text" v-model="age" />
    </div>
    <div>
      <button>Add Contact</button>
    </div>
  </form>
</template>

<script>
export default {
  emits: ["add-contact"],
  data() {
    return {
      name: "",
      age: "",
    };
  },
  methods: {
    submitData() {
      this.$emit("add-contact", this.name, this.age);
    },
  },
};
</script>
