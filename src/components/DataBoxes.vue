<template>
  <div class="mainBox">
    <div class="mainBox1">
        <h1 class="mainBox1-title">Cases</h1>
        <div class="mainBox1-content">
            <h1>New</h1>
            <span> {{ numberWithCommas(status.NewConfirmed) }} </span>
        
        </div>
        <div class="mainBox1-content">
            <span>TotalConfirmed  </span>
            <span>{{ numberWithCommas(status.TotalConfirmed) }} </span>
        
        </div>
      
    </div>
    <div class="mainBox1">
        <h1 class="mainBox1-title">Deaths</h1>
        <div class="mainBox1-content">
            <h1>New</h1>
            <span> {{ numberWithCommas(status.NewDeaths) }} </span>
        
        </div>
        <div class="mainBox1-content">
            <span>Total  </span>
            <span>{{ numberWithCommas(status.TotalDeaths) }} </span>
        
        </div>
    </div>
  </div>
</template>
<style >

.mainBox {
  /* border: 1px solid red; */
  margin-top: 2rem;
  /* width: 83vw; */
  display: flex;
  justify-content: space-between;
  height: 40vh;
}
@media only screen and (min-width: 768px) and (max-width: 979px) {
.mainBox{
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
}
}
.mainBox1 {
  /* border: 2px solid pink; */
  background-color: rgb(198, 200, 207);
  width: 49%;
  height: 100%;
  text-align: center;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-content: center;
  margin-left: 1rem;
}
.mainBox1-title{
    font-size: 2rem;
    font-weight: bolder;

}
.mainBox1-content{
    /* border: 2px solid red; */
    padding: 1.5rem;
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
       font-size: 1rem;
    font-weight: bold;
}
.mainBox2 {
  /* border: 2px solid pink; */
  width: 49%;
  height: 100%;
}
</style>
<script>
export default {
  name: "DataBoxes",
  props: ["status"],
  methods: {
    numberWithCommas(x) {
      x = x.toString();
      var pattern = /(-?\d+)(\d{3})/;
      while (pattern.test(x)) x = x.replace(pattern, "$1,$2");
      return x;
    },
  }
};
</script>

