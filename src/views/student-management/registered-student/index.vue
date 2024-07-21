<template>
  <div class="register-student">
    <div class="search_box">
      <el-form
        ref="form"
        label-position="right"
        :model="form"
        size="mini"
        label-width="100px"
      >
        <el-row>
          <el-col :span="6">
            <el-form-item label="姓名：">
              <el-input v-model="form.nickname"></el-input>
            </el-form-item>
          </el-col>
          <el-col :span="6">
            <el-form-item label="渠道：">
              <el-select v-model="form.channel" placeholder="请选择渠道">
                <el-option
                  v-for="item in channelArr"
                  :key="item.value"
                  :label="item.key"
                  :value="item.value"
                ></el-option>
              </el-select>
            </el-form-item>
          </el-col>

          <el-col :span="6">
            <el-form-item label="会员年龄：">
              <el-select v-model="form.memberAge" placeholder="请选择活动区域">
                <el-option label="区域一" value="shanghai"></el-option>
                <el-option label="区域二" value="beijing"></el-option>
              </el-select>
            </el-form-item>
          </el-col>

          <el-col :span="6">
            <el-form-item label="会员状态：">
              <el-select
                v-model="form.memberStatus"
                placeholder="请选择会员状态"
              >
                <el-option
                  v-for="item in memberStatusArr"
                  :key="item.value"
                  :label="item.key"
                  :value="item.value"
                ></el-option>

                <el-option label="区域一" value="shanghai"></el-option>
                <el-option label="区域二" value="beijing"></el-option>
              </el-select>
            </el-form-item>
          </el-col>
        </el-row>

        <el-row>
          <el-col :span="6">
            <el-form-item label="手机号：">
              <el-input
                placeholder="请输入手机号"
                v-model="form.mobile"
              ></el-input>
            </el-form-item>
          </el-col>
          <el-col :span="8">
            <el-form-item label="注册日期：">
              <div class="date_box">
                <el-date-picker
                  style="width: 80x"
                  v-model="form.beginCreate"
                  type="date"
                  placeholder="开始日期"
                >
                </el-date-picker>

                <span class="tit"> 至</span>
                <el-date-picker
                  style="width: 80x"
                  v-model="form.endCreate"
                  type="date"
                  placeholder="结束日期"
                >
                </el-date-picker>
              </div>
            </el-form-item>
          </el-col>

          <el-col :span="8">
            <el-form-item label="课程类型：">
              <el-select v-model="form.courseType" placeholder="请选择活动区域">
                <el-option label="区域一" value="shanghai"></el-option>
                <el-option label="区域二" value="beijing"></el-option>
              </el-select>
            </el-form-item>
          </el-col>
        </el-row>

        <el-row>
          <el-form-item>
            <el-button type="primary" @click="search">查询</el-button>
            <el-button @click="add">新增</el-button>
          </el-form-item>
        </el-row>
      </el-form>
    </div>

    <div class="box">
      <div class="table_box">
        <el-table :data="tableData" stripe style="width: 100%" max-height="500">
          <el-table-column prop="id" label="ID"> </el-table-column>
          <el-table-column prop="nickname" label="姓名" width="100">
          </el-table-column>

          <el-table-column prop="memberAge" label="会员年龄"> </el-table-column>
          <el-table-column prop="mobile" label="手机号"> </el-table-column>
          <!-- <el-table-column prop="address" label="注册时间"> </el-table-column> -->
          <el-table-column prop="channel" label="渠道"> </el-table-column>
          <!-- <el-table-column prop="address" label="来源"> </el-table-column> -->
          <el-table-column prop="memberStatus" label="会员状态">
          </el-table-column>

          <el-table-column fixed="right" label="操作" width="220">
            <template slot-scope="scope">
              <el-button
                @click="
                  () => {
                    handleClick(scope.row, 'archives');
                  }
                "
                type="text"
                size="small"
                >档案</el-button
              >
              <el-button
                @click="
                  () => {
                    handleClick(scope.row, 'edit');
                  }
                "
                type="text"
                size="small"
                >修改</el-button
              >

              <el-button
                @click="
                  () => {
                    handleClick(scope.row, 'delete');
                  }
                "
                type="text"
                size="small"
                >删除</el-button
              >

              <el-button
                @click="
                  () => {
                    handleClick(scope.row, 'course');
                  }
                "
                type="text"
                size="small"
                >排课</el-button
              >
              <el-button
                @click="
                  () => {
                    handleClick(scope.row, 'order');
                  }
                "
                type="text"
                size="small"
                >添加订单</el-button
              >
            </template>
          </el-table-column>
        </el-table>
      </div>

      <div class="pagination">
        <el-pagination
          background
          :page-sizes="[10, 20, 30, 40, 50]"
          layout="total, sizes, prev, pager, next, jumper"
          :total="total"
          :page-size.sync="paging.pageSize"
          :current-page.sync="paging.current"
          @size-change="handleSizeChange"
          @current-change="handleCurrentChange"
        />
      </div>
    </div>

    <!-- 新增弹窗 -->
    <AddStudentsDialog
      :show.sync="dialogVisible"
      @submitFn="submitFn"
      @cancelFn="cancelFn"
    ></AddStudentsDialog>
  </div>
</template>
<script>
import { list, deleteUser } from "@/api/member";
import AddStudentsDialog from "./add-dialog/index.vue";

export default {
  components: {
    AddStudentsDialog: AddStudentsDialog,
  },
  data() {
    return {
      dialogVisible: false,
      form: {
        nickname: "", //姓名
        // channel: "", //渠道：
        mobile: "", //手机号：
        // memberStatus: "", //会员状态：
        // memberAge: "", //会员年龄：
        // courseType: "", // 课程类型：
        beginCreate: "", //开始日期
        endCreate: "", // 结束日期
      },
      channelArr: [{ key: "官网", value: "1" }],
      memberStatusArr: [{ key: "新注册", value: "5" }],
      memberAgeArr: [{ key: "6", value: "6" }],
      courseTypeArr: [{ key: "定制体验课", value: "6" }],
      tableData: [
        {
          date: "2016-05-02",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄",
        },
      ],
      paging: {
        current: 1,
        pageSize: 10,
      },
      total: 0, //总数
    };
  },
  created() {
    this.getList();
  },

  methods: {
    getList() {
      let data = {
        ...this.form,
        ...this.paging,
      };
      list(data).then((resp) => {
        console.log(resp);
        this.total = resp.data.total;
        this.tableData = resp.data.list;
      });
    },
    search() {
      this.paging.current = 1;
      this.getList();
    },
    handleSizeChange(val) {
      this.paging.pageSize = val;
      this.getList();
      console.log(`每页 ${val} 条`);
    },
    handleCurrentChange(val) {
      this.paging.current = val;
      this.getList();
      console.log(`当前页: ${val}`);
    },
    handleClick(row, str) {
      console.log(row, str);
      //1档案 2修改 3排课 4添加订单
      if (str === "archives") {
        this.$router.push({
          path: "/register-student-profile",
        });
      } else if (str == "delete") {
        this.$confirm("确定要删除该学员吗？", "提示", { type: "warning" })
          .then(() => {
            console.log(row);
            deleteUser(row.id).then((res) => {
              console.log(res);
              if (res.status === 200) {
                this.$message({
                  type: "success",
                  message: res.message,
                });

                this.getList();
              }
            });
          })
          .catch(() => {
            //选择取消后执行
            this.$notify({
              title: "已取消",
              type: "info",
            });
          });
      }
    },
    add() {
      this.dialogVisible = true;
    },
    submitFn() {},
    cancelFn() {
      this.dialogVisible = false;
    },
  },
};
</script>
<style lang="scss" scoped>
.register-student {
  padding-top: 20px;
  .box {
    padding: 30px;
  }

  .search_box {
    .date_box {
      display: flex;

      .tit {
        margin: 0 3px;
      }
    }
  }
}
</style>
