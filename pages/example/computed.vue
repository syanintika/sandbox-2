<template>
  <div>
    <h4>Belajar Computed</h4>
    <div>
      <ol>
        <li v-for="(book,i) in books" :key="i">{{book}}</li>
      </ol>
    </div>
    <h5>{{bookLength}}</h5>
    <div>
      <h5>Fullname : {{fullname}}</h5>
      <h5>firstname : {{firstName}}</h5>
      <h5>lastname : {{lastName}}</h5>
      <input class="form-control" type="text" v-model="fullname" />
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      firstName: "Ghany",
      lastName: "Ersa",
      books: ["Buku tulis", "Buku cerita", "Buku baca", "Novel"],
    };
  },
  computed: {
    fullname: {
      set(value) {
        //        0       1      2
        // value = "GHANY ABDILLAH ERSA";
        const [first, ...lastname] = value.split(" ");
        this.firstName = first;
        this.lastName = lastname.join(" ");
      },
      get() {
        debugger;
        return this.firstName + " " + this.lastName;
      },
    },
    bookLength() {
      return this.books.length > 0
        ? "Bukunya " + this.books.length
        : "Gak punya buku";
    },
  },
};
</script>