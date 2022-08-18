<template>
  <div>
    <el-row :gutter="40">
      <el-col :span="15" :offset="4" style="background-color: #ffffff; margin-top: 20px; padding: 20px; border-radius: 4px">
        <h2 style="text-align: center; margin-bottom: 40px">制作专项试卷</h2>
        <el-form
          :model="questionInfoForm"
          ref="questionInfoForm"
          label-width="auto"
          :rules="rules"
        >
          <el-form-item label="请输入试卷名称" prop="specialTestName">
            <el-input
              placeholder="请输入内容"
              v-model="questionInfoForm.specialTestName"
            >
            </el-input>
          </el-form-item>
          <el-form-item label="请选择题目数量" prop="questionNumber">
            <el-input-number
              v-model="questionInfoForm.questionNumber"
              :min="4"
              :max="10"
              placeholder="题目数量"
            ></el-input-number>
          </el-form-item>
          <el-form-item label="请选择及格线（需要做对的题目数量）" prop="threshold">
            <el-input-number
              v-model="questionInfoForm.threshold"
              :min="0"
              :max="questionInfoForm.questionNumber"
              placeholder="及格线"
            ></el-input-number>
          </el-form-item>
          <el-form-item label="请选择题目难度" prop="specialLevel">
            <el-rate
              v-model="questionInfoForm.specialLevel"
              show-text
              :texts="texts"
              :max="3"
            >
            </el-rate>
          </el-form-item>
          <el-form-item>
            <el-button
              type="primary"
              style="width: 200px"
              @click="submitCreateSpecialTest"
              >开始制作</el-button
            >
          </el-form-item>
        </el-form>
        <!-- <el-input placeholder="请输入内容"
                  v-model="specialTestName">
          <template slot="prepend">试卷名称</template>
        </el-input> -->
      </el-col>

      <!-- <el-col :span="4">
        <template>
          <el-input-number v-model="questionNumber"
                           :min="4"
                           :max="10"
                           placeholder="题目数量"></el-input-number>
        </template>
      </el-col>

      <el-col :span="4">
        <template>
          <el-input-number v-model="threshold"
                           :min="0"
                           :max="questionNumber"
                           placeholder="及格线"></el-input-number>
        </template>
      </el-col> -->

      <!-- <el-col :span="3">
        <el-rate v-model="specialLevel"
                 show-text
                 :texts="texts"
                 :max="3">
        </el-rate>
      </el-col> -->
    </el-row>

    <!-- <el-row :gutter="30">
      <el-button type="success"
                 plain
                 style="margin-left: 16px;"
                 @click="submitCreateSpecialTest">创建试卷</el-button>
    </el-row> -->
  </div>
</template>
<script>
export default {
  data() {
    var validaterate = (rule, value, callback) => {
      if (value === 0) {
        callback(new Error("请选择题目难度"));
      }
      callback();
    };
    var validatethreshold = (rule, value, callback) => {
      if (value === 0) {
        callback(new Error("请选择及格线"));
      }
      callback();
    };
    return {
      specialTestName: "",
      threshold: null,
      texts: ["简单", "普通", "困难"],
      specialLevel: null,
      drawer: false,
      questionNumber: null,
      questionInfoForm: {
        specialTestName: "",
        questionNumber: 4,
        threshold: 0,
        specialLevel: 0,
      },
      rules: {
        specialTestName: [
          { required: true, message: "请输入试卷名称", trigger: "blur" },
        ],
        threshold: [
          { validator: validatethreshold, trigger: "blur" },
          { required: true, trigger: "blur" },
        ],
        specialLevel: [
          { validator: validaterate, trigger: "blur" },
          { required: true, trigger: "blur" },
        ],
        questionNumber: [{ required: true, trigger: "blur" },]
      },
    };
  },
  methods: {
    submitCreateSpecialTest() {
      this.$refs.questionInfoForm.validate((valid) => {
        if (valid) {
          this.$router.push({
            name: "SelectQuestion",
            params: {
              //需要发送过去的信息：testName，threshold，specialLevel, questionNumber
              specialLevel: this.questionInfoForm.specialLevel,
              questionNumber: this.questionInfoForm.questionNumber,
              testName: this.questionInfoForm.specialTestName,
              specialThreshold: this.questionInfoForm.threshold,
              testType: 0,
            },
          });
        } else {
          console.log("error submit");
        }
      });
      // this.$router.push({
      //   name: "SelectQuestion",
      //   params: {
      //     //需要发送过去的信息：testName，threshold，specialLevel, questionNumber
      //     specialLevel: this.specialLevel,
      //     questionNumber: this.questionNumber,
      //     testName: this.specialTestName,
      //     specialThreshold: this.threshold,
      //     testType: 0,
      //   },
      // });
    },
  },
};
</script>

<style scoped>
.el-rate {
  font-size: 40px;
  margin: 0;
  height: 0px;
}

.el-row {
  margin-bottom: 30px;
}

.el-button {
  width: 820px;
}

.el-radio-button {
  margin-bottom: 20px;
  margin-left: 30px;
  margin-top: 10px;
}
</style>
