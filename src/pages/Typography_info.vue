<template>
  <div class="content">
    <div class="md-layout">
      <div class="md-layout-item">

        <!-- <div class="overlay-page" @click="closeOverlayClick" ref="overlay">
          <div class="overlay-content" @click.stop> -->
            <!-- <button @click="closeOverlay">✖</button> -->

          <md-card>
            <md-card-header data-background-color="gray">
              <div class="flex-container">
                <h1 class="title"><strong>{{ machine.Name }}</strong></h1>
                <md-button style="padding: 5px 5px; min-width: 10px;" class="md-lg md-simple" @click="Connection(machineId)">
                  <strong>Connection</strong>
                </md-button>
                <md-button style="padding: 5px 5px; min-width: 10px;" class="md-lg md-simple" @click="Delete()">
                  <strong>Delete</strong>
                </md-button>
                <md-button style="padding: 5px 5px; min-width: 10px;" class="md-lg md-simple" @click="Code()">
                  <strong>Code</strong>
                </md-button> 
                <md-button style="padding: 5px 5px; min-width: 10px;" class="md-lg md-simple" @click="Back()">
                  <strong>Back</strong>
                </md-button>
              </div>
              <div v-if="showCode">
                  <pre><code>{{ codeSnippet }}</code></pre>
              </div>
            </md-card-header>
<!--           
          <md-card-content>
            <div id="typography">
              <div class="row">
                <div class="tim-typo">
                  <h5>
                    <span class="tim-note">Id</span>{{ machine.Id }}
                    Dashboard
                  </h5>
                </div>

              </div>
            </div>
          </md-card-content> -->


        </md-card>

        <md-card class="md-card-plain">
              <md-card-header data-background-color="gray">
                <!-- <h3 class="title"><strong>{{ machine.Name }}</strong></h3> -->
                <!-- <hr> -->
                <p class="category">
                  <span style="float: left; width: 50%;"><strong>Id</strong>: {{ machine.Id }}</span>
                  <br>
                  <span style="float: left; width: 50%"><strong>State</strong>: {{machine.State}}</span> 
                  <span style="float: right; width: 50%;"><strong>OwnerOrg</strong>: {{ machine.OwnerOrg }} </span>
                  <br>
                  <span style="float: left; width: 50%"><strong>UserOrg</strong>: {{ machine.UserOrg }} </span> 
                  <span style="float: right; width: 50%;"><strong>UserOrgDueDate</strong>: {{ machine.UserOrgDueDate }} </span>
                  <br>
                  <span style="float: left; width: 50%"><strong>User</strong>: {{ machine.User }} </span> 
                  <span style="float: right; width: 50%;"><strong>Os</strong>: {{ machine.Details.os }} </span>
                  <br>
                  <span style="float: left; width: 50%"><strong>Arch</strong>: {{ machine.Details.arch }} </span> 
                  <span style="float: right; width: 50%;"><strong>CPUSKU</strong>: {{ machine.Details.cpusku }} </span>
                  <br>                  
                  <span style="float: left; width: 50%"><strong>CPUSockets</strong>: {{ machine.Details.cpusockets }} </span> 
                  <span style="float: right; width: 50%;"><strong>CPUCores</strong>: {{ machine.Details.cpucores }} </span>
                  <br>
                  <span style="float: left; width: 50%"><strong>GPU</strong>: {{ machine.Details.gpu }} </span> 
                  <span style="float: right; width: 50%;"><strong>GPUNum</strong>: {{ machine.Details.gpunums }} </span>
                  <br>
                  <span style="float: left; width: 50%"><strong>Network</strong>: {{ machine.Details.network }} </span> 
                  <span style="float: right; width: 50%;"><strong>IP</strong>: {{ machine.Details.ip }} </span>
                  <br>
                  <span style="float: left; width: 50%"><strong>Ram</strong>: {{ machine.Details.ram }} </span> 
                  <br>
                  

                </p>
                <!-- <hr> -->
              </md-card-header>
              <md-card-content>
                <!-- <SimpleTable_tr :transaction="transaction.bidders"></SimpleTable_tr> -->
              </md-card-content>
          </md-card>

          <!-- </div>
        </div> -->
        
      </div>
    </div>
  </div>
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
      this.$router.push("/table_my"); // 返回上一页面
    },
    Connection(Id) {
      this.$router.push({name: "Terminal", params: { itemId: Id }});
    },
    closeOverlayClick(event) {
      if (event.target === this.$refs.overlay) {
        this.$router.push("/table_my");
      }
    },
    Back() {
      this.$router.push("/table_my");
    },
    Delete() {
      this.$axios.get(window.location.protocol+"//"+window.location.host+"/api/v1/deleteresource/"+this.machineId)
        .then(response => {
          setTimeout(() => {
            this.$router.push("/table_my");
          }, 2000);
        })
        .catch(error => {
          console.log('Error fetching users:', error);
        });
    },
    Code() {
      this.showCode = !this.showCode; // 切换显示状态
    }
    
  },
  created() {
    this.$axios.get('/api/v1/queryresource/'+this.machineId)
      .then(response => {
        this.machine = JSON.parse(response.data.data);
        console.log(this.machine);
      })
      .catch(error => {
        console.error('Error fetching users:', error);
      });
  },
  data() {
    return {
      machineId: this.$route.params.itemId,
      machine: {},
      showCode: false,
      codeSnippet: "curl " +window.location.protocol +"//"+window.location.host +  "/api/v1/setup/"+ this.machineId + " | bash",
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
pre {
  background-color: #f4f4f4;
  border: 1px solid #ddd;
  padding: 10px;
  overflow: auto;
}
code {
  color: #d63384;
}

</style>