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
    <!-- <h2>{{ testdata }}</h2> -->
    <pre v-if="responseData && responseData.length">{{ responseData  }}</pre>
    <pre> </pre>
  </div>
</template>

<script setup>
var myHeaders = new Headers();
// var testdata = "user";
// var user = "i am a user";
myHeaders.append("X-RapidAPI-Host", "instagram47.p.rapidapi.com");
myHeaders.append(
  "X-RapidAPI-Key",
  "ad8b4ad4b9mshae7a0a0393e1946p1f42b9jsn3d69d120c87b"
);

var requestOptions = {
  method: "GET",
  headers: myHeaders,
  redirect: "follow",
};


let responseData = ref([]);

onMounted(async () => {
  await fetch(
    "https://ac17bbe4-d0b1-47a1-8f66-0c6966a510e8.mock.pstmn.io/search?search=irtrtrtrtrtrtrtrt",
    requestOptions
  )
    .then((response) => response.json())
    .then((result) => {
      if (result && result.body && result.body.users) {
        responseData = result.body.users;
        console.log(responseData);
      }
    })
    .catch((error) => console.log("error", error));
});
</script>

<style></style>
