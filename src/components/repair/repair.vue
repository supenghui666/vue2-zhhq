<template>
  <div class="outsale">
    <div class="logo">
      <h1>建邺智慧后勤管理中心</h1>
      <div>
        <img class="user" src="../login/already_login.png" @click="$router.push('/login')">
        <router-link to="#" class="go_sale">维护报修</router-link>
        <span class="back_home" @click="$router.go(-1)">返回上一页</span>
      </div>
    </div>
    <transition name="fade">
      <div v-show="showRule" class="rule_detail">
        <i class="el-icon-close close_rule" @click="showRule?showRule=false:showRule"></i>
        <h5>
          <span>维护报修规则：</span>
        </h5>
        <ul>
          <li>1、每周五更新预定菜单；</li>
          <li>2、预定时间：8：00-9：00、12：00-14：00；</li>
          <li>3、预定时间内可以，可以取消预定内容，14：00之后，无法取消预定状态；</li>
          <li>4、面点：每天最多可选择两个品类，每个最多十个预订量；</li>
          <li>5、凉菜：每个品类只能一份预订量；</li>
        </ul>
      </div>
    </transition>
    <div class="all_agency">
      <div class="nav">
        <router-link to="/repair/applyRepair">维护报修</router-link>
        <!-- <router-link to="/repair/myApply">我的申请</router-link> -->
      </div>
      <router-view class="food_container"></router-view>
    </div>
    <div v-show="showInstruction" class="fixed_" @click="showInstruction=false"></div>
    <div class="explain" @click="showInstruction=!showInstruction">操作说明</div>
    <div v-show="showInstruction" class="instruction">
      <img src="~common/images/7_weihubaoxiu.png">
    </div>
  </div>
</template>
<script>
  export default {
    data: () => ({
      showRule: false,
      showInstruction: false
    }),
    computed: {
      id () {
        return this.$store.getters['setRepairID']
      }
    }
  }
</script>
<style lang="stylus" rel="stylesheet/stylus" scoped>
@import '~common/css/common.styl'
.all_agency
  position:absolute
  width:70%
  left:50%
  margin-left:-35%
  top:180px
  min-width:700px
  .nav
    position:absolute
    top:0
    left:0
    height:25px
    z-index:66666
  div
    a
      display:inline-block
      width:80px
      height:25px
      line-height:25px
      color:#fff
      background-color:#476ade
      text-align:center
      border-radius:0 20px 0 0
      font-size:14px
      text-decoration:none
    .router-link-active
      background-color:#1c3da6
</style>