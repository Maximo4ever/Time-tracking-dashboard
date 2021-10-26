<template>
  <div class="activities">
    <ActivityBanner :index="index" />
    <ActivityBody :activity="activity" />
  </div>
</template>

<script>
import ActivityBanner from './ActivityBanner.vue';
import ActivityBody from './ActivityBody.vue';

export default {
  components: { ActivityBanner, ActivityBody },
  name: "Activities",
  props: {
    activity: {
      type: Object,
      required: true,
    },
    index: {
      type: Number,
      required: true,
    },
  },
};
</script>

<style>
.activities {
  width: 285px;
  transform: translateY(-10px);
}
</style>
