<template>
  <div class="table-users">
    <div v-for="(user, i) in item.users.slice(0, 5)" :key="user.profile_url">
      <div :style="`position: absolute; left: -${i * 6}px`">
        <img :src="require(`~/assets/table avatars/${user.profile_url}`)" />
      </div>
    </div>
    <div v-if="item.users.slice(5).length">
      <div class="profile-text-avatar">
        <div>
          <span> +{{ item.users.slice(5).length }} </span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["item"],
};
</script>

<style>
.table-users {
  display: flex;
  align-items: center;
}

.table-users div {
  position: relative;
  width: 24px;
  height: 24px;
}

.profile-text-avatar {
  position: absolute;
  left: -30px;
}

.profile-text-avatar div {
  background-color: #f9f5ff;
  width: 26px;
  height: 26px;
  border: 3px solid #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
}

.profile-text-avatar span {
  color: #7f56d9;
  font-size: 12px;
  font-weight: 500;
}
</style>