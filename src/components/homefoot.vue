<template>
  <section class="our-courses" >
      <div class="row">
        <div class="col-lg-6 offset-lg-3">
          <div class="section-heading">
            <h6>我们系统</h6>
            <h4>你可以 <em>训练的模式</em></h4>
            <p>针对不同基础的学生，有不同的训练模式</p>
          </div>
        </div>
        <div class="col-lg-12">
          <div class="naccs">
              <div class="row">
                <div class="col-lg-3">
                  <div class="menu">
                    <div class="gradient-border" v-on:click="change(0)"><span >模式一</span></div>
                    <div class="gradient-border" v-on:click="change(1)" ><span >模式二</span></div>
                    <div class="gradient-border" v-on:click="change(2)"><span >模式三</span></div>
                  </div>
                </div>
                <div class="col-lg-9">

                  <div v-show="0===number">
                    <ul class="nacc">
                      <li class="active">
                        <div>
                          <div class="left-image">
                            <img src="../assets/images/courses-01.jpg" alt="">
                          </div>
                          <div class="right-content">
                            <h4>训练模式一</h4>
                            <p>此模式针对基础较薄弱学生。
                              <br><br>训练模式为：首先进行知
                              识点学习，学习之后再通过配套练习来检验掌握情况
                            </p>
                          </div>
                        </div>
                      </li>
                    </ul>
                  </div>
                  <div v-show="1===number">
                    <ul class="nacc">
                      <li class="active">
                        <div>
                          <div class="left-image">
                            <img src="../assets/images/courses-02.jpg" alt="">
                          </div>
                          <div class="right-content">
                            <h4>训练模式二</h4>
                            <p>  此模式针对有一定基础的学生。
                              <br><br>训练模式为：对学生给出系统的训练计划，学生依次完成计划的套题。</p>

                          </div>
                        </div>
                      </li>
                    </ul>
                  </div>
                  <div v-show="2===number">
                    <ul class="nacc">
                      <li class="active">
                        <div>
                          <div class="left-image">
                            <img src="../assets/images/courses-03.jpg" alt="">
                          </div>
                          <div class="right-content">
                            <h4>训练模式三</h4>
                            <p>    此模式针对基础较好，只是想针对某些薄弱知识点进行巩固学习的学生。
                              <br><br>首先，学生勾选想要专项学习的知识点，然后系统针对该学生推出专门的专项练习计划，学生依次完成训练计划中的套题。</p>

                          </div>
                        </div>
                      </li>
                    </ul>
                  </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
  </section>
</template>

<script>
export default {
  name: "homefoot",
  data(){
    return {
      number:0
    }
  },
  methods:{
    change(index){
      this.number=index;
    }
  }
}

</script>

<style scoped>
@import "../assets/css/templatemo-eduwell-style.css";
@import "../assets/css/bootstrap.min.css";
.item-list{
  display: flex;
  justify-content: flex-start;
  align-items: center;
  margin: 13px 0px;
  width: 100%;
  flex-flow: row wrap;
}
</style>
