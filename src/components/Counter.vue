<template>
  <h2>{{ header }}</h2>
  <p>{{ count }}<sup>2</sup> = {{ squaredCount }}</p>

  <div>
    <h3>{{ count }}</h3>
    <div class="btn-group">
      <button @click="increase">+1</button>
      <button @click="decrease">-1</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Counter",
  props: {
    header: {
      type: String,
      required: true,
    },
    start: {
      type: Number,
      default: 100,
      validator(val) {
        return val >= 10;
      },
    },
  },
  data() {
    return {
      count: this.start ?? 5,
    };
  },
  methods: {
    increase() {
      this.count++;
    },
    decrease() {
      this.count--;
    },
  },
  computed: {
    squaredCount() {
      return this.count ** 2;
    },
  },
};
</script>

<style>
.btn-group {
  display: flex;
  gap: 0.5rem;
}
</style>
