<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";
import axios from "axios";
const router = useRouter();
const giteedata = ref({
  grant_type: "password",
  username: "1808200572@qq.com",
  password: "CPZW18872689076",
  client_id: "1329c377a227fb1d028261bde08b7b79f34587547ead7da6790ca15dfa310870",
  client_secret:
    "685fa2cd8820dbb85688b5c17564cbc8d10aa10cd48ab93f8afaea3b8f43182c",
  scope:
    "user_info projects pull_requests issues notes keys hook groups gists enterprises",
});
const handleClick = () => {
  axios
    .post("https://gitee.com/oauth/token", giteedata.value)
    .then((res) => {
      if (res.data.access_token != "") {
        router.push("/test");
      } else {
        console.log("登录出现错误");
      }
      console.log("res.data.access_token", res.data.access_token);
    })
    .catch((err) => {
      console.log(err);
    });
};
const getAuthorization = () => {
  axios
    .get(
      "https://gitee.com/oauth/authorize?client_id=f3fd7280e1bc85e43ffdb1f4bd00002bd1a862346ee0fb2f92987cef47de2d91&redirect_uri=405d2e20c02c7a45f442405bff5b9ed59967cee7ecfa757b8bce41f623c9279d&response_type=code"
    )
    .then((res) => {
      console.log("res", res);
    })
    .catch((error) => {
      console.log("error", error);
    });
};
</script>
<template>
  <header>
    <section>
      <img src="../../public/images/1.png" />
    </section>
    <div class="biglogin">
      <div class="loginbox">
        <h1 style="text-align: center">登录，即刻创造您的应用</h1>
        <div class="switchlogin">
          <p>手机号登陆</p>
          <p>账号密码登录</p>
        </div>
        <div class="textinput">
          <p>
            <el-input
              v-model="giteedata.username"
              style="width: 350px; height: 50px"
              placeholder="账号"
            />
          </p>
          <p>
            <el-input
              v-model="giteedata.password"
              style="width: 350px; height: 50px"
              type="password"
              placeholder="密码"
              show-password
            />
          </p>
        </div>
        <el-checkbox label="我已阅读并同意服务协议和隐私协议" size="large" />
        <el-button type="primary" @click="handleClick">登录</el-button>
        <p style="text-align: center">
          <span>还未注册？</span>
          <span style="color: #409eff">立即注册</span>
        </p>
      </div>
    </div>
  </header>
</template>
<style scoped>
header,
.switchlogin,
.biglogin,
.loginbox,
.textinput {
  display: flex;
}

img {
  width: 40vw;
  height: 99.5vh;
}

.biglogin {
  width: 50vw;
  height: 100vh;
  justify-content: center;
  align-items: center;
}

.loginbox {
  justify-content: center;
  flex-direction: column;
}

.switchlogin {
  justify-content: space-around;
}

.textinput {
  align-items: center;
  flex-direction: column;
}
</style>
