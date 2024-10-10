<template>
  <el-tabs :tab-position="tabPosition" style="height: 100%" class="demo-tabs">
    <el-tab-pane label="工作台">工作台内容</el-tab-pane>
    <el-tab-pane label="项目">项目内容</el-tab-pane>
    <el-tab-pane label="AI">AI内容</el-tab-pane>
    <el-tab-pane label="事项">事项内容</el-tab-pane>
    <el-tab-pane label="代码" class="code-tabs-pane">
      <el-tabs v-model="activeName" class="demo-tabs" @tab-click="handleClick">
        <el-tab-pane label="最近访问" name="first">
          <div style="text-align: center; margin-top: 8vw">
            <img src="../../public/images/4.png" alt="" />
            <div>暂无数据</div>
          </div>
        </el-tab-pane>
        <el-tab-pane label="全部仓库" name="second">
          <!-- 全部仓库内容 -->
        </el-tab-pane>
        <el-tab-pane label="开源仓库" name="third">
          <div style="text-align: center; margin-top: 8vw">
            <img src="../../public/images/4.png" alt="" />
            <div>暂无数据</div>
          </div>
        </el-tab-pane>
      </el-tabs>
    </el-tab-pane>
    <el-tab-pane label="制品">制品内容</el-tab-pane>
    <el-tab-pane label="洞察">洞察内容</el-tab-pane>
    <el-tab-pane label="知识">知识内容</el-tab-pane>
    <el-tab-pane label="自动化">自动化内容</el-tab-pane>
  </el-tabs>
</template>

<script setup>
import { ref } from 'vue';
import { ElTabs, ElTabPane } from 'element-plus';

// 定义 tabPosition 和 activeName 响应式数据
const tabPosition = ref('left');
const activeName = ref('first');

// 处理标签点击事件
const handleClick = (tab, event) => {
  console.log(tab, event);
};

// 如果你的项目中使用了 <script setup> 语法，确保 Element Plus 组件已经被全局注册
// 如果没有全局注册，可以在此处按需导入并注册
</script>

<style>
.demo-tabs > .el-tabs__content {
  padding: 32px;
  color: #6b778c;
  font-size: 32px;
  font-weight: 600;
}

.el-tabs--right .el-tabs__content,
.el-tabs--left .el-tabs__content {
  height: 100%;
}
</style>