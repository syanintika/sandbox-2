<template>
  <div>
    <div class="row">
      <div class="col-md-4" v-for="(item,i) in listClass" :key="i">
        <class-item :name="item.name" :desc="item.desc" />
      </div>
    </div>
  </div>
</template>
<script>
export default {
  asyncData() {
    return {
      listClass: [
        { name: "Fullstack 5", desc: "Ini deskripsi fullsatck 5" },
        { name: "Fullstack 6", desc: "Ini deskripsi fullsatck 6" },
        { name: "Fullstack 7", desc: "Ini deskripsi fullsatck 7" },
        { name: "Fullstack 8", desc: "Ini deskripsi fullsatck 8" },
        { name: "Fullstack 9", desc: "Ini deskripsi fullsatck 9" },
      ],
    };
  },
};
</script>