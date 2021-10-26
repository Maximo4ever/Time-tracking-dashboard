<template>
  <div class="profile__footer" @click="filterData">
    <p class="profile__footer__time" id="daily">Daily</p>
    <p class="profile__footer__time active" id="weekly">Weekly</p>
    <p class="profile__footer__time" id="mounthly">Mounthly</p>
  </div>
</template>

<script>
import { inject } from "@vue/runtime-core";
export default {
  setup() {
   const stateFilter = inject("stateFilter");

    const filterData = (e) => {
      if (e.target.className === "profile__footer__time") {
        if (e.target.id === "daily") stateFilter.value = 0;
        if (e.target.id === "weekly") stateFilter.value = 1;
        if (e.target.id === "mounthly") stateFilter.value = 2;
        e.path[1].childNodes.forEach((element) => {
          element.classList.remove("active")
        });
        e.target.classList.add("active")
      }
    };

    return { filterData };
  },
};
</script>

<style>
.profile__footer {
  display: flex;
  flex-direction: column;
  row-gap: 20px;
  margin-top: -22px;
  padding: 55px 30px 33px;
  border-radius: 15px;
  background-color: var(--Dark-blue);
}
.profile__footer__time {
  cursor: pointer;
  color: var(--Desaturated-blue);
  transition: color 0.2s;
}
.profile__footer__time:hover,
.profile__footer__time.active {
  color: #fff;
}
</style>
