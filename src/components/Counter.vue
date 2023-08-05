<template>
  <h2>Counter</h2>
  <p>{{ count }}<sup>2</sup> = {{ squaredCount }}</p>
  <p>{{ count }}<sup>2</sup> = {{ squaredCount }}</p>
  <p>{{ count }}<sup>2</sup> = {{ squaredCount }}</p>
  <p>{{ count }}<sup>2</sup> = {{ squaredCount }}</p>
  <p>{{ count }}<sup>2</sup> = {{ squaredCount }}</p>
  <p>{{ count }}<sup>2</sup> = {{ squaredCount }}</p>
</template>

<script>
export default {
  name: "Counter",
  data() {
    return {
      count: 5,
    };
  },
  computed: {
    squaredCount() {
      return this.count ** 2;
    },
  },
};
</script>

<style></style>
