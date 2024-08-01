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
        :rules="rules"
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
              <el-form-item
                label="通讯地址"
                prop="address"
                v-model="formInline.address"
              >
                <checkAddress
                  ref="address"
                  v-model="formInline.address"
                  :form="formInline.address"
                />
              </el-form-item>
            </div>
          </div>

          <div class="info_right">
            <img :src="formInline.img" alt="" />

            <input
              @change="uploadPhoto($event)"
              type="file"
              class="kyc-passin"
            />
          </div>
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
      <el-button type="primary" @click="onSubmit">确 定</el-button>
    </span>
  </el-dialog>
</template>
<script>
import checkAddress from "@/components/checkAddress/checkAddress.vue";
export default {
  components: {
    checkAddress,
  },
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
  watch: {
    formInline: {
      // deep: true,
      handler() {
        this.formInline.address = this.$refs.address.form;
        console.log(this.formInline.address);
      },
    },
  },
  data() {
    return {
      formInline: {
        img: "", //
        user: "",
        region: "",
        address: {
          // 省
          province: "",
          // 市
          city: "",
          // 区
          district: "",
          //详细地址
          detail: "",
        },
      },
      rules: {
        address: [
          { required: true, validator: this.validatePass, trigger: "blur" },
        ],
      },
    };
  },
  methods: {
    validatePass(rule, value, callback) {
      if (
        this.formInline.address.province == "" ||
        this.formInline.address.detail == ""
      ) {
        callback(new Error("请输入完整地址"));
      }
      callback();
    },
    onSubmit() {
      console.log(this.formInline.address);

      console.log("submit!");
    },
    closeDia() {
      this.dialogVisible = false;
      this.$emit("cancelFn");
    },
    uploadPhoto(e) {
      // 利用fileReader对象获取file
      let file = e.target.files[0];
      let filesize = file.size;
      let filename = file.name;
      // 2,621,440   2M
      if (filesize > 2101440) {
        // 图片大于2MB
      }
      let reader = new FileReader();
      reader.readAsDataURL(file);
      reader.onload = (e) => {
        // 读取到的图片base64 数据编码 将此编码字符串传给后台即可
        let imgcode = e.target.result;
        this.formInline.img = imgcode;
        console.log(this.formInline.img);
      };
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

    .info_right {
      // width: 200px;
      // height: 200px;
      // display: flex;
      // justify-content: center;
      // align-items: center;
      // background-color: aqua;
    }
  }
}
</style>
