<template>
  <form class="search">
    <div class="search__input">
      <!-- <mat-icon class="search__inputIcon" aria-hidden="false" aria-label="Example home icon">search</mat-icon> -->
      <input v-model="text" />
      <!-- <mat-icon aria-hidden="false" aria-label="Example home icon">mic</mat-icon> -->
    </div>
    <div class="search__buttons">
      <button @click="print">Google Search</button>
      <button>I'm Feeling Lucky</button>
    </div>
    <!-- <div *ngIf="hideButtons" class="search__buttonsHidden">
        <button mat-stroked-button (click)="print(searchQuery.value); $event.preventDefault()">Google Search</button>
        <button mat-stroked-button>I'm Feeling Lucky</button>

    </div> -->
  </form>
</template>

<script>
import router from "@/router";
import axios from "axios";
console.log("DPI");
console.log(process.env.API_KEY);
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      text: "",
    };
  },
  methods: {
    print(e) {
      e.preventDefault();

      // fetch(
      //   `https://www.googleapis.com/customsearch/v1?key=${API_KEY}&cx=9ec571f86697d07ac&q=google`
      // )
      //   .then((res) => res.json())
      //   .then((result) => {
      //     console.log(result);
      //     this.$router.push({
      //       name: "About",
      //       params: { name: this.$data.text, data: result },
      //     });
      //   });
      this.$router.push({
        name: "About",
        params: { name: this.$data.text, data: this.$data.text },
      });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.search__input {
  display: flex;
  align-items: center;
  border: 1px solid lightgray;
  height: 30px;
  padding: 10px 20px;
  border-radius: 999px;
  width: 75vw;
  margin: 0 auto;
  margin-top: 40px;
  max-width: 560px;
}

.search__input > input {
  flex: 1;
  padding: 10px 20px;
  border: none;
  font-size: medium;
}

.search__input > input:focus {
  outline-width: 0;
}

.search__inputIcon {
  color: gray;
}

.search__buttons {
  margin-top: 30px;
  display: flex;
  justify-content: center;
}

.search__buttons > button {
  margin: 5px;
  padding: 7px 15px;
  font-weight: normal;
  border: 1px solid white;
  background-color: #f8f8f8;
  color: #5f6368;
}

.search__buttons > button:hover {
  box-shadow: 0 1px 1px rgb(0 0 0 / 10%);
  background-color: #f8f9fa;
  border: 1px solid #dadce0;
  color: #202124;
}

.search__buttonsHidden {
  display: none !important;
}
</style>
