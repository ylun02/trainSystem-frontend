<template>
  <div>
    <!-- 套题难度、 -->
    <el-row>
      <el-col :span="18" :offset="3">
        <h2 style="text-align: center">制作套题</h2>
        <el-form
          :model="testInfoForm"
          ref="testInfoForm"
          label-width="auto"
          style="margin-left: 50px"
        >
          <el-form-item
            label="请选择套题难度"
            prop="setLevel"
            :rules="[
              { required: true, message: '请选择套题难度', trigger: 'blur' },
            ]"
          >
            <el-radio-group v-model="testInfoForm.setLevel">
              <el-radio v-model="setLevel" label="1" border>简单</el-radio>
              <el-radio v-model="setLevel" label="2" border>普通</el-radio>

              <el-radio v-model="setLevel" label="3" border>困难</el-radio>
            </el-radio-group>
          </el-form-item>
          <el-form-item
            prop="threshold"
            label="请选择及格线（需要通过的试卷数量）"
            :rules="[
              { required: true, message: '请选择及格线', trigger: 'blur' },
            ]"
          >
            <el-input-number
              v-model="testInfoForm.threshold"
              :min="3"
              :max="10"
            ></el-input-number>
          </el-form-item>
          <el-form-item>
            <el-button type="primary" @click="createSet"> 创建 </el-button>
          </el-form-item>
        </el-form>
      </el-col>

    </el-row>
  </div>
</template>
<script>
import request from "@/api/request";

export default {
  data() {
    return {
      testInfoForm: {
        setLevel: "",
        threshold: 0,
      },
    };
  },

  methods: {
    createSet() {
      this.$refs.testInfoForm.validate((valid) => {
        if (valid) {
          //创建套题
          request({
            url: "/createSet",
            method: "post",
            data: {
              setLevel: this.testInfoForm.setLevel,
              threshold: this.testInfoForm.threshold,
              teacherId: sessionStorage.getItem("token"),
            },
          }).then((res) => {
            console.log(res);
            this.$message({
              type: "success",
              message: "创建套题成功！",
            });
            this.$router.push({
              name: "CreateTest",
            });
          });
        } else {
          console.log("error submit");
        }
      });
    },
  },
};
</script>

<style scoped>
.el-col {
  background-color: #fff;
  padding: 10px 30px;
  border-radius: 4px;
  margin-top: 20px;
}
.el-button {
  width: 250px;
}
</style>
