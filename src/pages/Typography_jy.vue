<template>
  <!-- <div class="content"> -->
    <!-- <div class="md-layout">
      <div class="md-layout-item"> -->
        <div class="overlay-page">
          <div class="overlay-content">
            <button @click="closeOverlay">✖</button>
          <md-card>
          <md-card-header data-background-color="gray">
            <div class="flex-container">
              <h1 class="title"><strong>{{ machineId }}</strong></h1>
              <md-button style="padding: 10px 10px; min-width: 10px;" class="md-lg md-simple" @click="postTransaction()">
                <strong>发布</strong>
              </md-button>
              <md-button style="padding: 10px 10px; min-width: 10px;" class="md-lg md-simple" @click="gotoMarket()">
                <strong>算力市场</strong>
              </md-button>
            </div>
          </md-card-header>
          
          <md-card-content>
            <div id="typography">
              <div class="row">
                <div class="tim-typo">
                  <h5>
                    <span class="tim-note">Header 5</span>The life of Material, The life of Material, The life of Material, The life of Material, The life of Material Dashboard
                    <span class="tim-note">Header 5</span>The life of Material, The life of Material, The life of Material, The life of Material, The life of Material
                    Dashboard
                  </h5> 
                </div>
                <div class="tim-typo">
                  <h5>
                    <span class="tim-note">Header 5</span>The life of Material
                    Dashboard
                  </h5>
                </div>
                <div class="tim-typo">
                  <h5>
                    <span class="tim-note">Header 5</span>The life of Material
                    Dashboard
                  </h5>
                </div>
                <div class="tim-typo">
                  <h5>
                    <span class="tim-note">Header 5</span>The life of Material
                    Dashboard
                  </h5>
                </div>
                <div class="tim-typo">
                  <h5>
                    <span class="tim-note">Header 5</span>The life of Material
                    Dashboard
                  </h5>
                </div>
                <div class="tim-typo">
                  <h5>
                    <span class="tim-note">Header 5</span>The life of Material
                    Dashboard
                  </h5>
                </div>
              </div>
            </div>
          </md-card-content>
        </md-card>
          </div>
        </div>
        
      <!-- </div> -->
    <!-- </div>
  </div> -->
</template>

<script>
export default {
  props: {
    dataBackgroundColor: {
      type: String,
      default: "",
    },
  },
  methods: {
    closeOverlay() {
      this.$router.go(-1); // 返回上一页面
    },
    gotoMarket() {
      this.$router.push("/table_tr");
    },
    postTransaction() {
    }
  },
  data() {
    return {
      machineId: this.$route.params.itemId,
    };
  },
};
</script>
<style scoped>
.overlay-page {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}

.overlay-content {
  background: white;
  padding: 20px;
  border-radius: 8px;
  max-width: 80%;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
}

.flex-container {
  display: flex;
  align-items: center;  /* 垂直居中子元素 */
}
.title {
  margin-right: 10px;  /* 在标题和按钮之间添加一些间距 */
}

</style>