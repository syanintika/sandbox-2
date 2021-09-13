<template>
  <div>
    <h1>HTTP REQUEST : AXIOS</h1>
    <items-button @click.native="addClass" />
    <div class="row">
      <div class="col-md-3" v-for="(item,i) in listClass" :key="i">
        <class-item :name="item.name" :desc="item.description" :img="item.img" @click.native="detail(item.id)" />
      </div>
    </div>
  </div>
</template>
<script>
export default {
  mounted() {
    this.GET_LIST_CLASS();
  },
  data() {
    return {
      listClass: [],
    };
  },
  methods: {
    detail(id) {
      this.$router.push(`/example/http-request/${id}`);
    },
    addClass() {
      this.$router.push("/example/http-request/add");
    },
    async GET_LIST_CLASS() {
      const LIST_CLASS = await this.$axios.$get("api/class");
      this.listClass = LIST_CLASS.data;
    },
  },
};
</script>