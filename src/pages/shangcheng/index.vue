<template>
  <div class="page">
    <ViewBox class="shangcheng">
      <!-- <div class="top-input">
        <span class="add" v-if="location">{{location.city}}</span>
        <input placeholder='请输入商家名或地点' class="search"/>
      </div> -->
      <ScrollTab class="ScrollTab">
        <ScrollTabPanel :label="item.class_name" v-for="(item,index) in listArr" :key="index">
          <div class="class-wrap">
            <div v-for="(item,index) in item.son" :key="index" class="two-item" @click="toDetail(item.id)">
              <img v-lazy="item.two_sp_class_img" alt="" class="thumb">
              <p>{{item.fw_name}}</p>
            </div>
          </div>

        </ScrollTabPanel>
      </ScrollTab>
    </ViewBox>
  </div>
</template>

<script>
import { mapState } from 'vuex';
import { ViewBox, XInput } from "vux";
import { ScrollTab, ScrollTabPanel } from "vue-ydui/dist/lib.px/scrolltab";
export default {
  data() {
    return {
      listArr: []
    };
  },
  created() {
    this.setMetaTitle('商城');
    var _this = this;
    this.$axios.get( "/api/Show/ot_class").then(({ data }) => {
      _this.listArr = data;
    });
  },
  methods: {
    toDetail(id) {
      this.$router.push("/serviceList/" + id);
    }
  },
  computed:{
    ...mapState(["location"]),
  },
  components: {
    ScrollTab,
    ScrollTabPanel,
    ViewBox,
    XInput
  }
};
</script>

<style lang='scss'>
.ScrollTab {
  // margin-top: 1.2rem;
  padding-bottom: 50px;
  .yd-scrolltab-title{
    overflow-y: hidden;
  }
}
.shangcheng {
  .top-input {
    box-sizing: border-box;
    height: 1.2rem;
    display: flex;
    align-items: center;
    padding: 0.24rem 0.533333rem;
    @include font-dpr(19px);
    color: #292929;
    .add {
      margin-right: 0.333333rem;
      line-height: 1;
    }
    .search {
      padding-left: .266667rem;
      flex: 1;
      height: 0.693333rem;
      border: 1px solid #000000;
      border-radius: 0.346667rem;
      @include font-dpr(12px);
    }
  }
  .class-wrap {
    display: flex;
    flex-wrap: wrap;
    padding: 0.24rem;
    background: #ffffff;
    line-height: 1;
    padding-bottom: -0.4rem;
    .two-item {
      width: 33%;
      flex: none;
      display: inline-block;
      text-align: center;
      margin-bottom: 0.4rem;
      .thumb {
        width: 1.6rem;
        height: 1.2rem;
        margin-bottom: 0.24rem;
      }
    }
  }
  .yd-scrolltab-nav {
    background: #ffffff;
  }
  .yd-scrolltab-active {
    background: #f1f2f6;
  }
  .yd-scrolltab-content {
    background: #f1f2f6;
    padding-left: 0.933333rem;
  }
}
</style>