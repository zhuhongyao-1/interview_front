<template>
  <div class="first_page" v-loading="loading">
    <Header></Header>
    <div class="main-content">
      <el-container>
        <el-main style="margin-left: 20px">
          <div class="main-header">
            <div class="main-header-content">
              <el-tag
                effect="plain"
                v-for="(item, index) in subjectbtn"
                :key="item"
                @click="subjectvalue(index)"
                id="subjectvalue"
                ref="subjectref"
                >{{ item }}</el-tag
              >
              <!-- <el-tag effect="plain">数学</el-tag>
              <el-tag effect="plain">英语</el-tag>
              <el-tag effect="plain">政治</el-tag>
              <el-tag effect="plain">计算机</el-tag>
              <el-tag effect="plain">医学</el-tag>
              <el-tag effect="plain">农学</el-tag>
              <el-tag effect="plain">经管</el-tag>
              <el-tag effect="plain">艺术概论</el-tag>
              <el-tag effect="plain">法律</el-tag>
              <el-tag effect="plain">教育理论</el-tag>
              <el-tag effect="plain">杂七杂八</el-tag>
              <el-tag effect="plain">标签五</el-tag>
              <el-tag effect="plain">标签三</el-tag>
              <el-tag effect="plain">标签四</el-tag>
              <el-tag effect="plain">标签五</el-tag> -->
            </div>
          </div>
          <div class="main-center">
            <div class="main-center-content">
              <div class="main-center-content-top">
                <el-tabs v-model="activeName" @tab-click="handleClick">
                  <el-tab-pane label="Java" name="first">
                    <br />
                    <div
                      class="main-conetnet"
                      v-for="item in datalist"
                      :key="item.id"
                      v-show="item.status != '审核中'"
                    >
                      <div class="main-conetnet-first">
                        <div class="first-left">
                          <el-col :span="12" class="main-first-col">
                            <div class="main-inside">
                              <div
                                class="transfrom"
                                @click="a(item)"
                                v-html="item.titleName"
                              ></div>
                              <!-- <div class="main-first-left-tag ">       -->
                              <!-- <div v-html="item.explains"></div>                                                                                                                                                                                                                                                                                                         -->
                              <!-- <el-tag type="success" class="tag-main">{{item.tag}}</el-tag> -->
                              <!-- <el-tag type="success">{{item.tag}}</el-tag> -->
                              <!-- </div> -->
                              <div class="difficulty">
                                <div>
                                  <el-tag type="success">{{ item.tag }}</el-tag>
                                </div>
                                <div>|</div>
                                <div>{{ item.difficulty }}</div>
                                <div>|</div>
                                <!-- <div>{{item.difflcult}}</div> -->
                                <!-- <div>|</div> -->
                                <div>{{ item.createTime }}</div>
                              </div>
                              <div class="main-first-information">
                                <el-tooltip
                                  effect="dark"
                                  content="浏览量"
                                  placement="right"
                                >
                                  <el-link icon="el-icon-view">{{
                                    item.pageViews
                                  }}</el-link>
                                </el-tooltip>
                                <el-tooltip
                                  effect="dark"
                                  content="收藏数"
                                  placement="right"
                                >
                                  <el-link icon="el-icon-folder-add">{{
                                    item.collectionNumber
                                  }}</el-link>
                                </el-tooltip>
                                <el-tooltip
                                  effect="dark"
                                  content="留言数"
                                  placement="right"
                                >
                                  <el-link icon="el-icon-edit">{{
                                    item.messageNumber
                                  }}</el-link>
                                </el-tooltip>
                                <!-- <el-tooltip  effect="dark" content="遇到数" placement="right">
                                <el-link icon="el-icon-user-solid">{{item.yudao}}</el-link>
                                 </el-tooltip> -->
                              </div>
                            </div>
                          </el-col>
                        </div>
                        <el-col :span="12">
                          <!-- <div class="main-right-one">
                              <el-tooltip class="item" effect="dark" :content="item.area" placement="top">
      <el-button>区域</el-button>
    </el-tooltip>
                          </div> -->
                        </el-col>
                      </div>
                    </div>
                    <div class="lookmore">
                      <div>
                        <el-button
                          type="primary"
                          @click="lookmore"
                          class="seemore"
                          >查看更多</el-button
                        >
                      </div>
                    </div>
                  </el-tab-pane>
                  <el-tab-pane label="前端" name="second">
                    <br />
                    <div
                      class="main-conetnet"
                      v-for="item in datalist"
                      :key="item.id"
                      v-show="item.status != '审核中'"
                    >
                      <div class="main-conetnet-first">
                        <div class="first-left">
                          <el-col :span="12" class="main-first-col">
                            <div class="main-inside">
                              <div class="transfrom" @click="a(item)">
                                {{ item.titleName }}
                              </div>
                              <!-- <div class="main-first-left-tag ">                                                                                                                                                                                                                                                                                                              
                              <el-tag type="success" class="tag-main">{{item.tag}}</el-tag>
 
                              </div> -->
                              <div class="difficulty">
                                <div>
                                  <el-tag type="success">{{ item.tag }}</el-tag>
                                </div>
                                <div>|</div>
                                <div>{{ item.difficulty }}</div>
                                <div>|</div>
                                <div>{{ item.createTime }}</div>
                              </div>
                              <div class="main-first-information">
                                <el-tooltip
                                  effect="dark"
                                  content="浏览量"
                                  placement="right"
                                >
                                  <el-link icon="el-icon-view">{{
                                    item.pageViews
                                  }}</el-link>
                                </el-tooltip>
                                <el-tooltip
                                  effect="dark"
                                  content="收藏数"
                                  placement="right"
                                >
                                  <el-link icon="el-icon-folder-add">{{
                                    item.collectionNumber
                                  }}</el-link>
                                </el-tooltip>
                                <el-tooltip
                                  effect="dark"
                                  content="留言数"
                                  placement="right"
                                >
                                  <el-link icon="el-icon-edit">{{
                                    item.messageNumber
                                  }}</el-link>
                                </el-tooltip>
                                <!-- <el-tooltip  effect="dark" content="遇到数" placement="right">
                                <el-link icon="el-icon-user-solid">{{item.yudao}}</el-link>
                                 </el-tooltip> -->
                              </div>
                            </div>
                          </el-col>
                        </div>
                        <el-col :span="12">
                          <!-- <div class="main-right-one">
                              <el-tooltip class="item" effect="dark" :content="item.area" placement="top">
      <el-button>区域</el-button>
    </el-tooltip>
                          </div> -->
                        </el-col>
                      </div>
                    </div>
                    <div class="lookmore">
                      <div>
                        <el-button
                          type="primary"
                          @click="lookmore"
                          class="seemore"
                          >查看更多</el-button
                        >
                      </div>
                    </div>
                  </el-tab-pane>
                  <el-tab-pane label="C++" name="third">
                    <br />
                    <div
                      class="main-conetnet"
                      v-for="item in datalist"
                      :key="item.id"
                      v-show="item.status != '审核中'"
                    >
                      <div class="main-conetnet-first">
                        <div class="first-left">
                          <el-col :span="12" class="main-first-col">
                            <div class="main-inside">
                              <div class="transfrom" @click="a(item)">
                                {{ item.titleName }}
                              </div>
                              <!-- <div class="main-first-left-tag ">                                                                                                                                                                                                                                                                                                              
                              <el-tag type="success" class="tag-main">{{item.tag}}</el-tag>
                               <el-tag type="success">{{item.tag}}</el-tag>
                              </div> -->
                              <div class="difficulty">
                                <div>
                                  <el-tag type="success">{{ item.tag }}</el-tag>
                                </div>
                                <div>|</div>
                                <div>{{ item.difficulty }}</div>
                                <div>|</div>
                                <div>{{ item.createTime }}</div>
                              </div>
                              <div class="main-first-information">
                                <el-tooltip
                                  effect="dark"
                                  content="浏览量"
                                  placement="right"
                                >
                                  <el-link icon="el-icon-view">{{
                                    item.pageViews
                                  }}</el-link>
                                </el-tooltip>
                                <el-tooltip
                                  effect="dark"
                                  content="收藏数"
                                  placement="right"
                                >
                                  <el-link icon="el-icon-folder-add">{{
                                    item.collectionNumber
                                  }}</el-link>
                                </el-tooltip>
                                <el-tooltip
                                  effect="dark"
                                  content="留言数"
                                  placement="right"
                                >
                                  <el-link icon="el-icon-edit">{{
                                    item.messageNumber
                                  }}</el-link>
                                </el-tooltip>
                                <!-- <el-tooltip  effect="dark" content="遇到数" placement="right">
                                <el-link icon="el-icon-user-solid">{{item.yudao}}</el-link>
                                 </el-tooltip> -->
                              </div>
                            </div>
                          </el-col>
                        </div>
                        <el-col :span="12">
                          <!-- <div class="main-right-one">
                              <el-tooltip class="item" effect="dark" :content="item.area" placement="top">
      <el-button>区域</el-button>
    </el-tooltip>
                          </div> -->
                        </el-col>
                      </div>
                    </div>
                    <div class="lookmore">
                      <div>
                        <el-button
                          type="primary"
                          @click="lookmore"
                          class="seemore"
                          >查看更多</el-button
                        >
                      </div>
                    </div>
                  </el-tab-pane>
                  <el-tab-pane label="golang" name="fourth">
                    <br />
                    <div
                      class="main-conetnet"
                      v-for="item in datalist"
                      :key="item.id"
                      v-show="item.status != '审核中'"
                    >
                      <div class="main-conetnet-first">
                        <div class="first-left">
                          <el-col :span="12" class="main-first-col">
                            <div class="main-inside">
                              <div class="transfrom" @click="a(item)">
                                {{ item.titleName }}
                              </div>
                              <!-- <div class="main-first-left-tag ">                                                                                                                                                                                                                                                                                                              
                              <el-tag type="success" class="tag-main">{{item.tag}}</el-tag>
                               <el-tag type="success">{{item.tag}}</el-tag>
                              </div> -->
                              <div class="difficulty">
                                <div>
                                  <el-tag type="success">{{ item.tag }}</el-tag>
                                </div>
                                <div>|</div>
                                <div>{{ item.difficulty }}</div>
                                <div>|</div>

                                <div>{{ item.createTime }}</div>
                              </div>
                              <div class="main-first-information">
                                <el-tooltip
                                  effect="dark"
                                  content="浏览量"
                                  placement="right"
                                >
                                  <el-link icon="el-icon-view">{{
                                    item.pageViews
                                  }}</el-link>
                                </el-tooltip>
                                <el-tooltip
                                  effect="dark"
                                  content="收藏数"
                                  placement="right"
                                >
                                  <el-link icon="el-icon-folder-add">{{
                                    item.collectionNumber
                                  }}</el-link>
                                </el-tooltip>
                                <el-tooltip
                                  effect="dark"
                                  content="留言数"
                                  placement="right"
                                >
                                  <el-link icon="el-icon-edit">{{
                                    item.messageNumber
                                  }}</el-link>
                                </el-tooltip>
                                <!-- <el-tooltip  effect="dark" content="遇到数" placement="right">
                                <el-link icon="el-icon-user-solid">{{item.yudao}}</el-link>
                                 </el-tooltip> -->
                              </div>
                            </div>
                          </el-col>
                        </div>
                        <el-col :span="12">
                          <!-- <div class="main-right-one">
                              <el-tooltip class="item" effect="dark" :content="item.area" placement="top">
      <el-button>区域</el-button>
    </el-tooltip>
                          </div> -->
                        </el-col>
                      </div>
                    </div>
                    <div class="lookmore">
                      <div>
                        <el-button
                          type="primary"
                          @click="lookmore"
                          class="seemore"
                          >查看更多</el-button
                        >
                      </div>
                    </div>
                  </el-tab-pane>
                  <el-tab-pane label="python" name="five">
                    <br />
                    <div
                      class="main-conetnet"
                      v-for="item in datalist"
                      :key="item.id"
                      v-show="item.status != '审核中'"
                    >
                      <div class="main-conetnet-first">
                        <div class="first-left">
                          <el-col :span="12" class="main-first-col">
                            <div class="main-inside">
                              <div class="transfrom" @click="a(item)">
                                {{ item.titleName }}
                              </div>
                              <!-- <div class="main-first-left-tag ">                                                                                                                                                                                                                                                                                                              
                              <el-tag type="success" class="tag-main">{{item.tag}}</el-tag>
                               <el-tag type="success">{{item.tag}}</el-tag>
                              </div> -->
                              <div class="difficulty">
                                <div>
                                  <el-tag type="success">{{ item.tag }}</el-tag>
                                </div>
                                <div>|</div>
                                <div>{{ item.difficulty }}</div>
                                <div>|</div>

                                <div>{{ item.createTime }}</div>
                              </div>
                              <div class="main-first-information">
                                <el-tooltip
                                  effect="dark"
                                  content="浏览量"
                                  placement="right"
                                >
                                  <el-link icon="el-icon-view">{{
                                    item.pageViews
                                  }}</el-link>
                                </el-tooltip>
                                <el-tooltip
                                  effect="dark"
                                  content="收藏数"
                                  placement="right"
                                >
                                  <el-link icon="el-icon-folder-add">{{
                                    item.collectionNumber
                                  }}</el-link>
                                </el-tooltip>
                                <el-tooltip
                                  effect="dark"
                                  content="留言数"
                                  placement="right"
                                >
                                  <el-link icon="el-icon-edit">{{
                                    item.messageNumber
                                  }}</el-link>
                                </el-tooltip>
                                <!-- <el-tooltip  effect="dark" content="遇到数" placement="right">
                                <el-link icon="el-icon-user-solid">{{item.yudao}}</el-link>
                                 </el-tooltip> -->
                              </div>
                            </div>
                          </el-col>
                        </div>
                        <el-col :span="12">
                          <!-- <div class="main-right-one">
                              <el-tooltip class="item" effect="dark" :content="item.area" placement="top">
      <el-button>区域</el-button>
    </el-tooltip>
                          </div> -->
                        </el-col>
                      </div>
                    </div>
                    <div class="lookmore">
                      <div>
                        <el-button
                          type="primary"
                          @click="lookmore"
                          class="seemore"
                          >查看更多</el-button
                        >
                      </div>
                    </div>
                  </el-tab-pane>
                </el-tabs>
              </div>
            </div>
          </div>
        </el-main>
        <!-- <el-aside style="width: 500px">
          <div class="aside-center">
            <div class="aside-center-inside">
              <div class="aside-center-inside-header">
                <div class="aside-center-inside-header-inside">
                  <div>关于本站</div>
                </div>
              </div>

              <div class="aside-center-inside-botton">
                <div class="aside-center-inside-botton-inside">
                  <div class="head-portrait">
                    <el-avatar :size="40" @error="errorHandler">
                      <img src="../assets/img/qq.jpg" alt="" />
                    </el-avatar>
                  </div>
                  <div class="aside-center-inside-botton-inside-information">
                    <div
                      class="aside-center-inside-botton-inside-information-font"
                    >
                      我们不断努力扩大我们的学习资源库，为您提供更多更全面的编程题目和解析。您可以在我们的平台上找到各种各样的编程语言和算法题目，以及实用的面试技巧和经验分享。
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <el-card class="box-card">
            <div slot="header" class="clearfix"></div>
            <div
              class="box-card-content"
              v-for="item in scorelist"
              :key="item.id"
            >
              <div class="box-card-content-inside">
                <div class="box-card-content-inside-img">
                  <el-avatar :src="imgurl"></el-avatar>
                </div>
                <div class="box-card-content-inside-jieshao">
                  <div class="box-card-content-inside-jieshao-header">
                    <div class="user">
                      <span>{{ item.username }}</span>
                    </div>
                    <div>
                      <el-tag type="" size="mini">{{ item.tag }}</el-tag>
                    </div>
                  </div>
                  <div>
                    <div><span>本月积分:15</span></div>
                  </div>
                </div>
                <div></div>
              </div>
            </div>
            <div></div>
          </el-card>
        </el-aside> -->
      </el-container>
    </div>
    <Floor></Floor>
  </div>
</template>

<script>
import { lookmorea, lookmoreab } from "../api/firstpage";
import "../css/firstpage.css";
import Floor from "../components/floor.vue";
// import '../components/header.vue'
import Header from "../components/header.vue";
export default {
  data() {
    return {
      subjectbtn: {
        java: "Java",
        javaScript: "JavaScript",
        html: "Html",
        css: "CSS",
        python: "python",
        go: "go",
        cPlus: "c++",
        c: "c",
        ruby: "Ruby",
      },
      imgurl: "http://localhost:3001/qq.jpg",
      Prompt: "111",
      timer: "",
      loading: true,
      visible: true,
      activeName: "first",
      num: 5,
      datalistlength: "",
      one: null,
      two: "",
      numall: "",
      // more:"",
      // number:"",
      datalist: [
        {
          titleName: "equals的使用方法",
          tag: "java基础",
          difflcult: "困难",
          createTime: "2023-4-2",
          pageViews: 100,
          collectionNumber: 100,
          messageNumber: 100,
        },
      ],
      scorelist: {},
      children: [],
    };
  },
  methods: {
    subjectvalue(index) {
      console.log(index, "index");
      console.log(this.subjectbtn.index);
      // console.log(this.$refs.subjectref)
      this.$http({
        url: "http://localhost:3001/users/changesubjectbtn",
        method: "get",
        params: {
          btnvalue: index,
        },
      })
        .then((res) => {
          console.log(res), (this.datalist = res.data);
        })
        .catch((err) => {
          console.log(err);
        });
    },
    a(a) {
      // console.log()
      console.log(a, "0===============");
      console.log(a, this.$cookies.get("username"));
      this.$router.push("/contentmain?id=" + a.id);
      // this.$http({
      //   method:"get",
      //   url:"http://localhost:3001/users/updateseevalue",
      //   // url:"http://localhost:3001/updateseevalue",
      //   params:{
      //     see:"true",
      //     title:a.title,
      //     username:this.$cookies.get("username"),
      //     views:a.views +1
      //     // view:view
      //   }
      // }).then((res) => {

      // //        this.$http({
      // //   method:"get",
      // //   url:"http://localhost:3001/subject/updatescore",
      // //   params:{
      // //     username:this.$cookies.get("username")
      // //   }
      // // }).then((res) => {
      // //     console.log(res)
      // // }).catch((err) => {
      // //     console.log(err)
      // // });
      // }).catch((err) => {
      //     console.log(err)
      // });
      this.$store.dispatch("infromation", a.title);
      this.$cookies.set("title", this.$store.state.title);
      // this.$cookies.set("title",this.$store.state.title)
      // alert(11)
    },
    lookmore() {
      //防止多次请求，数据已经没有了
      if (this.one == this.two) {
        alert("已经是最后一次了,再点也没有用");
        return;
      }
      this.num += 5;

      lookmorea(this.num, this.numall)
        .then(
          (res) => (
            console.log(res, this.datalistlength, this.datalist),
            (this.datalistlength = res.data.data.length),
            (this.datalist = res.data.data),
            (this.numall = res.data.numvalue),
            lookmoreab()
          )
        )
        .catch((err) => {
          console.log(err);
        });
    },
    handleClick(e) {
      console.log("111", e.$options.propsData.label);
      this.getTitleList(e.$options.propsData.label);
      // changearea(e.$options.propsData.label).then(res=>{
      //   console.log(res),this.datalist  = res.data
      // }).catch(err=>{
      //   console.log(err)
      // })
    },
    getTitleList(tag) {
      this.$http({
        url: "http://localhost:3001/title/getTitle",
        method: "get",
        params: {
          tag: tag,
        },
      })
        .then((res) => {
          console.log(res.data.data);
          this.datalist = res.data.data;
        })
        .catch((err) => {
          console.log(err);
        });
    },
    errorHandler() {
      return true;
    },
  },
  components: {
    // header
    Header,
    Floor,
  },
  mounted() {
    this.getTitleList("Java");
    var that = this;
    that.timer = setInterval(function () {
      if (document.readyState == "complete") {
        that.loading = false;
      }
      window.clearInterval(that.timer);
    }, 1000);

    // this.$http({
    //   methods:"get",
    //   url:"users/save",
    //   params:{
    //       num :this.num,
    //       numall : this.numall

    //   }
    // }).then((res=>((console.log(res)),
    // this.datalist = res.data.data,
    // console.log(this.datalist.data)
    // )))
  },
};
</script>

<style  lang="css" scoped>
.main-content {
  margin: 0 auto;
  width: 70%;
}
.main-conetnet-first {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
}
.box-card-content-inside-jieshao-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 10px;
}
.el-card__body {
  border-bottom: 1px solid;
}
.box-card-content-inside {
  display: flex;
  height: 60px;
  border-bottom: 1px solid;
  margin-bottom: 20px;
}
.box-card-content-inside-img {
  margin-right: 20px;
}
.header-inside {
  display: flex;
  justify-content: space-between;
  padding-left: 10px;
  padding-right: 10px;
  height: 10px;
  align-items: center;
}
.score {
  font-size: 14px;
  color: gray;
  text-align: left;
  margin-top: 5px;
}
.aside-button-inside-information-button-inside-right-header {
  display: flex;
  width: 120px;
  justify-content: space-between;
}

.aside-button-inside-information-button-inside-img {
  padding-right: 20px;
}
.text {
  font-size: 14px;
}

/* .item {
      margin-bottom: 18px;
    } */
.box-card {
  /* width: 480px; */
}
.clearfix:before,
.clearfix:after {
  display: table;
  content: "";
}
.clearfix:after {
  clear: both;
}
.aside-button-inside-information-button {
  /* padding: 10px; */
  padding-top: 20px;
  padding-bottom: 20px;
  border-bottom: 1px solid darkgray;
}
.lookmore {
  padding-bottom: 20px;
  padding-top: 20px;
}
.huobao {
  border: 1px solid grey;
  background: aqua;
}
.aside-button-inside-information-header-inside {
  display: flex;
  justify-content: space-between;
}
.aside-button {
  background: white;
}
.aside-button-inside-information-header {
  padding-top: 20px;
  padding-bottom: 20px;
  border-bottom: 1px solid darkgrey;
}
.aside-button-inside-information-button-inside {
  display: flex;
}
.tag-main {
  margin-right: 20px;
}
.aside-button-inside {
  padding-left: 10px;
  padding-right: 10px;
}
.main-center-content-top {
  padding-left: 11px;
  padding-right: 11px;
}
.aside-button {
  background: white;
  box-shadow: 1px 8px 8px white;
}
.aside-button-inside-button-information-inside-describe-top-lift {
  flex: 1;
  line-height: 2;
}
.Jump {
  color: #1890ff;
}
.aside-header-inside {
  padding-left: 10px;
  padding-right: 10px;
}
.transfrom:hover {
  color: #1890ff;
}
.aside-button-inside-button {
  border-bottom: 1px solid;
}
.aside-center {
  padding-left: 10px;
  padding-right: 10px;
  box-shadow: 8px 8px 8px white;
  height: 500px;
}
.v2 {
  flex: 1;
}
.admin {
  flex: 5;
}
.aside-button-inside-button-information-inside {
  display: flex;
}
.aside-button-inside-button-information-inside-touxiang {
  flex: 1;
  line-height: 4;
}
.aside-button-inside-button-information-inside-describe {
  flex: 5;
  text-align: left;
}
.aside-button-inside-button-information-inside-describe-top {
  display: flex;
}
.aside-button-inside-header {
  display: flex;
  justify-content: space-between;
  height: 40px;
  line-height: 40px;
  border-bottom: 1px solid;
  padding-left: 10px;
  padding-right: 10px;
}
.aside-center-inside-botton-inside-information-font {
  text-align: left;
}
.aside-center-inside-botton-inside {
  display: flex;
  justify-content: space-between;
  /* line-height: 2; */
  /* margin-top: 30px; */
}
.aside-center {
  margin-top: 30px;
  margin-bottom: 30px;
  background: white;
}
.aside-center-inside-header-inside {
  height: 50px;
  line-height: 50px;
  border-bottom: 1px solid darkgray;
}
.aside-header-inside {
  /* border: 1px solid rgba(208, 198, 198, 0.709); */
}
.main-right-one {
  /* position: absolute;
    bottom: 10px;
    right: 0; */
  /* position: relative;
    left: 760px;
    bottom: -120px; */
  width: 100%;
  text-align: right;
  height: 48px;
  line-height: 48px;
  /* display: grid; */
  /* align-items: center; */
}
.aside-center-inside-botton-inside-information {
  width: 380px;
  height: 500px;
}
.main-center {
  background: white;
  margin-top: 20px;
}
.first_page {
  background: #f0f2f5;
}
.aside-header {
  /* padding: 20px; */
  /* height: 50px; */
  line-height: 50px;
  border-bottom: 1px solid rgba(207, 199, 199, 0.455);
  background: white;
  box-shadow: 5px 8px 8px white;
}
.aside-header-inside-top {
  border-bottom: 1px solid rgba(173, 168, 160, 0.815);
}
.el-aside {
  padding: 52px 20px;
}
.zouwei {
  position: relative;
}
.main-conetnet {
  display: -webkit-box;
  height: 160px;
  border-bottom: 1px solid rgba(0, 0, 0, 0.377);
}
.main-inside {
  width: 300px;
  font-size: 15px;
}
.main-first-col {
  text-align: left;
  line-height: 40px;
}
.main-first-information {
  display: flex;
  justify-content: space-between;
}
.difficulty {
  display: flex;
  justify-content: space-between;
}
.el-aside {
  width: 500px !important;
}
.main-header {
  background: white;
}
.main-header-content {
  display: flex;
  justify-content: space-between;
}
</style>
