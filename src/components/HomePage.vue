<template>
  <div>
    <div class="flex">
      <img src="../assets/pig1.png" class="h-[55vw] w-[40vw]"/>
      <div class="h-[55vw] w-[60vw]">
        <div class="text-center leading-[13vw] text-xl">登录，即刻创造您的应用</div>
        <div class="text-center bg-white">
          <div>
            <ul ref="t1" class="ul">
              <li :class="{ 'choose': currentTab === 0 }" @click="selectTab(0)">手机号登录</li>
              <li :class="{ 'choose': currentTab === 1 }" @click="selectTab(1)">账号密码登录</li>
            </ul>
          </div>

          <div ref="neirong">
            <div :style="{ display: currentTab === 0 ? 'block' : 'none' }">
              <input class="rounded-md"  type="text" placeholder="手机号">
              <br />
              <input class="rounded-md" type="password" placeholder="密码">
            </div>

            <div :style="{ display: currentTab === 1 ? 'block' : 'none' }">
              <input class="rounded-md" id="username" type="text" placeholder="账号">
              <br />
              <input class="rounded-md" id="password" type="password" placeholder="密码">
            </div>
          </div>
          <div class="x">
            <label class="custom-checkbox">
              <input type="checkbox" name="option" value="1" onchange="toggleCheck(this)">
              <span class="checkmark"></span>
            </label>
            我已阅读并同意<a href="#">服务协议</a>和<a href="#">隐私政策</a>
          </div>
          <button class="rounded-md" @click="login">登录</button>
          <div class="zc">还未注册？<a href="#">立即注册</a></div>
        </div>
      </div>
    </div>
  </div>
</template>
  
<script setup>
import { ref } from 'vue';
const t1 = ref();
const neirong = ref();
const currentTab = ref(0); // 用于跟踪当前选中的tab

const selectTab = (index) => {
  currentTab.value = index;
};

function toggleCheck(radio) {
  const checkmark = radio.nextElementSibling;
  if (radio.checked) {
    checkmark.style.display = 'block';
  } else {
    checkmark.style.display = 'none';
  }
}
</script>
  
  <style>
  * {
  margin: 0;
  padding: 0;
}
input {
  height: 5vw;
  width: 30vw;
  border: 1px solid #d6d7df;
  margin-left: 5vw;
  margin-top: 10px;
}
.choose {
  font-weight: bold;
  color: #839df1;
  border-bottom: 3px solid #0035e3;
}

.ul {
  position: relative;
  left: 14vw;
  display: flex;
  width: 30vw;
}

.ul li {
  margin-left: 6vw;
  margin-bottom: 3vw;
}

.g {
  width: 1vw;
  height: 1vw;
}

.x {
  margin-top: 1vw;
  margin-left: -10vw;
  font-size: 1vw;
}

a {
  color: #3861e9;
}

/* 隐藏原生的复选框 */
input[type="checkbox"] {
  display: none;
}

/* 自定义复选框的样式 */
.custom-checkbox {
  position: relative;
  padding-left: 35px;
  cursor: pointer;
  display: inline-block;
  line-height: 20px;
  margin-right: 15px;
}

/* 自定义正方形的样式 */
.custom-checkbox .checkmark {
  position: absolute;
  top: -0.8vw;
  left: 3.5vw;
  height: 1vw;
  width: 1vw;
  background-color :white;
  border: 1px solid black;
}

/* 当复选框选中时的样式 */
.custom-checkbox input[type="checkbox"]:checked + .checkmark:after {
  display: block;
}

/* 自定义打勾的样式 */
.custom-checkbox .checkmark:after {
  content: "";
  position: absolute;
  left: 0.3vw;
  top: 0vw;
  width: 4px;
  height: 8px;
  border: solid green; /* 设置勾的颜色 */
  border-width: 0 2px 2px 0;
  transform: rotate(45deg);
  display: none; /* 默认不显示 */
}

button {
  margin-top: 3vw;
  margin-left: 5vw;
  color: white;
  background-color: #0035e3;
  text-align: center;
  width: 30vw;
  height: 3vw;
}

.zc {
  font-size: 1vw;
  margin-top: 1vw;
  margin-left: 5vw;
  color: #8f91a4;
}
  </style>