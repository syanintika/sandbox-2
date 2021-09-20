<script>
export default {
  methods: {
    confirm(message) {
      return this.$swal({
        icon: "question",
        title: "Are you sure?",
        text: message,
        showCancelButton: true,
      });
    },
    async requestPost(url, payload, isNotif = true) {
      try {
        const data = await this.$axios.$post(url, payload);
        if (isNotif)
          this.$swal({
            icon: "success",
            title: "Success",
            text: "data berhasil disimpan",
          });
        return data;
      } catch (error) {
        this.$swal({
          icon: "warning",
          title: "Bahaya!!!",
          text: error.toString(),
        });
      }
    },
    async requestPut(url, payload, isNotif = true) {
      try {
        const data = await this.$axios.$put(url, payload);
        if (isNotif)
          this.$swal({
            icon: "success",
            title: "Success",
            text: "data berhasil disimpan",
          });
        return data;
      } catch (error) {
        this.$swal({
          icon: "warning",
          title: "Bahaya!!!",
          text: error.toString(),
        });
      }
    },
    async requestGet(url) {
      try {
        const data = await this.$axios.$get(url);
        return data;
      } catch (error) {
        this.$swal({
          icon: "warning",
          title: "Bahaya!!!",
          text: error.toString(),
        });
      }
    },
    async requestDelete(url) {
      try {
        const data = await this.$axios.$delete(url);
        this.$swal({
          icon: "success",
          title: "Good!!!",
          text: "data berhasil dihapus",
        });
        return data;
      } catch (error) {
        this.$swal({
          icon: "warning",
          title: "Bahaya!!!",
          text: error.toString(),
        });
      }
    },
  },
};
</script>