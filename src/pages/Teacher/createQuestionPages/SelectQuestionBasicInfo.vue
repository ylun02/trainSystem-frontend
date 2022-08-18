<template>
  <div>
    <el-row>
      <el-col :span="15" :offset="4" style="background-color: #ffffff; margin-top: 20px; padding: 20px; border-radius: 4px">
        <h2 style="text-align: center; margin-bottom: 20px">
          {{
            this.$route.params.questionForm == 1 ? "制作填空题" : "制作编程题"
          }}
        </h2>
        <el-form
          :model="questionInfoForm"
          ref="questionInfoForm"
          :rules="rules"
          style="margin-left: 80px"
          label-width="auto"
        >
          <el-form-item label="请选择题目类型" prop="questionType">
            <el-radio-group
              v-model="questionInfoForm.questionType"
              @change="changeRadio"
            >
              <el-radio label="1" border>语言基础</el-radio>
              <el-radio label="2" border>数据结构</el-radio>
              <el-radio label="3" border>算法</el-radio>
            </el-radio-group>
          </el-form-item>
          <el-form-item label="请选择题目难度" prop="rate">
            <el-rate
              v-model="questionInfoForm.rate"
              show-text
              :texts="texts"
              :max="3"
            >
            </el-rate>
          </el-form-item>
          <el-form-item v-if="questionInfoForm.questionType != 0" prop="point" label="请选择题目知识点">
            <el-select
              placeholder="请选择题目知识点"
              v-model="questionInfoForm.point"
            >
              <el-option
                v-for="(point, index) in knowledgePointList"
                :key="index"
                :value="point"
              >
              </el-option>
            </el-select>
          </el-form-item>
          <el-form-item>
            <el-button type="primary" @click="clickNext" style="width: 200px;">下一步</el-button>
          </el-form-item>
        </el-form>
        <!-- <div>
          <el-radio v-model="questionType" label="1" border>语言基础</el-radio>
          <el-radio v-model="questionType" label="2" border>数据结构</el-radio>
          <el-radio v-model="questionType" label="3" border>算法</el-radio>
        </div> -->
      </el-col>

      <!-- <el-col :span="24">
        <el-rate v-model="questionLevel" show-text :texts="texts" :max="3">
        </el-rate>
      </el-col>

      <el-col>
        <el-button @click="drawer = true" type="primary" style="width: 400px">
          选择知识点
        </el-button>

        <el-drawer
          title="选择知识点"
          :visible.sync="drawer"
          :with-header="false"
          size="31%"
        >
          <div>
            <el-radio-group v-model="selectKnowledgePoint">
              <el-row :gutter="10">
                <el-radio-button
                  v-for="knowledgePoint in knowledgePointList"
                  :label="knowledgePoint"
                  :key="knowledgePoint"
                  >{{ knowledgePoint }}</el-radio-button
                >
              </el-row>
            </el-radio-group>
          </div>
        </el-drawer>
      </el-col>

      <el-col :span="24">
        <el-button
          type="success"
          plain
          style="margin-left: 100px; width: 200px; margin-top: 20px"
          @click="clickNext"
          >下一步</el-button
        >
      </el-col> -->
    </el-row>
  </div>
</template>
<script>
export default {
  name: "SelectQuestionBasicInfo",
  data() {
    var validaterate = (rule, value, callback) => {
      if (value === 0) {
        callback(new Error("请选择题目难度"));
      }
      callback();
    };
    return {
      texts: ["简单", "普通", "困难"],
      questionInfoForm: {
        questionType: "",
        point: "",
        rate: 0,
      },
      rules: {
        rate: [{ validator: validaterate, trigger: "blur" },{ required: true, trigger: "blur" }],
        point: [
          { required: true, message: "请选择题目知识点", trigger: "blur" },
        ],
        questionType: [
          { required: true, message: "请选择题目类型", trigger: "blur" },
        ],
      },
    };
  },

  computed: {
    knowledgePointList() {
      if (this.questionInfoForm.questionType == "1") {
        return [
          "C基本语法",
          "C输入输出",
          "C数据类型",
          "C变量与常量",
          "C运算符",
          "C判断与循环",
          "C函数",
          "C数组",
          "C指针",
          "C字符串",
          "C结构体",
        ];
      }

      if (this.questionInfoForm.questionType == "2") {
        return [
          "数组",
          "字符串 ",
          "字符串匹配",
          "链表",
          "双向链表",
          "双指针",
          "队列",
          "单调栈",
          "树",
          "二叉树",
          "二叉搜索树",
          "堆",
          "图",
          "哈希表",
          "有序集合",
        ];
      }

      if (this.questionInfoForm.questionType == "3") {
        return [
          "排序",
          "桶排序",
          "计数排序",
          "归并排序",
          "拓扑排序",
          "二分查找",
          "回溯",
          "递归",
          "分治",
          "动态规划",
          "贪心算法",
          "深度优先搜索",
          "广度优先搜索",
        ];
      }

      return [];
    },
  },

  methods: {
    clickNext() {
      this.$refs.questionInfoForm.validate((valid) => {
        if (valid) {
          //根据不同的questionForm跳转到不同的组件
          if (this.$route.params.questionForm === 1) {
            this.$router.push({
              name: "InputQuestionInfoType1",
              params: {
                questionType: this.questionInfoForm.questionType,
                questionLevel: this.questionInfoForm.rate,
                selectKnowledgePoint: this.questionInfoForm.point,
                questionForm: this.$route.params.questionForm,
              },
            });
          }

          if (this.$route.params.questionForm === 2) {
            this.$router.push({
              name: "InputQuestionInfoType2",
              params: {
                questionType: this.questionInfoForm.questionType,
                questionLevel: this.questionInfoForm.rate,
                selectKnowledgePoint: this.questionInfoForm.point,
                questionForm: this.$route.params.questionForm,
              },
            });
          }
        } else {
          console.log("error submit");
        }
      });
      //根据不同的questionForm跳转到不同的组件
      // if (this.$route.params.questionForm === 1) {
      //   this.$router.push({
      //     name: "InputQuestionInfoType1",
      //     params: {
      //       questionType: this.questionType,
      //       questionLevel: this.questionLevel,
      //       selectKnowledgePoint: this.selectKnowledgePoint,
      //       questionForm: this.$route.params.questionForm,
      //     },
      //   });
      // }

      // if (this.$route.params.questionForm === 2) {
      //   this.$router.push({
      //     name: "InputQuestionInfoType2",
      //     params: {
      //       questionType: this.questionType,
      //       questionLevel: this.questionLevel,
      //       selectKnowledgePoint: this.selectKnowledgePoint,
      //       questionForm: this.$route.params.questionForm,
      //     },
      //   });
      // }
    },
    changeRadio() {
      this.questionInfoForm.point = "";
    },
  },

  mounted() {
    console.log("questionForm", this.$route.params.questionForm);
  },
};
</script>
<style scoped>

.el-radio-button {
  margin-bottom: 20px;
  margin-left: 30px;
  margin-top: 10px;
  font-size: 40px;
}

.el-col {
  margin-top: 20px;
}

.el-rate {
  margin-top: 12px;
}
</style>
