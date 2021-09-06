<template>
  <div>
    <div class="card">
      <div class="card-body">
        <h2 class="mb-5">Belajar EMIT 2</h2>
        <h5>Parent : {{fullname}}</h5>
        <input-type name="fullname" :value="fullname" @get="(val)=>fullname=val" />
        <input-type name="address" :value="address" @get="(val)=>address=val" />
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      fullname: "",
      address: "",
    };
  },
  methods: {
    notif() {
      this.$swal({
        icon: "success",
        title: "Apakah kamu yakin?",
        text: "mau menghapus ini",
      });
    },
  },
};
</script>