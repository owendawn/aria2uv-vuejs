<template>

  <el-menu
    id="download-menu"
    :default-active="this.$route.fullPath"
    class="el-menu-vertical-demo"
    @select="handleSelect"
    active-text-color="#fff"
    style="border-bottom:1px solid #d8d8d8;border-left:1px solid #d8d8d8;"
  >

    <router-link to="/download">
      <el-menu-item index="/download">
        <i class="el-icon-success"></i>
        <span slot="title">正在下载
          <el-badge
            class="mark"
            :value="this.$store.state.globalStat.numActive"
          />
        </span>
      </el-menu-item>
    </router-link>
    <router-link to="/wait">
      <el-menu-item index="/wait">
        <i class="el-icon-info"></i>
        <span slot="title">正在等待
          <el-badge
            class="mark"
            :value="this.$store.state.globalStat.numWaiting"
          />
        </span>
      </el-menu-item>
    </router-link>
    <router-link to="/finish">
      <el-menu-item index="/finish">
        <i class="el-icon-remove"></i>
        <span slot="title">已经结束
          <el-badge
            class="mark"
            :value="this.$store.state.globalStat.numStopped"
          />
        </span>
      </el-menu-item>
    </router-link>
    <div
      class="menu-tip"
      style=""
    >
      <h4>Just Kidding{{this.$store.state.globalStat.numStoppedTotal}}</h4>
      <span>
        ☺ -v- Jest with an ass and he will flap you in the face with his tail.
      </span>
    </div>
  </el-menu>

</template>
<script>
import store from "../store/modules/base/store.js"
export default {
  store,
  data() {
    return {
      isCollapse: true
    };
  },
  methods: {
    handleSelect(key, keyPath) {
      console.log(key, keyPath);
    }
  }
}
</script>
<style>
.el-menu-vertical-demo:not(.el-menu--collapse) {
  width: 198px;
  min-height: 400px;
}
#download-menu a {
    text-decoration:none;
}
#download-menu .el-menu-item i {
  line-height: 56px;
  font-size: 18pt;
}
#download-menu .el-menu-item.is-active {
  background-color: #315f54;
}
#download-menu .menu-tip {
  padding: 0 12px;
  text-align: center;
  line-height: 1.5rem;
  word-break: break-word;
  white-space: normal;
  border-top: 1px solid #d8d8d8;
}

#download-menu .el-badge__content {
  color: #fff;
  background-color: #6c757d;
  border-radius: 10px;
}
#download-menu .el-menu-item.is-active .el-badge__content {
  color: #212529 !important;
  background-color: #f8f9fa;
}
</style>
