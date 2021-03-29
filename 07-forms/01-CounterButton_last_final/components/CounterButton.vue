<template>
  <div>
    <button @click="increment" type="button">
      {{ innerCount }}
    </button>
  </div>
</template>

<script>
export default {
  name: 'CounterButton',

  model: {
    prop: 'count',
    event: 'increment',
  },

  props: {
    count: {
      type: Number,
      default: 0,
    },
  },

  data() {
    return {
      innerCount: this.count,
    };
  },

  watch: {
    count(newVal, oldVal) {
      if (newVal === oldVal) return;

      this.innerCount = newVal;
    },
  },

  methods: {
    increment() {
      this.innerCount += 1;
      this.$emit('increment', this.innerCount);
    },
  },
};
</script>

<style></style>
