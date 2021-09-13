<template>
  <div class="card">
    <div class="card-body">
      {{detailClass}}
      <form @submit.prevent="tambahKelas">
        <input-type name="Nama Kelas" @get="(val)=>detailClass.name=val" />
        <input-type name="Deskripsi kelas" @get="(val)=>detailClass.description=val" />
        <input-type type="date" name="Tanggal Mulai" @get="(val)=>detailClass.startDate=val" />
        <input-type type="date" name="Tanggal Selesai" @get="(val)=>detailClass.endDate=val" />
        <div class="text-right">
          <button class="btn btn-outline-secondary" type="button" @click="$router.go(-1)">Back</button>
          <button class="btn btn-outline-primary" type="submit">Save</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      detailClass: {
        name: "",
        description: "",
        startDate: "",
        endDate: "",
      },
    };
  },
  methods: {
    async tambahKelas() {
      //   const payload = {
      //     name: this.name,
      //     description: this.description,
      //   };
      try {
        const payload = this.detailClass;
        const TAMBAH_KELAS = await this.$axios.$post("api/class", payload);
        this.$swal({
          icon: "success",
          title: "Success",
          text: "data berhasil disimpan",
        });
        this.$router.go(-1);
      } catch (error) {
        this.$swal({
          icon: "warning",
          title: "Danger",
          text: error.message,
        });
      }
    },
  },
};
</script>