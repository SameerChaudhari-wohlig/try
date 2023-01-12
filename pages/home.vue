<template>
  <v-card class="mx-auto" max-width="100%">
    <v-toolbar color="cyan-lighten-1">
      <v-btn variant="text" icon="mdi-menu"></v-btn>

      <v-toolbar-title>Instagram</v-toolbar-title>

      <v-spacer></v-spacer>
      <v-text-field placeholder="Search ..." v-model="search"></v-text-field>
      <!-- <v-btn v-model="search" variant="text" icon="mdi-magnify" ></v-btn> -->
    </v-toolbar>
    <v-list v-for="data in filteredinsta" :key="data" lines="one">
      <v-list-item class="txt">
        <v-avatar size="100" rounded="0">
          <v-img :src="data.user.image"></v-img>
        </v-avatar>
        <div>
          <h2 class="pt-3">{{ data.user.full_name }}</h2>
          <h3>{{ data.user.username }}</h3>
        </div>
      </v-list-item>
    </v-list>
  </v-card>
</template>

<script setup>
import data from "../instaData";
const search = ref("");
let posts = ref([]);
// data = data.body.users;
// const insta = ref(data);
// let User = ref([]);
// User = body.user;

// const url =  "https://instagram47.p.rapidapi.com/search?search=ig_sameer_tweet"


// const options = {
//   method: "GET",
//   headers: {
//     "X-RapidAPI-Key": "ad8b4ad4b9mshae7a0a0393e1946p1f42b9jsn3d69d120c87b",
//     "X-RapidAPI-Host": "instagram47.p.rapidapi.com",
//     "Content-Type": "application/json",
//   },
// }

// const { data, pending, error, refresh } = await useFetch(url, options);
// console.log(data, "data from response");
// if (error) {
//   console.log(error);
// }

const filteredinsta = computed(() => {
  if (search.value) {
    // console.log("inside if");
    return [...data["body"]["users"]].filter((item) => {
      return search.value
        .toLocaleLowerCase()
        .split(" ")
        .every((v) => item.user.full_name.toLocaleLowerCase().includes(v));
    });
  } else {
    // console.log("inside else");
    return data["body"]["users"];
  }
});
</script>

<style>
.img {
  padding-left: 20px;
}

.v-text-field .v-field--no-label input,
.v-text-field .v-field--active input {
  margin-top: 26px;
}

.txt .v-list-item__content {
  display: flex;
}
</style>
