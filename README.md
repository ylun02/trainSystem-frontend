

# 项目目录 （粗略）
- src
    - api ：对axios的封装和配置
        - request.js ：对axios二次封装。创建axios对象，设置请求和响应拦截器。
    - assets ：静态文件，所依赖的css、js、images、fonts
    - components ：组件
        - login.vue ：登录页面组件
        - register.vue ：注册页面组件
        - webhome.vue ：首页组件
        - middle.vue ：首页组件中用到的子组件
        - homefoot.vue ： 首页组件中用到的子组件
    - pages ：路由组件
        - Admin : 管理员系统组件
            - AddTeacher : 添加教师账号组件
                - index.vue
            - HandleAccount : 管理用户账号组件
                - index.vue
            - HandleStuApplication : 处理学生申请组件
                - index.vue
            - HandleTeaApplication : 处理老师申请组件
                - index.vue
            - SystemInfo : 查看系统信息组件
                - index.vue
            - SystemMaintain : 系统维护组件（待完善）
                - index.vue
            - index.vue : 管理员系统主页组件
        - Teacher : 教师系统组件
            - answerQuestionPages : 处理学生留言组件
                - MyQuestion.vue
            - createQuestionPages : 上传题目功能所需组件
                - InputQuestionInfoType1.vue : 输入填空题题目内容组件
                - InputQuestionInfoType2.vue : 输入编程题题目内容组件
                - SelectQuestionBasicInfo.vue : 输入题目基本信息组件
                - UploadQuestion.vue : 选择上传题目类型组件
            - createTestPages : 制作试卷功能所需组件
                - CreateTest.vue : 制作试卷主页面
                - NormalTest.vue : 输入普通试卷基本信息组件
                - SelectQuestion.vue : 选择题目（组装试卷）组件
                - SetTest.vue : 输入套题基本信息组件
                - SpecialTest.vue : 输入专项试卷基本信息组件
            - personInfoManagementPages : 教师信息功能所需组件
                - BasicInfo.vue : 教师工作信息组件
                - TeacherInfo.vue : 教师个人信息组件
            - queryStudentInfo : 查看学生信息功能所需组件
                - BlankPage.vue : 空白页
                - StudentInfo.vue : 展示学生信息组件
            - sourceManagementPages : 资源管理功能所需组件
                - ModifyNormalTest.vue : 修改普通试卷组件
                - ModifyQuestionType1.vue : 修改填空题组件
                - ModifyQuestionType2.vue : 修改编程题组件
                - ModifySpecialTest.vue : 修改专项试卷组件
                - NormalTestManagement.vue : 普通试卷管理组件
                - QuestionDetail.vue : 查看题目信息组件
                - QuestionManagement.vue : 管理题目组件
                - SourceManagement.vue : 管理资源主页组件
                - SpecialTestManagement.vue : 管理专项试卷组件
                - TestSetManagement.vue : 管理套题组件
            - TeacherHome.vue : 教师系统主页组件
            - TeacherMenu.vue : 教师系统主页菜单组件
        - Train ：训练系统相关组件
            - comment : 评论区组件
                - comment.vue
            - containerMain ：训练系统主界面相关组件
                - info.vue ：展示个人信息页面组件
                - modifyInfo.vue ：修改个人信息页面组件
                - practice.vue ：查看练习记录页面组件
                - setKnowledgePoints.vue ：模式三勾选知识点页面组件
                - studyCharts.vue ：练习记录统计图表页面组件
                - training.vue ：训练模式页面组件
                - welcome.vue ：欢迎页面组件
            - judge 包含批改答案页面组件
                - judge.vue : 批改模式二和三练习组件
                - judge1.vue : 批改模式一练习组件
            - trainModel ：进入训练后相关组件
                - model1.vue 模式一学习知识点页面组件
                - model2.vue ：做题页面组件（包括模式二、三）
                - modelQuestion1.vue : 模式一做题组件
            - index.vue ：训练系统页面结构组件
            - Learning.vue : 学习知识点组件
        - levelTest.vue ：水平测试页面组件
        - viewRecord.vue ：查看单次练习记录页面组件
        - router ：路由配置信息
            - admin.js : 管理员系统所用路由配置信息
            - home.js ：首页所用路由配置信息（首页、登录、注册）
            - index.js ：其余路由配置信息
            - teacher.js : 教师系统所用路由配置信息
        - App.vue ：App组件
        - main.js ：项目入口文件
- vue.config.js ：项目配置文件



# TrainingSystem

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
