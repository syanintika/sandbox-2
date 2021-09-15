<template>
  <div>
    <h1>HTTP REQUEST : AXIOS</h1>
    <items-button @click.native="addClass" />
    <div class="row">
      <div class="col-md-3" v-for="(item,i) in listClass" :key="i">
        <class-item @refresh="GET_LIST_CLASS" :id="item.id" :name="item.name" :desc="item.description" :img="item.img" @click.native="detail(item.id)" />
      </div>
    </div>
  </div>
</template>
<script>
// import request from "../../../mixins/request.vue";
export default {
  // mixins: [request],
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
      // this.$router.push(`/example/http-request/${id}`);
    },
    addClass() {
      this.$router.push("/example/http-request/add");
    },
    async GET_LIST_CLASS() {
      // const LIST_CLASS = await this.$axios.$get("api/class");
      const LIST_CLASS = await this.requestGet("api/class");
      this.listClass = LIST_CLASS.data;
    },
  },
};
</script>