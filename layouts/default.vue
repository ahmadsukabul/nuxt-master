<template>
  <div>
    halo
    <input v-model="data" placeholder="text" />
    <NuxtPage />
  </div>
</template>
<script setup>
import { ref, watch } from "vue";

const data = ref();

const route = useRoute();
// const router = useRouter()

console.log(route);
// watch(route, (value) => {
//     console.log(value)
//     console.log('watch 2')
//     // menu.isOpen = false
// })
watch(
  route,
  (newV, oldV) => {
    console.log("log vsion");
    axios.get("/api/version").then((r) => {
      if (r.data.last_build) {
        version.value = r.data;
      }
    });
    if (newV !== oldV) {
      location = location.origin + to.fullPath;
    } else {
      console.log("version same");
    }
  },
  { deep: true }
);

watch(data, (newV, oldV) => {
  console.log("log daa");
});
</script>
