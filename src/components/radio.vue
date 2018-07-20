<template>
  <div class="page">
    <radio-group @change="radioChange">
      <label class="weui-cell weui-check__label" v-for="item in radioItems" :key="index">
        <radio class="weui-check" :value="item.value" :checked="item.checked" />
        <div class="weui-cell__bd">{{item.name}}</div>
        <div class="weui-cell__ft weui-cell__ft_in-radio" v-if="item.checked">
          <icon class="weui-icon-radio" type="success_no_circle" size="16"></icon>
        </div>
      </label>
    </radio-group>
  </div>
</template>
<script>
export default {
  props: {
    radioItems: {
      type: Array,
      default: []
    }
  },
  data: function() {},
  methods: {
    radioChange: function(e) {
      let radioItems = this.radioItems;
      for (let i = 0; i < radioItems.length; ++i) {
        radioItems[i].checked = radioItems[i].value === e.mp.detail.value;
      }
      this.$emit("importRadioData", {
        file_url: e.mp.detail.value
      });
      this.radioItems = radioItems;
    }
  }
};
</script>
>