<template>
  <div class="searchPage">
    <div class="searchPage__header">
      <router-link 
      to="/"
        ><img
          class="searchPage__logo"
          src="https://www.google.com/images/branding/googlelogo/1x/googlelogo_color_272x92dp.png"
          alt=""
      /></router-link>
      <div class="seachPage__headerBody">
        <form class="search">
          <div class="search__input">
            <input v-model="searchQuery" />
          </div>
          <!-- <div *ngIf="!hideButtons" class="search__buttons">
                    <button mat-stroked-button (click)="print(searchQuery.value); $event.preventDefault()">Google
                        Search</button>
                    <button mat-stroked-button>I'm Feeling Lucky</button>

                </div> -->
          <div class="search__buttonsHidden">
            <button @click="retreiveData2" type="submit">Google Search</button>
            <button>I'm Feeling Lucky</button>
          </div>
        </form>
      </div>
    </div>
    <div v-if="employees.length != 0" class="searchPage__result">
      <p class="searchPage__resultCount">
        About {{ employees.searchInformation.totalResults }} results in
        {{ employees.searchInformation.formattedSearchTime }} for {{ data }}
      </p>
      <div
        v-for="item in employees.items"
        :key="item.link"
        class="searchPage__results"
      >
        <a href="{{item.link}}" class="searchPage__topLink">{{
          item.displayLink
        }}</a>
        <a class="searchPage__resultTitle" href="{{item.link}}">
          <h2>{{ item.title }}</h2>
        </a>
        <p class="searchPage__resultSnippet">
          {{ item.snippet }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
let API_KEY = "AIzaSyBa_aNPMW56QnludqsdgAHUHmxDbjSgGQ0";

import axios from "axios";
export default {
  name: "About",
  props: {
    data: String,
  },
  data() {
    return {
      employees: [],
      searchQuery: "",
    };
  },
  created() {
    this.retreiveData();
  },
  methods: {
    retreiveData() {
      axios
        .get(
          `https://www.googleapis.com/customsearch/v1?key=${process.env.API}&cx=9ec571f86697d07ac&q=${this.data}`
        )
        .then((response) => {
          this.employees = response.data;
        })
        .catch((e) => {
          console.log(e);
        });
    },
    retreiveData2(e) {
      e.preventDefault();
      
      axios
        .get(
          `https://www.googleapis.com/customsearch/v1?key=${process.env.API}&cx=9ec571f86697d07ac&q=${this.searchQuery}`
        )
        .then((response) => {
          this.employees = response.data;
        })
        .catch((e) => {
          console.log(e);
        });
    },
  },
};
</script>


<style>
.searchPage__header {
  display: flex;
  position: sticky;
  top: 0;
  background-color: white;
  z-index: 100;
  align-items: flex-start;
  padding: 30px;
  border-bottom: 1px solid lightgray;
}

.searchPage__logo {
  object-fit: contain;
  height: 50px;
  margin-right: 50px;
}

/* This is search tab */
.search__input {
  display: flex;
  align-items: center;
  border: 1px solid lightgray;
  height: 30px;
  padding: 10px 20px;
  border-radius: 999px;
  width: unset;
  margin: unset;
  margin-top: 0;
  max-width: unset;
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

.searchPage__resultCount {
  color: #70757a;
  font-size: 14px;
  margin-left: 60px;
  margin-top: 20px;
}

.searchPage__results {
  max-width: 650px;
  margin-top: 10px;
  margin-left: 60px;
  margin-bottom: 50px;
}
.searchPage__resultTitle {
  text-decoration: none;
  color: #1a0dab;
}

.searchPage__results > .searchPage__topLink {
  color: #202124;
}
</style>