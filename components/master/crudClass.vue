<template>
  <div class="card">
    <div class="card-body">
      {{detailClass}}
      <form @submit.prevent="submitDate">
        <input-type name="Nama Kelas" :value="detailClass.name" @get="(val)=>detailClass.name=val" />
        <input-type name="Deskripsi kelas" :value="detailClass.description" @get="(val)=>detailClass.description=val" />
        <input-type type="date" name="Tanggal Mulai" :value="detailClass.startDate" @get="(val)=>detailClass.startDate=val" />
        <input-type type="date" name="Tanggal Selesai" :value="detailClass.endDate" @get="(val)=>detailClass.endDate=val" />
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
  mounted() {
    if (this.$route.params.id) this.GET_DATA();
  },
  methods: {
    async GET_DATA() {
      const DETAIL = await this.requestGet(
        "api/class/" + this.$route.params.id
      );
      console.log(DETAIL);
      // DETAIL.data harus mempunyai atribut yg sama dengan detailClass
      // this.detailClass = DETAIL.data;
      // apabila gak sama maka
      this.detailClass = {
        name: DETAIL.data.name,
        description: DETAIL.data.description,
        startDate: DETAIL.data.startDate,
        endDate: DETAIL.data.endDate,
      };
    },
    async UPDATE_DATA(payload) {
      payload.id = this.$route.params.id;
      const updateClass = await this.requestPut("api/class", payload);
      return updateClass;
    },
    async CREATE_DATA(payload) {
      const createClass = await this.requestPost("api/class", payload);
      return createClass;
    },
    async submitDate() {
      //   const payload = {
      //     name: this.name,
      //     description: this.description,
      //   };
      try {
        const payload = this.detailClass;
        let request = null;
        if (this.$route.params.id) {
          // UPDATE
          request = await this.UPDATE_DATA(payload);
        } else {
          // CREATE
          request = await this.CREATE_DATA(payload);
        }
        if (request) {
          this.$router.push("/example/http-request");
        }
      } catch (error) {
        this.$swal({
          icon: "warning",
          title: "BAHAYA!!!",
          text: error.toString(),
        });
      }
    },
  },
};
</script>