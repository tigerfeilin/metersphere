<template>
  <div class="metric-container">
    <el-row type="flex">
      <el-col>
        <div style="font-size: 14px;color: #AAAAAA;float: left">{{$t('api_report.response_code')}} :</div>
        <el-tooltip
          :content="responseResult.responseCode"
          placement="top">
          <div class="node-title">
            {{responseResult && responseResult.responseCode ? responseResult.responseCode :'0'}}
          </div>
        </el-tooltip>
      </el-col>
      <el-col>
        <div style="font-size: 14px;color: #AAAAAA;float: left">{{$t('api_report.response_time')}} :</div>
        <div style="font-size: 14px;color:#61C550;margin-top:2px;margin-left:10px;float: left">{{responseResult && responseResult.responseTime?responseResult.responseTime:0}} ms</div>
      </el-col>
      <el-col>
        <div style="font-size: 14px;color: #AAAAAA;float: left">{{$t('api_report.response_size')}} :</div>
        <div style="font-size: 14px;color:#61C550; margin-top:2px;margin-left:10px;float: left">{{responseResult && responseResult.responseSize?responseResult.responseSize:0}} bytes</div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
  export default {
    name: "MsRequestMetric",

    props: {
      response: {
        type: Object,
        default() {
          return {}
        }
      }
    },


    computed: {
      responseResult() {
        return this.response && this.response.responseResult ? this.response.responseResult : {};
      },
      error() {
        return this.response && this.response.responseCode && this.response.responseCode >= 400;
      }
    }
  }
</script>

<style scoped>
  .metric-container {
    padding-bottom: 10px;
  }

  .node-title {
    width: 150px;
    text-overflow: ellipsis;
    white-space: nowrap;
    flex: 1 1 auto;
    padding: 0px 5px;
    overflow: hidden;
    font-size: 14px;
    color: #61C550;
    margin-top: 2px;
    margin-left: 10px;
    float: left
  }
</style>
