<template>
  <div class="vh-100 d-flex justify-content-center">
    <div class="d-flex align-items-center">
      <div class="card" style="width:30vw">
        <div class="card-body">
          <h3>Login</h3>
          {{login}}
          <form @submit.prevent="userLogin">
            <div class="form-group">
              <label for="email">Email</label>
              <input id="email" type="email" v-model="login.email" class="form-control" />
            </div>
            <div class="form-group">
              <label for="password">Password</label>
              <input type="password" id="password" v-model="login.password" class="form-control">
            </div>
            <button type="submit" class="btn btn-primary btn-lg w-100">Login</button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  layout: "clean",
  data() {
    return {
      login: {
        email: "",
        password: "",
      },
    };
  },
  methods: {
    async userLogin() {
      try {
        let response = await this.$auth.loginWith("local", {
          data: this.login,
        });
        this.$swal({
          icon: "success",
          title: "Selamat Datang",
          text: "Kamu berhasil login",
        });
        this.$router.push("/");
      } catch (err) {
        console.log(err);
      }
    },
  },
};
</script>