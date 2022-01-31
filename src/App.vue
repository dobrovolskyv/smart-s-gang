<template>
  <div class="content">
    <User />
    <Alcohol />
  </div>
</template>

<script>
import User from "@/components/User";
import Alcohol from "./components/Alcohol";

export default {
  components: {
    User,
    Alcohol,
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
}
.content {
  display: flex;
  justify-content: space-between;
  min-height: 100vh;
}
@media (max-width: 768px) {
  .content {
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  .main {
    width: 100%;
  }
  .header {
    width: 100%;
  }
}
</style>

