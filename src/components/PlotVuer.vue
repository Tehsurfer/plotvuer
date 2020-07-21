<template>
  <div class="plotvuer_input">
      <PlotVuerMain></PlotVuerMain>
  </div>
</template>
<script>
import PlotVuerMain from './PlotVuerMain'


export default {
  name: "PlotVuer",
  components: {
      PlotVuerMain
  },
  props:{
    url:{
      type: String,
      default: 'https://mapcore-bucket1.s3-us-west-2.amazonaws.com/ISAN/csv-data/use-case-4/RNA_Seq.csv',
    },
    plotType:{
      type: String,
      default: 'heatmap'
    },
    yAxisFilter: {
      type: Array,
      default: () => []
    },
    xAxisFilter: {
      type: Array,
      default: () => []
    },
    helpMode: {
      type: Boolean,
      default: false
    }
    
  },
  data: function() {
    return {
    };
  },
  methods: {
    loadURL: function(url){
      
    }
  },
  watch: {
    url: function(val){
      this.loadURL(val)
    }
  },

};
</script>
<style scoped src="element-ui/lib/theme-chalk/index.css"></style>
<style scoped>
.controls{
  padding-left: 55px;
  padding-top: 5px;
  align-items: left;
  min-width: 700px;
  text-align: left;
}
.ui-controls{
  position: absolute;
  height: 100%;
  width: 40px;
  right: 0px;
  pointer-events: none;
  z-index: 5
}


.title{
  width: 572px;
  height: 17px;
  font-family: Helvetica;
  font-size: 14px;
  font-weight: 500;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
  color: #606266;
  padding-top: 8px;
  padding-bottom: 8px;
}
.options {
  position: absolute;
  z-index: 11000;
  height: calc(100% - 20px);
  text-align: right;
  overflow: auto;
  padding-top: 8px;
  padding-bottom: 8px;
}

.channel-select {
  min-width: 220px;
  margin: 8px;
  margin-left: 0px;
  margin-right: 16px;
  border-radius: 4px;
  box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.12);

}
.view-heatmap-button{
  border-radius: 4px;
  box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.12);
  border: solid 1px #d8dce6;
  background-color: #8300bf;

  font-size: 14px;
  font-weight: 500;
  font-stretch: normal;
  font-style: normal;
  line-height: 1;
  letter-spacing: normal;
  color: white;
}
.input-div {
  display: flex;
  justify-content: space-between;
}

.zoomIn{
  top:51px;
  right:20px;
  position: absolute;
  pointer-events: auto;
}
.zoomOut{
  top:90px;
  right:20px;
  position: absolute;
    pointer-events: auto;
}
.resetView {
  top:129px;
  right:20px;
  position: absolute;
    pointer-events: auto;
}
.icon-button {
  box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.5);
  border: solid 1px #ffffff;
  background-color: #ffffff;
}
.freeSpin {
  bottom:79px;
  right:50%;
  position: absolute;
}
>>> .plot-popper {
  padding:9px 10px;
  min-width:150px;
  font-size:12px;
  color: #fff;
  background-color: #8300bf;  
}
>>> .plot-popper .popper__arrow::after{
  border-left-color: #8300bf !important;
}

>>> .el-select__tags-text {
  max-width: 90px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  display: inline-block;
  vertical-align: middle;
}
.modebar-container{
  display: none;
}
</style>

