<template>
  <div id="status">
    
   
    <!-- Button trigger modal -->
    <button
      type="button"
      @click="updateChart"
      class="btn btn-primary"
      data-toggle="modal"
      data-target="#exampleModalCenter"
    >Submit</button>
<geo-chart :data="[['United States']]"></geo-chart>
    <div
      class="modal fade"
      id="exampleModalCenter"
      tabindex="-1"
      role="dialog"
      aria-labelledby="exampleModalCenterTitle"
      aria-hidden="true"
    >
      <div class="modal-dialog modal-dialog-centered" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalCenterTitle">Status Prediction</h5>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">
            <div class="pie">
              <pie-chart id="chart"
                class="float-right"
                width="344px"
                height="190px"
                :data="chartData"
                :colors="['#006400', '#ff8c00']"
              ></pie-chart>
            </div>

            <div class="float-left">
              <ul class="certified">
                <li>Certified</li>
                {{this.chartData.Certified}}%
                <br />
                <br />
              </ul>
              <ul class="denied">
                <li>Denied</li>
                {{this.chartData.Denied}}%
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>



  <script>
 
export default {
   name: "status",
  
 
  data() {
    return {
      chartData: {}
    };
  },
  methods: {
    updateChart() {
      this.chartData = {
        "Certified": 60,
        "Denied": 40
      };
    }
  }
};

</script>
<style scoped>
pie:hover{
transform: scale(1.5);
}

.certified {
  list-style: none;
}

.certified li::before {
  /* \2022 is the CSS Code/unicode for a disc */
  content: "\2022";
  color: #006400;
  display: inline-block;
  width: 1em;
  margin-left: -0.9em;
  font-weight: bold;
  font-size: 1.1rem;
}
.denied {
  list-style: none;
}

.denied li::before {
  /* \2022 is the CSS Code/unicode for a disc */
  content: "\2022";
  color: #ff8c00;
  display: inline-block;
  width: 1em;
  margin-left: -0.9em;
  font-weight: bold;
  font-size: 1.1rem;
}
.modal-body {
  max-height: 300px;
  overflow-y: auto;
}
</style>