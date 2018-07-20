<template>
  <div class="page">
    <checkbox-group @change="checkboxChange">
      <label class="weui-cell weui-check__label" v-for="item in checkboxItems" :key="index">
        <checkbox class="weui-check" :value="item.value" :checked="item.checked" />
        <div class="weui-cell__hd weui-check__hd_in-checkbox">
          <icon class="weui-icon-checkbox_circle" type="circle" size="23" v-if="!item.checked"></icon>
          <icon class="weui-icon-checkbox_success" type="success" size="23" v-if="item.checked"></icon>
        </div>
        <div class="weui-cell__bd">{{item.name}}</div>
      </label>
    </checkbox-group>
  </div>
</template>

<script>
export default {
  props: {
    checkboxItems: {
      type: Array,
      default: []
    }
  },
  data() {},
  methods: {
    checkboxChange(e) {
      var checkboxItems = this.checkboxItems,
        values = e.mp.detail.value;
      for (var i = 0, lenI = checkboxItems.length; i < lenI; ++i) {
        checkboxItems[i].checked = false;
        for (var j = 0, lenJ = values.length; j < lenJ; ++j) {
          if (checkboxItems[i].value == values[j]) {
            checkboxItems[i].checked = true;
            break;
          }
        }
      }
      this.$emit("importCheckData", {
        file_url: values
      });
      this.checkboxItems = checkboxItems;
    }
  }
};
</script>

<style>
</style>