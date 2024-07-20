<template>
  <div class="register-student-profile">
    <div>
      <div class="topTitle">基本信息</div>

      <div class="content">
        <div class="content_left">
          <div>
            <div class="item">
              <div>ID</div>
              <div>202401</div>
            </div>

            <div class="item">
              <div>注册时间</div>
              <div>2024-04-18 15：03</div>
            </div>

            <div class="item">
              <div>微信号</div>
              <div>微信号</div>
            </div>
          </div>
          <div>
            <div class="item">
              <div>中文名</div>
              <div>张武</div>
            </div>

            <div class="item">
              <div>性别</div>
              <div>男</div>
            </div>

            <div class="item">
              <div>会员等级</div>
              <div>已购买体验课</div>
            </div>
          </div>

          <div>
            <div class="item">
              <div>英文名</div>
              <div>Jack</div>
            </div>

            <div class="item">
              <div>生日</div>
              <div>2016-08-05</div>
            </div>

            <div class="item">
              <div>课程顾问</div>
              <div>Bruce</div>
            </div>
          </div>

          <div>
            <div class="item">
              <div>年龄</div>
              <div>8</div>
            </div>

            <div class="item">
              <div>年龄</div>
              <div>8</div>
            </div>

            <div class="item">
              <div>私人管家</div>
              <div>Ella</div>
            </div>
          </div>

          <div>
            <div class="item">
              <div>手机号</div>
              <div>12345678910</div>
            </div>

            <div class="item">
              <div>Classin账号</div>
              <div>12345678910</div>
            </div>

            <div class="item">
              <div>来源</div>
              <div>XX论坛帖子</div>
            </div>
          </div>

          <div>
            <div class="item">
              <div>监护人</div>
              <div>张阿萨</div>
            </div>

            <div class="item">
              <div>渠道</div>
              <div>移动官网</div>
            </div>

            <div class="item">
              <div>使用教材</div>
              <div>牛津</div>
            </div>
          </div>

          <div>
            <div class="item">
              <div>紧急联络人</div>
              <div>刘美</div>
            </div>

            <div class="item">
              <div>学校</div>
              <div>杭州外国语</div>
            </div>

            <div class="item">
              <div>年级</div>
              <div>一年级</div>
            </div>
          </div>

          <div>
            <div class="item">
              <div>号码</div>
              <div>12345678910</div>
            </div>

            <div class="item">
              <div>通信地址</div>
              <div>上海市静安区</div>
            </div>

            <div class="item">
              <div>备注</div>
              <div>12345678910</div>
            </div>
          </div>
        </div>

        <!-- 图片 -->
        <div class="content_right">11</div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  components: {},
  data() {
    return {};
  },
  methods: {},
  created() {},
};
</script>
<style lang="scss" scoped>
.register-student-profile {
  padding: 20px;
  .topTitle {
    height: 40px;
    padding-left: 20px;
    display: flex;
    align-items: center;
    background-color: #377f7f;
    color: #fff;
    font-size: 14px;
  }

  .content {
    display: flex;
    .content_left {
      display: flex;
      flex-direction: column;
      justify-content: center;
      // flex: 1;

      & > div {
        display: flex;
        margin-top: 20px;
        & > .item {
          display: flex;
          margin-right: 100px;

          & > div:nth-child(1) {
            display: flex;
            justify-content: flex-end;
            margin-right: 20px;
          }

          & > div:nth-child(1) {
            width: 100px;
            // background-color: pink;
          }
        }

        & > .item:nth-of-type(1) {
          // background-color: yellow;
          width: 200px;
        }
        & > .item:nth-of-type(2) {
          // background-color: red;
          width: 300px;
        }
      }
    }

    .content_right {
      margin-left: 20px;
    }
  }
}
</style>
