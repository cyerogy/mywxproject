<template>
  <div class="page">
    <div class="weui-uploader__bd">
      <div class="weui-uploader__files" id="uploaderFiles">
        <div v-for="item in files" :key="index">
          <div class="weui-uploader__file image-list" :id="item">
            <image @click="predivImage" class="weui-uploader__img" :src="item" mode="aspectFill" />
            <a class="image-delete" @click="deleteImage(index)">X</a>
          </div>
        </div>
      </div>
      <div class="weui-uploader__input-box">
        <div class="weui-uploader__input" @click="chooseImage"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      files: []
    };
  },
  methods: {
    chooseImage(e) {
      var _this = this;
      wx.chooseImage({
        sizeType: ["original", "compressed"], // 可以指定是原图还是压缩图，默认二者都有
        sourceType: ["album", "camera"], // 可以指定来源是相册还是相机，默认二者都有
        success: function(res) {
          // 返回选定照片的本地文件路径列表，tempFilePath可以作为img标签的src属性显示图片
          _this.files = _this.files.concat(res.tempFilePaths);
          //连接后台接口
        },
        fail: function() {
          console.log("fail");
        },
        complete: function() {
          console.log("commplete");
        }
      });
    },
    predivImage(e) {
      wx.previewImage({
        current: e.currentTarget.id, // 当前显示图片的http链接
        urls: this.files // 需要预览的图片http链接列表
      });
    },
    deleteImage(index) {
      this.files.splice(index, 1);
      //连接后台接口
    }
  }
};
</script>
<style>
.image-list {
  float: left;
  height: 90px;
}
.image-delete {
  z-index: 100;
  position: relative;
  margin-top: -78px;
  background: red;
  opacity: 0.5;
  color: #fff;
  text-align: right;
}
</style>