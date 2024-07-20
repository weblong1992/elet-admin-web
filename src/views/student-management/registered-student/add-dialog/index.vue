<template>
  <el-dialog
    @close="closeDia"
    :title="title"
    :visible.sync="dialogVisible"
    width="70%"
  >
    <div class="con">
      <el-form
        :inline="true"
        :model="formInline"
        label-width="100px"
        size="mini"
        class="demo-form-inline"
      >
        <div class="tip">
          <div class="linebar"></div>

          <div>基本信息</div>
        </div>

        <div class="info">
          <div class="info_left">
            <div class="item">
              <el-form-item label="姓名">
                <el-input
                  v-model="formInline.user"
                  placeholder="审批人"
                ></el-input>
              </el-form-item>
              <el-form-item label="性别">
                <el-select v-model="formInline.region" placeholder="活动区域">
                  <el-option label="区域一" value="shanghai"></el-option>
                  <el-option label="区域二" value="beijing"></el-option>
                </el-select>
              </el-form-item>
            </div>

            <div class="item">
              <el-form-item label="英文名">
                <el-input
                  v-model="formInline.user"
                  placeholder="审批人"
                ></el-input>
              </el-form-item>
              <el-form-item label="出生年月">
                <el-select v-model="formInline.region" placeholder="活动区域">
                  <el-option label="区域一" value="shanghai"></el-option>
                  <el-option label="区域二" value="beijing"></el-option>
                </el-select>
              </el-form-item>
            </div>

            <div class="item">
              <el-form-item label="监护人">
                <el-input
                  v-model="formInline.user"
                  placeholder="手机号"
                ></el-input>
              </el-form-item>
              <el-form-item label="出生年月">
                <el-select v-model="formInline.region" placeholder="活动区域">
                  <el-option label="区域一" value="shanghai"></el-option>
                  <el-option label="区域二" value="beijing"></el-option>
                </el-select>
              </el-form-item>
            </div>

            <div class="item">
              <el-form-item label="课程顾问">
                <el-input
                  v-model="formInline.user"
                  placeholder="手机号"
                ></el-input>
              </el-form-item>
              <el-form-item label="Classin">
                <el-select v-model="formInline.region" placeholder="活动区域">
                  <el-option label="区域一" value="shanghai"></el-option>
                  <el-option label="区域二" value="beijing"></el-option>
                </el-select>
              </el-form-item>
            </div>

            <div class="item">
              <el-form-item label="渠道">
                <el-input
                  v-model="formInline.user"
                  placeholder="手机号"
                ></el-input>
              </el-form-item>
              <el-form-item label="来源">
                <el-select v-model="formInline.region" placeholder="活动区域">
                  <el-option label="区域一" value="shanghai"></el-option>
                  <el-option label="区域二" value="beijing"></el-option>
                </el-select>
              </el-form-item>
            </div>

            <div class="item">
              <el-form-item label="紧急联络人">
                <el-input
                  v-model="formInline.user"
                  placeholder="手机号"
                ></el-input>
              </el-form-item>
              <el-form-item label="联系方式">
                <el-select v-model="formInline.region" placeholder="活动区域">
                  <el-option label="区域一" value="shanghai"></el-option>
                  <el-option label="区域二" value="beijing"></el-option>
                </el-select>
              </el-form-item>
            </div>

            <div class="item">
              <el-form-item label="会员状态">
                <el-select v-model="formInline.region" placeholder="活动区域">
                  <el-option label="注册会员" value="1"></el-option>
                  <el-option label="已购体验课" value="2"></el-option>
                  <el-option label="已购常规课" value="2"></el-option>
                </el-select>
              </el-form-item>
              <el-form-item label="私人管家">
                <el-select v-model="formInline.region" placeholder="活动区域">
                  <el-option label="区域一" value="shanghai"></el-option>
                  <el-option label="区域二" value="beijing"></el-option>
                </el-select>
              </el-form-item>
            </div>

            <div class="item">
              <el-form-item label="微信号">
                <el-select v-model="formInline.region" placeholder="活动区域">
                  <el-option label="区域一" value="shanghai"></el-option>
                  <el-option label="区域二" value="beijing"></el-option>
                </el-select>
              </el-form-item>
            </div>

            <div class="item">
              <el-form-item label="通讯地址">
                <el-select v-model="formInline.region" placeholder="活动区域">
                  <el-option label="区域一" value="shanghai"></el-option>
                  <el-option label="区域二" value="beijing"></el-option>
                </el-select>
              </el-form-item>
            </div>
          </div>

          <div class="info_right">上传</div>
        </div>

        <div class="tip">
          <div class="linebar"></div>

          <div>学习信息</div>
        </div>

        <div class="study_info">
          <div>
            <el-form-item label="学校">
              <el-input
                v-model="formInline.user"
                placeholder="请输入学校"
              ></el-input>
            </el-form-item>
            <el-form-item label="年级">
              <el-select v-model="formInline.region" placeholder="活动区域">
                <el-option label="一年级" value="1"></el-option>
                <el-option label="二年级" value="2"></el-option>
                <el-option label="三年级" value="3"></el-option>
              </el-select>
            </el-form-item>

            <el-form-item label="教材">
              <el-select v-model="formInline.region" placeholder="请选择教材">
                <el-option label="人教" value="1"></el-option>
                <el-option label="牛津" value="2"></el-option>
                <el-option label="剑桥" value="3"></el-option>
                <el-option label="其他" value="4"></el-option>
              </el-select>
            </el-form-item>
          </div>
          <div>
            <el-form-item label="备注">
              <el-input
                placeholder="请输入备注"
                type="textarea"
                v-model="formInline.remark"
              ></el-input>
            </el-form-item>
          </div>
        </div>
      </el-form>
    </div>

    <span slot="footer" class="dialog-footer">
      <el-button @click="closeDia">取 消</el-button>
      <el-button type="primary">确 定</el-button>
    </span>
  </el-dialog>
</template>
<script>
export default {
  props: {
    show: {
      type: Boolean,
      default: false,
    },
    title: {
      type: String,
      default: "",
    },
  },
  computed: {
    dialogVisible: {
      get() {
        return this.show;
      },
      set(val) {
        this.$emit("update:show", val);
      },
    },
  },
  data() {
    return {
      formInline: {
        user: "",
        region: "",
      },
    };
  },
  methods: {
    onSubmit() {
      console.log("submit!");
    },
    closeDia() {
      this.dialogVisible = false;
      this.$emit("cancelFn");
    },
  },
};
</script>
<style lang="scss" scoped>
.con {
  //   display: flex;
  .tip {
    // margin-bottom: 20px;
    display: flex;
    align-items: center;
    & > div:nth-child(1) {
      width: 3px;
      height: 25px;
      margin-right: 5px;
      background-color: #3952fe;
    }
  }
  .info {
    display: flex;
  }
}
</style>
