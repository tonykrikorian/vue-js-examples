/* eslint-disable quotes */
<template>
  <header>
    <nav>
      <ul>
        <li class="nav-item">
          <img src=".\assets\build-a-bot-logo.png" alt="" class="logo" />
          Build-a-bot
        </li>
      </ul>
    </nav>
  </header>
  <main>
    <RobotBuilder />
  </main>
</template>

<script>
// eslint-disable-next-line quotes
// import HomePage from "./home/HomePage.vue";
// eslint-disable-next-line quotes
// eslint-disable-next-line no-unused-vars
// eslint-disable-next-line quotes
import RobotBuilder from "./build/RobotBuilder.vue";

export default {
  // eslint-disable-next-line quotes
  name: "App",
  components: {
    RobotBuilder,
  },
};
</script>

<style>
body {
  background: linear-gradient(to bottom, #555, #999);
  background-attachment: fixed;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}

main {
  margin: 0 auto;
  padding: 30px;
  background-color: white;
  width: 1024px;
  min-height: 300px;
}

header {
  background-color: #999;
  width: 1084px;
  margin: 0 auto;
}
ul {
  padding: 3px;
  display: flex;
}
.nav-item {
  display: inline-block;
  padding: 5px 10px;
  font-size: 22px;
  border-right: 1px solid #bbb;
}
.logo {
  vertical-align: middle;
  height: 30px;
}
</style>
