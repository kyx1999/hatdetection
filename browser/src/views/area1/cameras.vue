<template>
  <div class="cameras-container">
    <el-row :gutter="32" style="margin:0 auto">
      <el-col :xs="24" :sm="24" :lg="8">
        <div class="camera-wrapper">
          <r-t-m-p-player />
          <br>
          <el-button class="alarm-button" type="danger">
            发出警报
          </el-button>
        </div>
      </el-col>
      <el-col :xs="24" :sm="24" :lg="8">
        <div class="camera-wrapper">
          <r-t-m-p-player />
          <br>
          <el-button class="alarm-button" type="danger">
            发出警报
          </el-button>
        </div>
      </el-col>
      <el-col :xs="24" :sm="24" :lg="8">
        <div class="camera-wrapper">
          <r-t-m-p-player />
          <br>
          <el-button class="alarm-button" type="danger">
            发出警报
          </el-button>
        </div>
      </el-col>
    </el-row>
    <el-row :gutter="32" style="margin:0 auto">
      <el-col :xs="24" :sm="24" :lg="8">
        <div class="camera-wrapper">
          <r-t-m-p-player />
          <br>
          <el-button class="alarm-button" type="danger">
            发出警报
          </el-button>
        </div>
      </el-col>
      <el-col :xs="24" :sm="24" :lg="8">
        <div class="camera-wrapper">
          <r-t-m-p-player />
          <br>
          <el-button class="alarm-button" type="danger">
            发出警报
          </el-button>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
import RTMPPlayer from './components/RTMPPlayer'

export default {
  name: 'Cameras',
  components: { RTMPPlayer }
}
</script>

<style lang="scss" scoped>
.cameras-container{
  padding: 32px;
  background-color: rgb(240, 242, 245);
  position: relative;

  .camera-wrapper {
    background: #fff;
    padding: 16px 16px 0;
    margin-bottom: 32px;

    .alarm-button{
      position: relative;
      left: 50%;
      margin-left: -50px;
      margin-bottom: 16px;
    }
  }
}
</style>
