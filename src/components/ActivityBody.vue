<template>
  <div class="activities__body">
    <div class="activity-container">
      <h3 class="activity__title">{{ activityObj.title }}</h3>
      <img
        src="../assets/icon-ellipsis.svg"
        alt="icon ellipsis"
        class="activity__options"
      />
    </div>
    <div class="current-previous-container">
      <h4 class="hours">{{ activityObj.current }}hrs</h4>
      <p class="last-week">Last Week - {{ activityObj.previous }}hrs</p>
    </div>
  </div>
</template>

<script>
import { inject, ref, watchEffect } from "@vue/runtime-core";
export default {
  props: {
    activity: {
      type: Object,
      required: true,
    },
  },
  setup(props) {
    const stateFilter = inject("stateFilter");
    const activityObj = ref({
      title: props.activity.title,
      current: Object.values(props.activity.timeframes)[stateFilter.value].current,
      previous: Object.values(props.activity.timeframes)[stateFilter.value].previous,
    });
    watchEffect(() => {
      console.log(stateFilter.value);
      activityObj.value.title = props.activity.title;
      activityObj.value.current = Object.values(props.activity.timeframes)[stateFilter.value].current;
      activityObj.value.previous = Object.values(props.activity.timeframes)[stateFilter.value].previous;
    });
    return { stateFilter, activityObj };
  },
};
</script>

<style>
.activities__body {
  padding: 26px 26px 40px;
  background-color: var(--Dark-blue);
  border-radius: 15px;
  height: 100%;
}
.activity-container {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.activity__title {
  font-weight: 500;
  font-size: 19px;
}
.activity__options {
  padding: 10px 5px;
  cursor: pointer;
}
.hours {
  font-size: 3em;
  font-weight: 300;
  padding: 22px 0 9.5px;
}
.last-week {
  color: var(--Desaturated-blue);
}
</style>
