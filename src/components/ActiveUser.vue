<template>
  <li>
    <h2>{{ userName }} {{ isActive ? "[Active]" : " " }}</h2>
    <button @click="toggleStatus">change Status</button>
    <button @click="toggleDetails">
      {{ detailsAreVisible ? "Hide" : "Show" }} Details
    </button>
    <ul v-if="detailsAreVisible">
      <li>
        <strong>Age</strong>
        {{ age }}
      </li>
    </ul>
  </li>
</template>

<script>
export default {
  props: {
    id: {
      type: String,
      required: true,
    },
    userName: {
      type: String,
      required: true,
    },
    age: {
      type: Number,
      required: true,
    },
    isActive: {
      type: Boolean,
      required: false,
      default: false,
    },
  },
  emits: ["toggle-status"],

  data() {
    return {
      detailsAreVisible: false,
      //   userIsActive: this.isActive,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleStatus() {
      this.$emit("toggle-status", this.id);
    },
  },
};
</script>
