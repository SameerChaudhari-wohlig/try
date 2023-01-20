<template>
  <div>
    <v-toolbar color="cyan-lighten-1">
      <v-btn variant="text" icon="mdi-menu"></v-btn>
      <v-toolbar-title>Instagram</v-toolbar-title>
      <nuxt-link class="edit" to="/"><v-btn>Home</v-btn></nuxt-link>
      <nuxt-link class="edit" to="/home"><v-btn>User</v-btn></nuxt-link>
      <nuxt-link class="edit" to="/about"><v-btn>About</v-btn></nuxt-link>
      <!-- <v-text-field placeholder="Search ..." v-model="search"></v-text-field> -->
    </v-toolbar>
    <h1>About</h1>
    <!-- <pre>{{data}}</pre> -->
    <v-card class="mx-auto" max-width="100%">
      <v-list v-for="post in posts" :key="post" lines="one">
        <v-list-item class="txt">
          <v-avatar size="100" rounded="0">
            <v-img :src="post.thumbnailUrl"></v-img>
          </v-avatar>
          <div>
            <h3>{{ post.id }}</h3>
            <h2 class="pt-3">{{ post.title }}</h2>
          </div>
        </v-list-item>
      </v-list>
    </v-card>
    <!-- <div>
      <v-card class="mx-auto" max-width="100%">
        <v-list v-for="response in responseData" :key="response" lines="one">
          <v-list-item class="txt">
            <v-avatar size="100" rounded="0">
              <v-img :src="responseData[0].user.profile_pic_url"></v-img>
            </v-avatar>
            <div>
              <h2 class="pt-3">{{ responseData[0].user.username }}</h2>
              <h3>{{ responseData[0].user.full_name }}</h3>
            </div>
          </v-list-item>
        </v-list>
      </v-card>
    </div> -->

    <!-- <h2>{{ testdata }}</h2>    -->
    <!-- <pre v-if="responseData && responseData.length">{{ responseData }}</pre> -->
    <!-- <pre v-for="response in responseData" :key="response">{{responseData[0]}}</pre> -->
  </div>
</template>

<script setup>
const url = "https://jsonplaceholder.typicode.com/photos/";

let posts = ref([]);
const { data } = await useFetch(url);
posts = data;

// var myHeaders = new Headers();

// myHeaders.append("X-RapidAPI-Host", "instagram47.p.rapidapi.com");
// myHeaders.append(
//   "X-RapidAPI-Key",
//   "ad8b4ad4b9mshae7a0a0393e1946p1f42b9jsn3d69d120c87b"
// );

// var requestOptions = {
//   method: "GET",
//   headers: myHeaders,
//   redirect: "follow",
// };

// let responseData = ref([{}]);

// onMounted(async () => {
//   await fetch(
//     "https://ac17bbe4-d0b1-47a1-8f66-0c6966a510e8.mock.pstmn.io/search?search=irtrtrtrtrtrtrtrt",
//     requestOptions
//   )
//     .then((response) => response.json())
//     .then((result) => {
//       if (result && result.body.users && result.body.users) {
//         responseData = result.body.users;
//         console.log(responseData);
//       }
//     })
//     .catch((error) => console.log("error", error));
// });
</script>

<style></style>
