<template>
  <div>
    <el-card>
      <div slot="header">
        <div>收藏记录{{ num }}</div>
      </div>
      <div class="card-content">
        <div class="card-content-box" v-for="item in items" :key="item.id">
          <div class="card-content-child">
            <div class="card-content-child-inside">
              <div class="card-content-header">
                <div class="card-content-header-inside">
                  <div @click="gotitle(item)" v-html="item.titleName"></div>
                </div>
              </div>

              <div class="card-content-tag">
                <div class="card-content-tag-inside">
                  <el-tag>{{ item.tag }}</el-tag>
                </div>
              </div>

              <div class="card-content-information">
                <div class="card-content-information-inside">
                  <ul>
                    <li style="text-align: left">{{ item.questionType }}</li>
                    <li
                      style="
                        border-left: 1px solid;
                        border-right: 1px solid;
                        text-align: center;
                      "
                    >
                      {{ item.difflculty }}
                    </li>
                    <li style="text-align: right">{{ item.createTime }}</li>
                  </ul>
                </div>
              </div>

              <div class="card-content-bottom">
                <div class="card-content-bottom-inside">
                  <el-link icon="el-icon-edit" :underline="false"
                    >浏览数&nbsp;&nbsp;{{ item.pageViews }}</el-link
                  >
                  <el-link icon="el-icon-edit" :underline="false"
                    >收藏数&nbsp;&nbsp;{{ item.collectionNumber }}</el-link
                  >
                  <el-link icon="el-icon-edit" :underline="false"
                    >留言数&nbsp;&nbsp;{{ item.messageNumber }}</el-link
                  >
                </div>
              </div>
            </div>
            <div class="card-content-btn">
              <el-button type="primary" size="mini">选项</el-button>
            </div>
          </div>
        </div>
      </div>
    </el-card>
    <floor></floor>
  </div>
</template>

<script>
import "../css/seevalue.css";
export default {
  name: "WorkspaceJsonSeevalue",

  data() {
    return {
      num: 0,
      items: "",
    };
  },

  mounted() {
    this.$http({
      method: "get",

      url: "http://localhost:3001/users/collectionValue",
      params: {
        userId: this.$cookies.get("userId"),
      },
    })
      .then((res) => {
        console.log(res),
          (this.items = res.data.data),
          (this.num = res.data.data.length),
          console.log(this.$cookies.username);
      })
      .catch((err) => {
        console.log(err);
      });
  },

  methods: {
    gotitle(vlaue) {
      console.log("qqqq" + vlaue);
      this.$router.push("/contentmain?id=" + vlaue.id);
      this.$store.dispatch("infromation", vlaue.titleName);
      this.$cookies.set("title", this.$store.state.title.titleName);
    },
  },
};
</script>

<style lang="css" scoped>
</style>