<template>
  <div class="profile__body">
    <img
      src="../assets/image-jeremy.png"
      alt="user profile"
      class="profile__body__img"
    />
    <div class="profile__body__info">
      <span class="profile__body__report">Report for</span>
      <h1 class="profile__body__name">
        Jeremy
        Robson
      </h1>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style>
.profile__body {
  position: relative;
  height: 370px;
  display: flex;
  align-items: start;
  justify-content: start;
  flex-direction: column;
  background-color: var(--Blue);
  padding: 30px 30px;
  border-radius: 15px;
}
.profile__body__img {
  height: 90px;
  border: 4px solid var(--Pale-Blue);
  border-radius: 50%;
  margin-bottom: 2.2em;
}
.profile__body__report {
  color: var(--Pale-Blue);
  font-size: 17px;
  margin-bottom: 5px;
}
.profile__body__name {
  font-weight: 300;
  font-size: 2.45em;
}
</style>
