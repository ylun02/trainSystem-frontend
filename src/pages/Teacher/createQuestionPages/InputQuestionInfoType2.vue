<template>
  <div>
    <el-row>
      <el-col :span="20">
        <el-form ref="questionInfoForm" :model="questionInfoForm">
          <el-form-item prop="questionTitle" :rules="[{required: true, message: '请输入题目', trigger: 'blur'}]">
            <el-input
              type="textarea"
              :rows="8"
              placeholder="请输入题目"
              v-model="questionInfoForm.questionTitle"
              style="font-size: 20px"
            >
            </el-input>
          </el-form-item>
          <el-form-item label="io实例个数">
            <el-input-number
              v-model="questionInfoForm.ioNumber"
              :min="0"
              placeholder="io实例个数"
            ></el-input-number>
          </el-form-item>
        </el-form>
        <!-- <el-input type="textarea"
                  :rows="8"
                  placeholder="请输入题目"
                  v-model="questionTitle"
                  style="font-size:20px">
        </el-input> -->
      </el-col>

      <!-- <el-col :span="24"
              style="margin-top:10px">
        <el-input-number v-model="ioNumber"
                         label="io实例个数"
                         :min="0"
                         placeholder='io实例个数'></el-input-number>
      </el-col> -->

      <el-col :span="24">
        <el-collapse>
          <el-collapse-item
            :title="`I/O实例:${i}`"
            :name="i"
            v-for="i in ioNumber"
            :key="i"
            style="margin-top: 15px"
          >
            <div>
              <el-input
                placeholder="请输入内容"
                v-model="inputList[i - 1]"
                :id="i"
              >
                <template slot="prepend">Input</template>
              </el-input>
            </div>

            <div style="margin-top: 15px">
              <el-input
                placeholder="请输入内容"
                v-model="outputList[i - 1]"
                :id="i"
              >
                <template slot="prepend">Output</template>
              </el-input>
            </div>
          </el-collapse-item>
        </el-collapse>
      </el-col>
    </el-row>

    <el-row>
      <el-divider>请展开下方折叠面板填入题目答案</el-divider>
      <el-col :span="24">
        <el-collapse>
          <el-collapse-item title="C语言答案" style="margin-top: 15px">
            <div>
              <el-input
                type="textarea"
                :rows="8"
                placeholder="C语言答案"
                v-model="answerList[0]"
                style="font-size: 20px"
              >
              </el-input>
            </div>
          </el-collapse-item>

          <el-collapse-item title="Java语言答案" style="margin-top: 15px">
            <div>
              <el-input
                type="textarea"
                :rows="8"
                placeholder="Java语言答案"
                v-model="answerList[1]"
                style="font-size: 20px"
              >
              </el-input>
            </div>
          </el-collapse-item>

          <el-collapse-item title="python语言答案" style="margin-top: 15px">
            <div>
              <el-input
                type="textarea"
                :rows="8"
                placeholder="python语言答案"
                v-model="answerList[2]"
                style="font-size: 20px"
              >
              </el-input>
            </div>
          </el-collapse-item>
        </el-collapse>
      </el-col>

      <el-col :span="24">
        <el-button
          type="success"
          plain
          style="
            margin-left: 450px;
            margin-top: 50px;
            width: 200px;
            height: 50px;
            font-size: 20px;
          "
          @click="uploadQuestion"
          >完成创建</el-button
        >
      </el-col>
    </el-row>
  </div>
</template>
<script>
import request from "@/api/request";

export default {
  name: "InputQuestionInfoType2",
  data() {
    return {
      questionTitle: "",
      ioNumber: 0,
      inputList: [],
      outputList: [],
      answerList: [],
      questionInfoForm: {
        questionTitle: "",
        ioNumber: 0
      },
    };
  },

  methods: {
    uploadQuestion() {
      this.$refs.questionInfoForm.validate((valid) => {
        if (valid) {
          request({
            url: "/uploadQuestion",
            method: "post",
            data: {
              questionTitle: this.questionInfoForm.questionTitle,
              questionAnswerList: this.answerList,
              questionType: this.$route.params.questionType,
              questionLevel: this.$route.params.questionLevel,
              kowledgePoint: this.$route.params.selectKnowledgePoint,
              questionForm: this.$route.params.questionForm,
              ioNumber: this.ioNumber,
              inputList: this.inputList,
              outputList: this.outputList,
              teacherId: sessionStorage.getItem("token"),
            },
          });

          this.$message({
            type: "success",
            message: "上传成功！",
          });

          this.$router.push({
            name: "UploadQuestion",
          });
        } else {
          console.log('error submit');
        }
      });
      // request({
      //   url: '/uploadQuestion',
      //   method: 'post',
      //   data: {
      //     questionTitle: this.questionTitle,
      //     questionAnswerList: this.answerList,
      //     questionType: this.$route.params.questionType,
      //     questionLevel: this.$route.params.questionLevel,
      //     kowledgePoint: this.$route.params.selectKnowledgePoint,
      //     questionForm: this.$route.params.questionForm,
      //     ioNumber: this.ioNumber,
      //     inputList: this.inputList,
      //     outputList: this.outputList,
      //     teacherId: sessionStorage.getItem('token'),
      //   },
      // })

      // this.$message({
      //   type: 'success',
      //   message: '上传成功！',
      // })

      // this.$router.push({
      //   name: 'UploadQuestion',
      // })
    },
  },

  mounted() {
    console.log(this.$route.params.questionType);
    console.log(this.$route.params.questionLevel);
    console.log(this.$route.params.selectKnowledgePoint);
    console.log(this.$route.params.questionForm);
  },
};
</script>
<style></style>
