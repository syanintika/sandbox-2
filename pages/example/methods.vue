<template>
  <div>
    <h4>Belajar Method</h4>
    <div class="text-center">
      <h4>{{count}}</h4>
    </div>
    <items-button @click.native="counter(10)" />
  </div>
</template>
<script>
export default {
  data() {
    return {
      count: 0,
      name: "Ghany AE",
    };
  },
  methods: {
    counter(val) {
      this.count += val;
      this.decrement();
    },
    decrement() {
      setTimeout(() => {
        this.count -= 2;
      }, 500);
    },
  },
};
</script>