<template>
  <div class="profile">
    <ProfileBody />
    <ProfileFooter />
  </div>
</template>

<script>
import ProfileBody from './ProfileBody.vue'
import ProfileFooter from './ProfileFooter.vue'
export default {
  components: { ProfileFooter, ProfileBody },
    name: "Profile"
}
</script>

<style>
.profile {
  grid-area: profile;
  width: 285px;
}
</style>