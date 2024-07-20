<template>
  <div>
    <el-form
      ref="passwordForm"
      label-position="top"
      :model="password"
      :rules="rules"
      size="small"
    >
      <el-form-item label="原密码：" prop="oldPassword">
        <el-input v-model="password.oldPassword" show-password />
      </el-form-item>
      <el-form-item label="新密码：" prop="newPassword">
        <el-input v-model="password.newPassword" show-password />
      </el-form-item>
      <el-form-item label="确认新密码：" prop="confirmNewPassword">
        <el-input v-model="password.confirmNewPassword" show-password />
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="updatePassword">更 改</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
import { updatePassword } from "@/api/user";

export default {
  name: "RPassword",
  data() {
    // 校验新密码是否一致
    let checkpass = (rule, value, callback) => {
      if (value == this.password.newPassword) {
        callback();
      } else {
        callback(new Error("密码不一致"));
      }
    };

    return {
      password: {
        oldPassword: "",
        newPassword: "",
        confirmNewPassword: "",
      },
      rules: {
        oldPassword: [
          { required: true, message: "请输入原密码", trigger: "blur" },
          // { validator: validatePass, message: "原密码不正确", trigger: "blur" },
        ],
        newPassword: [
          { required: true, message: "请输入新密码", trigger: "blur" },
        ],
        confirmNewPassword: [
          { required: true, message: "不能为空", trigger: "blur" },
          { validator: checkpass, trigger: "blur" },
        ],
      },
    };
  },
  methods: {
    updatePassword() {
      this.$refs["passwordForm"].validate((valid) => {
        if (valid) {
          if (this.password.newPassword == this.password.oldPassword) {
            this.$message({
              message: "原密码要与新密码不一样!",
              type: "error",
            });
          } else {
            updatePassword(this.password).then((resp) => {
              if (resp.status === 200) {
                this.$message.success(resp.message);
                this.$refs["passwordForm"].resetFields();
              }
            });
          }
        }
      });
    },
  },
};
</script>

<style scoped></style>
