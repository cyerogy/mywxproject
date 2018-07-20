<template>
  <div class="page">
    <div class="page__bd">
      <div class="weui-cells__title">带图标、说明的列表项</div>
      <div class="weui-cells weui-cells_after-title">
        <div class="weui-cell">
          <div class="weui-cell__bd">标题文字</div>
          <div class="weui-cell__ft">说明文字</div>
        </div>
        <div class="weui-cell">
          <div class="weui-cell__bd">标题文字</div>
          <div class="weui-cell__ft">说明文字</div>
        </div>
      </div>

      <div class="weui-cells__title">带图标、说明、跳转的列表项</div>
      <div class="weui-cells weui-cells_after-title">
        <navigator url="" class="weui-cell weui-cell_access" hover-class="weui-cell_active">
          <div class="weui-cell__bd">cell standard</div>
          <div class="weui-cell__ft weui-cell__ft_in-access">说明文字</div>
        </navigator>
        <navigator url="" class="weui-cell weui-cell_access" hover-class="weui-cell_active">
          <div class="weui-cell__bd">cell standard</div>
          <div class="weui-cell__ft weui-cell__ft_in-access">说明文字</div>
        </navigator>
      </div>

      <div class="weui-cells__title">radiogroup组件</div>
      <div class="weui-cells weui-cells_after-title">
        <radiogroup :radioItems="rItems" @importRadioData="getRadioResult"></radiogroup>
      </div>

      <div class="weui-cells__title">checkgroup组件</div>
      <div class="weui-cells weui-cells_after-title">
        <checkgroup :checkboxItems="cItems" @importCheckData="getCheckResult"></checkgroup>
      </div>
    </div>
  </div>
</template>

<script>
// Use Vuex
import base64 from "../../../src/images/base64";
import radiogroup from "@/components/radio.vue";
import checkgroup from "@/components/check.vue";
export default {
  components: { radiogroup, checkgroup },
  data() {
    return {
      icon: "",
      rItems: [
        { name: "男", value: "0" },
        { name: "女", value: "1", checked: true }
      ],
      cItems: [
        { name: "standard is dealt for u.", value: "0", checked: true },
        { name: "standard is dealicient for u.", value: "1", checked: false }
      ]
    };
  },
  mounted() {
    this.icon = base64.icon20;
  },
  methods: {
    getRadioResult: function() {
      let args = Array.from(arguments);
      console.log(args);
    },
    getCheckResult: function() {
      let args = Array.from(arguments);
      console.log(args);
    }
  }
};
</script>
<style>
</style>
