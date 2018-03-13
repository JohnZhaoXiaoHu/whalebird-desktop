<template>
  <div id="side_menu">
    <div class="profile-wrapper">
      <div class="profile">
        <span>@{{ username }}</span>
        <span>{{ account.domain }}</span>
      </div>
    </div>
    <el-menu
      default-active="1"
      background-color="#373d48"
      text-color="#909399"
      active-text-color="#ffffff"
      :router="true"
      class="el-menu-vertical timeline-menu">
      <el-menu-item index="1" :route="{path: `/${id()}/home`}">
        <icon name="home"></icon>
        <span>Home</span>
      </el-menu-item>
      <el-menu-item index="2" :route="{path: `/${id()}/notifications`}">
        <icon name="bell"></icon>
        <span>Notification</span>
      </el-menu-item>
      <el-menu-item index="3" :route="{path: `/${id()}/favorites`}">
        <icon name="star"></icon>
        <span>Fav</span>
      </el-menu-item>
      <el-menu-item index="4" :route="{path: `/${id()}/local`}">
        <icon name="users"></icon>
        <span>LocalTimeline</span>
      </el-menu-item>
      <el-menu-item index="5" :route="{path: `/${id()}/global`}">
        <icon name="globe"></icon>
        <span>PublicTimeline</span>
      </el-menu-item>
    </el-menu>
  </div>
</template>

<script>
import { mapState } from 'vuex'

export default {
  name: 'side-menu',
  computed: {
    ...mapState({
      account: state => state.TimelineSpace.account,
      username: state => state.TimelineSpace.username
    })
  },
  methods: {
    id () {
      return this.$route.params.id
    }
  }
}
</script>

<style lang="scss" scoped>
#side_menu {
  .profile-wrapper {
    background-color: #373d48;
    position: fixed;
    top: 0;
    left: 65px;
    width: 180px;
    height: 60px;

    .profile {
      color: #ffffff;
      font-weight: bold;
      padding: 10px 20px;
    }
  }

  .timeline-menu {
    position: fixed;
    top: 60px;
    left: 65px;
    height: 100%;
    width: 180px;
  }
}
</style>