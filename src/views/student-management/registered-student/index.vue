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
          <el-col :span="4">
            <el-form-item label="姓名：">
              <el-input v-model="form.name"></el-input>
            </el-form-item>
          </el-col>
          <el-col :span="4">
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

          <el-col :span="4">
            <el-form-item label="会员等级：">
              <el-select v-model="form.name" placeholder="请选择会员等级">
                <el-option
                  v-for="item in memberLevelArr"
                  :key="item.value"
                  :label="item.key"
                  :value="item.value"
                ></el-option>
              </el-select>
            </el-form-item>
          </el-col>

          <el-col :span="4">
            <el-form-item label="课程顾问：">
              <el-select
                v-model="form.courseConsultant"
                placeholder="请选择课程顾问"
              >
                <el-option
                  v-for="item in courseConsultantArr"
                  :key="item.value"
                  :label="item.key"
                  :value="item.value"
                ></el-option>
              </el-select>
            </el-form-item>
          </el-col>

          <el-col :span="4">
            <el-form-item label="私人管家：">
              <el-select
                v-model="form.privateButler"
                placeholder="请选择私人管家"
              >
                <el-option
                  v-for="item in privateButlerArr"
                  :key="item.value"
                  :label="item.key"
                  :value="item.value"
                ></el-option>
              </el-select>
            </el-form-item>
          </el-col>

          <el-col :span="4">
            <el-form-item label="中教：">
              <el-select
                v-model="form.chineseEducation"
                placeholder="请选择中教"
              >
                <el-option
                  v-for="item in chineseEducationArr"
                  :key="item.value"
                  :label="item.key"
                  :value="item.value"
                ></el-option>
              </el-select>
            </el-form-item>
          </el-col>
        </el-row>

        <el-row>
          <el-col :span="4">
            <el-form-item label="手机号：">
              <el-input
                placeholder="请输入手机号"
                v-model="form.phone"
              ></el-input>
            </el-form-item>
          </el-col>
          <el-col :span="4">
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

          <el-col :span="4">
            <el-form-item label="会员年龄：">
              <el-select v-model="form.memberAge" placeholder="请选择活动区域">
                <el-option label="区域一" value="shanghai"></el-option>
                <el-option label="区域二" value="beijing"></el-option>
              </el-select>
            </el-form-item>
          </el-col>

          <el-col :span="6">
            <el-form-item label="注册日期：">
              <el-date-picker
                v-model="form.registerDate"
                type="date"
                placeholder="选择日期"
              >
              </el-date-picker>
            </el-form-item>
          </el-col>

          <el-col :span="4">
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
          <el-table-column prop="date" label="ID"> </el-table-column>
          <el-table-column prop="name" label="中文姓名" width="100">
          </el-table-column>

          <el-table-column prop="address" label="英文姓名"> </el-table-column>
          <el-table-column prop="address" label="会员年龄"> </el-table-column>
          <el-table-column prop="address" label="手机号"> </el-table-column>
          <el-table-column prop="address" label="注册时间"> </el-table-column>
          <el-table-column prop="address" label="渠道"> </el-table-column>
          <el-table-column prop="address" label="来源"> </el-table-column>
          <el-table-column prop="address" label="课程顾问"> </el-table-column>
          <el-table-column prop="address" label="私人管家"> </el-table-column>
          <el-table-column prop="address" label="中教"> </el-table-column>

          <el-table-column prop="address" label="会员等级"> </el-table-column>
          <el-table-column prop="address" label="会员状态"> </el-table-column>

          <el-table-column fixed="right" label="操作" width="220">
            <template slot-scope="scope">
              <el-button
                @click="
                  () => {
                    handleClick(scope.row, 1);
                  }
                "
                type="text"
                size="small"
                >档案</el-button
              >
              <el-button
                @click="
                  () => {
                    handleClick(scope.row, 2);
                  }
                "
                type="text"
                size="small"
                >修改</el-button
              >
              <el-button
                @click="
                  () => {
                    handleClick(scope.row, 3);
                  }
                "
                type="text"
                size="small"
                >排课</el-button
              >
              <el-button
                @click="
                  () => {
                    handleClick(scope.row, 4);
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
import { list } from "@/api/member";
import AddStudentsDialog from "./add-dialog/index.vue";

export default {
  components: {
    AddStudentsDialog: AddStudentsDialog,
  },
  data() {
    return {
      dialogVisible: false,
      form: {
        name: "", //姓名
        channel: "", //渠道：
        memberLevel: "", // 会员等级：
        courseConsultant: "", // 课程顾问：
        privateButler: "", //私人管家
        chineseEducation: "", //中教：
        phone: "", //手机号：
        memberStatus: "", //会员状态：
        memberAge: "", //会员年龄：
        registerDate: "", //  注册日期：
        courseType: "", // 课程类型：
      },
      channelArr: [{ key: "官网", value: "1" }],
      memberLevelArr: [{ key: "注册会员", value: "2" }],
      courseConsultantArr: [{ key: "张三", value: "3" }],
      privateButlerArr: [{ key: "李四", value: "4" }],
      memberStatusArr: [{ key: "新注册", value: "5" }],
      memberAgeArr: [{ key: "6", value: "6" }],
      chineseEducationArr: [{ key: "6", value: "6" }],
      courseTypeArr: [{ key: "定制体验课", value: "6" }],
      tableData: [
        {
          date: "2016-05-02",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄",
        },
        {
          date: "2016-05-04",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1517 弄",
        },
        {
          date: "2016-05-01",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1519 弄",
        },
        {
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1516 弄",
        },
        {
          date: "2016-05-01",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1519 弄",
        },
        {
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1516 弄",
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
    // this.getList();
  },

  methods: {
    getList() {
      list(this.paging).then((resp) => {
        console.log(resp);
        this.total = resp.data.total;
        this.tableData = resp.data.list;
      });
    },
    search() {
      this.paging.currentPage = 1;
      this.getList();
    },
    handleSizeChange(val) {
      this.paging.pageSize = val;
      this.getList();
      console.log(`每页 ${val} 条`);
    },
    handleCurrentChange(val) {
      this.paging.currentPage = val;
      this.getList();

      console.log(`当前页: ${val}`);
    },
    handleClick(row, num) {
      console.log(row, num);
      //1档案 2修改 3排课 4添加订单
      if (num === 1) {
        this.$router.push({
          path: "/register-student-profile",
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
}
</style>
