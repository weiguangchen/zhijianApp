<template>
    <!-- <Tabbar>
        <TabbarItem link='/shanghu/yanzheng'>
            <span slot="label">验证</span>
        </TabbarItem>
        <TabbarItem link='/shanghu/pingjia'>
            <span slot="label">评价</span>
        </TabbarItem>
        <TabbarItem link='/shanghu/jingying'>
            <span slot="label">经营</span>
        </TabbarItem>
        <TabbarItem link='/shanghu/me'>
            <span slot="label">我的</span>
        </TabbarItem>
    </Tabbar> -->
     <div class="my-tabbar">
        <router-link class="tabbar-item" to="/shanghu/yanzheng/index" tag="span">
            <i class="iconfont icon-shouye"></i><div>验证</div>
        </router-link>
        <router-link class="tabbar-item" to="/shanghu/pingjias/index" tag="span">
            <i class="iconfont icon-shangcheng"></i><div>评价</div>
        </router-link>
        <router-link class="tabbar-item" to="/shanghu/jingying/index" tag="span">
            <i class="iconfont icon-faxian"></i><div>经营</div>
        </router-link>
        <router-link class="tabbar-item" to="/shanghu/me/index" tag="span">
            <i class="iconfont icon-wode"></i><div>我的</div>
        </router-link>
    </div>
</template>

<script>
import { Tabbar, TabbarItem } from "vux";

export default {
  data() {
    return {};
  },
  name:'shanghuTab',
  components: {
      Tabbar,TabbarItem
  }
};
</script>

<style lang='scss'>
.my-tabbar{
    background: #ffffff;
    position: fixed;
    left: 0;
    bottom: 0;
    width: 100%;
    height: 50px;
    display: flex;
     z-index: 200;
    .tabbar-item{
        display: flex;
        flex-direction: column;
        justify-content: center;
        font-size: 12px;
        .iconfont{
            font-size: 25px
        }
        text-align: center;
        flex: 1;
    }
}
</style>