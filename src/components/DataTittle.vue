<template>
    <div class="dataTitlte">
      <h2 class="country-tiltle">{{text}}</h2>
        <div class="timestamp">
            {{timestamp}}
        </div>
        </div>
</template>
<style >
.dataTitlte{
    text-align: center;

    font-size: 2rem;
}
.country-tiltle{
font-size: 2.54rem;
font-weight: bolder;
}
.timestamp{
  font-weight: bold;
}
</style>
<script>
import moment from 'moment'
export default {
name:"DataTitlte",
props:['text',"dataDate"],
computed:{
    timestamp:function () {
      return moment(this.dataDate).format('MMMM Do YYYY, h:mm:a');
    }
  }
}
</script>
