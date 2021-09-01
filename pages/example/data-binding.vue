<template>
  <div>
    <center>
      <NuxtLink to="/users"> User Nuxt LINK</NuxtLink> ||
      <a href="/users">User A</a>
    </center>
    <br><br>
    <form>
      <div class="form-group">
        <label for="name">Nama</label>
        <input type="text" class="form-control" v-model="name">
        {{name}}
      </div>
      <div class="form-group">
        <label for="name">Tanggal Lahir</label>
        <input type="date" class="form-control" v-model="date" required>
        {{date}}
      </div>
      <div class="form-group">
        <label for="provinsi">Provinsi</label>
        <select v-model="provinsi" class="form-control">
          <option>-Pilih provinsi-</option>
          <option v-for="(provinsi,i) in listProvinsi" :key="i" :value="provinsi.name">{{provinsi.name}}</option>
        </select>
        {{provinsi}}
      </div>
      <p class="h4" v-if="provinsi=='Banten'">AKU BERADA DI BANTEN</p>
      <a class="h5" v-else-if="provinsi=='DKI Jakarta'"> AKU Tidak Suka Jakarta</a>
      <span class="h6" v-else> Ke Jawa Barat Aja deh (bandung)</span>
      <p v-show="provinsi=='Jawa Barat'"> Hore aku jalan-jalan ke bandung</p>

      <button class="btn btn-primary">Submit</button>

    </form>

    <hr>
    <div class="form-group">
      <label for="lote">Lotre</label>
      <input type="number" class="form-control" v-model="lotre">
      {{lotre}}
    </div>
    <h1 v-if="lotre>3">{{lotre*3}}</h1>
    <h1 v-else-if="lotre>=1">{{lotre*1}}</h1>
    <h1 v-if="lotre==0">KALAH</h1>

  </div>
</template>

<script>
export default {
  data() {
    return {
      lotre: 0,
      name: "Ghany",
      date: "",
      provinsi: "Banten",
      listProvinsi: [
        { name: "Jawa Barat" },
        { name: "DKI Jakarta" },
        { name: "Banten" },
      ],
    };
  },
  methods: {},
};
</script>
