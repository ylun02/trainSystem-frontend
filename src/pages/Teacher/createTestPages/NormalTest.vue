<template>
  <div>
    <!-- 需要传进去的参数 1. 试卷名称   2. 套题id   3. 试卷编号 4. 限定时间-->
    <el-row>
      <el-col :span="14" :offset="5" style="background-color: #ffffff; padding: 20px; border-radius: 4px">
        <h2 style="text-align: center; margin-bottom: 40px">
          制作套题中的第 {{ questionInfoForm.normalTestNumber }} 张试卷
        </h2>
        <el-form
          :model="questionInfoForm"
          ref="questionInfoForm"
          label-width="auto"
          hide-required-asterisk
        >
          <el-form-item
            label="请输入试卷名称"
            prop="normalTestName"
            :rules="[
              { required: true, message: '请输入试卷名称', trigger: 'blur' },
            ]"
          >
            <el-input
              placeholder="请输入内容"
              v-model="questionInfoForm.normalTestName"
            >
            </el-input>
          </el-form-item>
          <el-form-item label="套题Id" prop="setId">
            <el-input v-model="questionInfoForm.setId" disabled> </el-input>
          </el-form-item>
          <el-form-item label="试卷序号">
            <el-input v-model="questionInfoForm.normalTestNumber" disabled>
            </el-input>
          </el-form-item>
          <el-form-item label="限定时间（30~180分钟）">
            <el-input-number
              v-model="questionInfoForm.limitTime"
              :min="30"
              :max="180"
              placeholder="限定时间"
            ></el-input-number>
          </el-form-item>
          <el-form-item>
            <el-button type="primary" @click="createNormalTest">
              开始制作
            </el-button>
          </el-form-item>
        </el-form>
        <!-- <el-input placeholder="请输入内容"
                  v-model="normalTestName">
          <template slot="prepend">试卷名称</template>
        </el-input> -->
      </el-col>

      <!-- <el-col :span="24">

        <el-input v-model="setId"
                  disabled>
          <template slot="prepend">套题Id</template>
        </el-input>
      </el-col>

      <el-col :span="24">

        <el-input v-model="normalTestNumber"
                  disabled>
          <template slot="prepend">试卷序号</template>
        </el-input>
      </el-col>

      <el-col :span="24">
        <template>
          
          <el-input-number v-model="limitTime"
                           :min="30"
                           :max="180"
                           placeholder="限定时间"></el-input-number>
        </template>
      </el-col> -->

      <!-- <el-col :span="24">
        <el-button @click="createNormalTest">
          创建试卷
        </el-button>
      </el-col> -->
    </el-row>
  </div>
</template>

<script>
export default {
  name: "NormalTest",
  data() {
    return {
      questionInfoForm: {
        normalTestName: "",
        setId: "",
        limitTime: 30,
        normalTestNumber: "",
      },
    };
  },

  methods: {
    createNormalTest() {
      console.log("创建试卷");
      this.$refs.questionInfoForm.validate((valid) => {
        if (valid) {
          this.$router.push({
            name: "SelectQuestion",
            params: {
              testName: this.questionInfoForm.normalTestName,
              questionNumber: 10,
              testType: 1,
              limitTime: this.questionInfoForm.limitTime,
              normalTestNumber: this.$route.params.normalTestNumber,
              setId: this.questionInfoForm.setId,
            },
          });
        } else {
          console.log("error submit");
        }
      });
      // this.$router.push({
      //   name: 'SelectQuestion',
      //   params: {
      //     testName: this.normalTestName,
      //     questionNumber: 10,
      //     testType: 1,
      //     limitTime: this.limitTime,
      //     normalTestNumber: this.$route.params.normalTestNumber,
      //     setId: this.setId,
      //   },
      // })
    },
  },

  mounted() {
    this.questionInfoForm.normalTestNumber =
      this.$route.params.normalTestNumber + 1;
    this.questionInfoForm.setId = this.$route.params.setId;
  },
};
</script>

<style scoped>
.el-col {
  margin-top: 20px;
}

.el-button {
  font-size: 15px;
  width: 350px;
}
/* 
* {
  border: 1px red solid;
} */
</style>
