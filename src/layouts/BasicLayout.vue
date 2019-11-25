<template>
<div :class="[`nav-theme-${navTheme}`, `nav-layout-${navLayout}`]">
  <a-layout id="components-layout-demo-side" style="min-height: 100vh">
    <a-layout-sider 
    v-if="navLayout === 'left'"
    :theme="navTheme"
    collapsible v-model="collapsed" :trigger="null">
      <div class="logo">Ant Desgin Vue Pro</div>
      <SiderMenu></SiderMenu>
    </a-layout-sider>
    <a-layout>
      <a-layout-header style="background: #fff; padding: 0">
        <a-icon class="trigger" :type="collapsed?'menu-fold':'menu-unfold'" @click="collapsed = !collapsed"></a-icon>
        <Header />
      </a-layout-header>

      <!-- <a-layout-content style="margin: 0 16px">
        <a-breadcrumb style="margin: 16px 0">
          <a-breadcrumb-item>User</a-breadcrumb-item>
          <a-breadcrumb-item>Bill</a-breadcrumb-item>
        </a-breadcrumb>
        <div :style="{ padding: '24px', background: '#fff', minHeight: '360px' }">
          Bill is a cat.
        </div>
      </a-layout-content> -->
      <a-layout-content style="margin: 24px 24px 0">
        <router-view></router-view>
      </a-layout-content>
      <a-layout-footer style="text-align: center">
        <Footer />
        <SettingDrawer></SettingDrawer>
      </a-layout-footer>
    </a-layout>
  </a-layout>
</div>
</template>

<script>
  import Header from "./Header";
  import Footer from "./Footer";
  import SiderMenu from "./SiderMenu";
  import SettingDrawer from "../components/settingDrawer"
  export default {
    data() {
      return {
        collapsed: false,
      }
    },
    computed: {
      navTheme(){
        return this.$route.query.navTheme || 'dark';
      },
      navLayout(){
        return this.$route.query.navLayout || 'left';
      }
    },
    components: {
      Header,
      Footer,
      SiderMenu,
      SettingDrawer
    }
  }
</script>

<style scoped>
  .trigger {
    padding: 0 20px;
    line-height: 60px;
    font-size: 20px;
  }
  .logo{
    height: 64px;
    line-height: 64px;
    text-align: 64px;
    overflow: hidden;
  }
  .nav-theme-dark >>> .logo{
    color: #ffffff;
  }

</style>