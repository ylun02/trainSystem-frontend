<template>
  <section class="services" id="services">
      <div class="row">
        <div class="col-lg-12">
          <div class="section-heading">
            <h6>我们系统的 </h6>
            <h4>特色 <em>优势</em></h4>
          </div>
        </div>
        <div class="col-lg-12">
          <div class="item-list">
            <div class="item">
              <div class="service-item">
                <div class="icon">
                  <img src="../assets/images/service-icon-01.png" alt="">
                </div>
                <h4>有效性</h4>
                <p>可以根据学生的情况进行有效的训练，加强学生的能力。</p>
              </div>
            </div>
            <div class="item">
              <div class="service-item">
                <div class="icon">
                  <img src="../assets/images/service-icon-02.png" alt="">
                </div>
                <h4>高效性</h4>
                <p>面对学生进行一对一的训练，让学生的学习效率更高。</p>
              </div>
            </div>
            <div class="item">
              <div class="service-item">
                <div class="icon">
                  <img src="../assets/images/service-icon-03.png" alt="">
                </div>
                <h4>个性化</h4>
                <p>我们对每个学生掌握知识的能力不同，会出现不同的训练计划，每个人都有专属于自己的计划。</p>
              </div>
            </div>
            <div class="item">
              <div class="service-item">
                <div class="icon">
                  <img src="../assets/images/service-icon-04.png" alt="">
                </div>
                <h4>智能化</h4>
                <p>我们系统可以根据学生的训练情况及时调整训练，智能推荐练习给学生。</p>
              </div>
            </div>
          </div>
          </div>
        </div>
  </section>
</template>

<script>
export default {
  name: "middle"
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
