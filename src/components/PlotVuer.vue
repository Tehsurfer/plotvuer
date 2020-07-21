<template>
  <div class="plotvuer_input">
      <PlotVuerMain :url="fileLocation"  :plotType="foundPlotType" :helpMode="helpMode" :yAxisFilter="yAxisFilter" :xAxisFilter="xAxisFilter"></PlotVuerMain>
  </div>
</template>
<script>
import PlotVuerMain from './PlotVuerMain'

function get_url_extension( url ) {
    return url.split(/[#?]/)[0].split('.').pop().trim();
}

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
      fileLocation: this.url,
      foundPlotType: this.plotType
    };
  },
  methods: {
    loadURL: function(url){
      var extension = get_url_extension(url)
      if (extension === 'json'){
        fetch(url).then(response => response.json())
        .then( data => {
          this.foundPlotType = data.plotType
          this.fileLocation = data.fileLocation
        });
      } else {
        this.fileLocation = url
      }
    }
  },
  watch: {
    url: function(val){
      this.loadURL(val)
    },
    plotType: function(val){
      this.foundPlotType = val
    }
  },
  mounted: function(){
    this.loadURL(this.url)
  }

};
</script>