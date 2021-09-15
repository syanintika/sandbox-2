<template>
  <div class="card">
    <img :src="img" class="card-img-top" :alt="'foto ' +name">
    <div class="card-body">
      <h5 class="card-title">{{name}}</h5>
      <p class="card-text">{{desc}}</p>
      <button v-if="!unfollow" type="button" class="btn btn-primary" @click="followClass">Follow</button>
      <button v-else type="button" class="btn btn-outline-danger" @click="followClass">Unfollow</button>
      <i class="fas fa-trash" @click="confirmDelete"></i>
    </div>
  </div>
</template>
<script>
import request from "../../mixins/request.vue";
import { currency } from "../../mixins/script";
export default {
  mounted() {
    currency();
  },
  mixins: [request],
  props: {
    id: {
      type: Number,
    },
    name: {
      type: String,
      default: "Nama Kelas",
    },
    desc: {
      type: String,
      default: "Ini deskripsi kelasnya ya",
    },
    img: {
      type: String,
      default: "https://shiftacademy.id/wp-content/uploads/2021/09/1.png",
    },
    unfollow: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    async confirmDelete() {
      // const confirm =await this.$swal({
      //   icon: "question",
      //   title: "Are you sure?",
      //   text: message,
      //   showCancelButton: true,
      // });
      const confirm = await this.confirm("Delete " + this.name + " class");
      if (confirm.isConfirmed) {
        await this.requestDelete("api/class/" + this.id);
        this.$emit("refresh");
      }
    },
    followClass() {
      const data = {
        name: this.name,
        desc: this.desc,
        img: this.img,
      };
      if (this.unfollow) this.$emit("unfollow-class", data);
      else this.$emit("follow-class", data);
    },
  },
};
</script>