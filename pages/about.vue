<template>
  <div>
    <h1>About</h1>
    <h2>{{  }}</h2>
    <pre>{{data}}</pre>
  </div>
</template>

<script setup>
var myHeaders = new Headers();
var testdata = "user";
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

const { response: data } = await useAsyncData("response", () => {
  return new Promise((resolve, reject) => {
    fetch(
      "https://ac17bbe4-d0b1-47a1-8f66-0c6966a510e8.mock.pstmn.io/search?search=irtrtrtrtrtrtrtrt",
      requestOptions
    )
      .then((response) => response.text())
      .then((result) => {
        resolve(result);
        console.log(result);
      })
      .catch((error) => console.log("error", error));
  }); 
});
// console.log(response);
</script>

<style></style>
