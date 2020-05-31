<template>
  <el-row :gutter="40" class="panel-group">
    <el-col :xs="12" :sm="12" :lg="6" class="card-panel-col">
      <div class="card-panel" @click="handleSetLineChartData('newVisitis')">
        <!--<div class="card-panel-icon-wrapper icon-people">-->
        <div class="card-panel-icon-wrapper icon-people-now">
          <!--<svg-icon icon-class="peoples" class-name="card-panel-icon" />-->
          <svg-icon icon-class="peoples" class-name="card-panel-icon" />
        </div>
        <div class="card-panel-description">
          <!--<div class="card-panel-text">-->
          <!--New Visits-->
          <!--</div>-->
          <div class="card-panel-text">
            当前人数
          </div>
          <!--<count-to :start-val="0" :end-val="102400" :duration="2600" class="card-panel-num" />-->
          <count-to :start-val="0" :end-val="44" :duration="2600" class="card-panel-num" />
        </div>
      </div>
    </el-col>
    <el-col :xs="12" :sm="12" :lg="6" class="card-panel-col">
      <div class="card-panel" @click="handleSetLineChartData('messages')">
        <!--<div class="card-panel-icon-wrapper icon-message">-->
        <div class="card-panel-icon-wrapper icon-people-today">
          <!--<svg-icon icon-class="message" class-name="card-panel-icon" />-->
          <svg-icon icon-class="peoples" class-name="card-panel-icon" />
        </div>
        <div class="card-panel-description">
          <!--<div class="card-panel-text">-->
          <!--Messages-->
          <!--</div>-->
          <div class="card-panel-text">
            今日上报
          </div>
          <!--<count-to :start-val="0" :end-val="81212" :duration="3000" class="card-panel-num" />-->
          <count-to :start-val="0" :end-val="9" :duration="3000" class="card-panel-num" />
        </div>
      </div>
    </el-col>
    <el-dialog v-el-drag-dialog :visible.sync="dialogTableVisible" title="未读消息" @dragDialog="handleDrag">
      <el-table :data="gridData">
        <el-table-column property="date" label="日期" />
        <el-table-column property="content" label="内容" />
      </el-table>
      <br>
      <el-button type="primary" style="position: relative; left: 50%; margin-left: -50px;">
        全部标为已读
      </el-button>
    </el-dialog>
  </el-row>
</template>

<script>
import CountTo from 'vue-count-to'
import elDragDialog from '@/directive/el-drag-dialog' // base on element-ui

export default {
  components: {
    CountTo
  },
  directives: { elDragDialog },
  data() {
    return {
      dialogTableVisible: false,
      gridData: [{
        date: '2020-05-31',
        content: '厂区1发现安全隐患！'
      }, {
        date: '2020-05-31',
        content: '厂区1发现安全隐患！'
      }, {
        date: '2020-05-31',
        content: '厂区1发现安全隐患！'
      }]
    }
  },
  methods: {
    handleSetLineChartData(type) {
      this.$emit('handleSetLineChartData', type)
    },
    // v-el-drag-dialog onDrag callback function
    handleDrag() {
      this.$refs.select.blur()
    }
  }
}
</script>

<style lang="scss" scoped>
.panel-group {
  margin-top: 18px;

  .card-panel-col {
    margin-bottom: 32px;
  }

  .card-panel {
    height: 108px;
    cursor: pointer;
    font-size: 12px;
    position: relative;
    overflow: hidden;
    color: #666;
    background: #fff;
    box-shadow: 4px 4px 40px rgba(0, 0, 0, .05);
    border-color: rgba(0, 0, 0, .05);

    &:hover {
      .card-panel-icon-wrapper {
        color: #fff;
      }

      .icon-people {
        background: #40c9c6;
      }

      .icon-message {
        background: #36a3f7;
      }

      .icon-money {
        background: #f4516c;
      }

      .icon-shopping {
        background: #34bfa3
      }

      .icon-people-now {
        color: #40c9c6;
      }

      .icon-people-today {
        color: #f4516c;
      }

      .icon-message-unread {
        color: #36a3f7;
      }

      .icon-message-emergency {
        color: #f4516c
      }
    }

    .icon-people {
      color: #40c9c6;
    }

    .icon-message {
      color: #36a3f7;
    }

    .icon-money {
      color: #f4516c;
    }

    .icon-shopping {
      color: #34bfa3
    }

    .icon-people-now {
      color: #40c9c6;
    }

    .icon-people-today {
      color: #f4516c;
    }

    .icon-message-unread {
      color: #36a3f7;
    }

    .icon-message-emergency {
      color: #f4516c
    }

    .card-panel-icon-wrapper {
      float: left;
      margin: 14px 0 0 14px;
      padding: 16px;
      transition: all 0.38s ease-out;
      border-radius: 6px;
    }

    .card-panel-icon {
      float: left;
      font-size: 48px;
    }

    .card-panel-description {
      float: right;
      font-weight: bold;
      margin: 26px;
      margin-left: 0px;

      .card-panel-text {
        line-height: 18px;
        color: rgba(0, 0, 0, 0.45);
        font-size: 16px;
        margin-bottom: 12px;
      }

      .card-panel-num {
        font-size: 20px;
      }
    }
  }
}

@media (max-width:550px) {
  .card-panel-description {
    display: none;
  }

  .card-panel-icon-wrapper {
    float: none !important;
    width: 100%;
    height: 100%;
    margin: 0 !important;

    .svg-icon {
      display: block;
      margin: 14px auto !important;
      float: none !important;
    }
  }
}
</style>
