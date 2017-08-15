<template>
    <div class="wrapper">
        <v-head></v-head>
        <v-sidebar></v-sidebar>
        <div class="content">
            <transition name="move" mode="out-in">
                <router-view></router-view>
            </transition>
        </div>
        <!-- <v-foot></v-foot> -->
        <div class="app-foot">
            <p>© 2017 杭州能联科技有限公司</p>
        </div>
    </div>
</template>

<script>
import vHead from './Header.vue';
import vSidebar from './Sidebar.vue';
import vFoot from './Footer.vue'
export default {
    components: {
        vHead, vSidebar, vFoot
    }
}
</script>
<style>
.app-foot {
  text-align: center;
  height: 80px;
  width: 100%;
  line-height: 80px;
  background: #e3e4e8;
  clear: both;
  margin-top: 30px;
}
</style>
