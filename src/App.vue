<template>
  <div class="container">
    <Profile />
    <Activities
      v-for="(activity, index) of activities"
      :key="index"
      :index="index"
      :activity="activity"
    />
  </div>
</template>

<script>
import { ref } from "@vue/reactivity";
import { onMounted, provide } from "@vue/runtime-core";
import Activities from "./components/Activities.vue";
import Profile from "./components/Profile.vue";

export default {
  name: "App",
  components: { Activities, Profile },
  setup() {
    const activities = ref([]);
    const stateFilter = ref(1);
    provide("activities", activities);
    provide("stateFilter", stateFilter);

    onMounted(() => {
      fetch("data.json")
        .then((res) => res.json())
        .then((data) => {
          activities.value = data;
        });
    });
    return { activities };
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
:root {
  --Mobile: 375px;
  --Desktop: 1440px;

  /* ### Primary */
  --Blue: hsl(246, 80%, 60%);
  /* ### Neutral */
  --Very-dark-blue: hsl(226, 43%, 10%);
  --Dark-blue: hsl(235, 46%, 20%);
  --Desaturated-blue: hsl(235, 45%, 61%);
  --Pale-Blue: hsl(236, 100%, 87%);
}
body {
  background-color: var(--Very-dark-blue);
  color: #fff;
  font-size: 18px;
  font-family: "Rubik", sans-serif;
}
#app {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}
.container {
  display: grid;
  grid-template-areas:
    "profile . . ."
    "profile . . .";
  gap: 13px 30px;
  justify-content: center;
  align-items: center;
}

@media (max-width: 1290px) {
  .container {
    width: 90%;
    grid-template-areas: "profile";
    grid-auto-columns: 100%;
    padding: 65px 0;
  }
  .profile, .activities {
    width: 100%;
    max-width: 600px;
    margin: auto;
  }
  .profile__body {
    height: auto;
    flex-direction: row;
    align-items: center;
  }
  .profile__body__img {
    margin: 0 1.2em 0 0;
  }
  .profile__body__name {
    font-size: 2em;
  }
  .profile__footer {
    flex-direction: row;
    justify-content: space-around;
  }
  
  .activities__body {
    padding: 28px;
  }
  .current-previous-container {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .hours {
    font-size: 2em;
    padding-top: 9.5px;
  }
  .last-week {
    padding-top: 5px;
  }
}
</style>
