<template>
  <div class="testpaper">
    <Header></Header>
    <div class="testpaper-inside">
      <el-container>
        <el-header>
          <dir class="testpaper-header">
            <div class="testpaper-header-first">
              <div class="testpaper-header-first-left">
                <div>
                  <el-link icon="el-icon-edit">搜索</el-link>
                </div>
              </div>
              <div class="testpaper-header-first-right">
                <div>
                  <el-input
                    placeholder="请输入内容"
                    v-model="testpaper_first"
                    class="input-with-select"
                  >
                    <el-button
                      slot="append"
                      icon="el-icon-search"
                      @click="searchpapervalue"
                    ></el-button>
                  </el-input>
                </div>
              </div>
            </div>
            <div class="testpaper-header-first">
              <div class="testpaper-header-first-left">
                <div>
                  <el-link icon="el-icon-edit">筛选 </el-link>
                </div>
              </div>
              <div class="testpaper-header-first-right">
                <div>
                  <el-autocomplete
                    class="inline-input"
                    v-model="state1"
                    :fetch-suggestions="querySearch"
                    placeholder="请输入内容"
                    @select="handleSelect"
                  ></el-autocomplete>
                </div>
              </div>
            </div>
            <div class="testpaper-header-first">
              <div class="testpaper-header-first-left">
                <!-- <div>
                  <el-link icon="el-icon-edit">来源</el-link>
                </div> -->
              </div>
              <div class="testpaper-header-first-right">
                <div>
                  <!-- <el-tooltip
                    effect="dark"
                    content="官方发布的题目"
                    placement="top"
                  >
                    <el-button size="medium" class="guanf" index="3"
                      >官方</el-button
                    >
                  </el-tooltip>
                  <el-tooltip
                    effect="dark"
                    content="用户自己上传"
                    placement="top"
                  >
                    <el-button size="medium" class="guanf" index="4"
                      >用户</el-button
                    >
                  </el-tooltip> -->
                </div>
              </div>
            </div>
          </dir>
        </el-header>
        <el-main>
          <div class="testpaper-main">
            <div class="testpaper-main-header">
              <div class="transform">
                <div class="transform-inside">
                  <div class="transform-inside-information">
                    <div class="transform-inside-information-header">
                      <div class="transform-inside-information-header-left">
                        <ul class="transform-inside-information-header-left-ul">
                          <li value="1" class="active" id="btn">最新</li>
                          <li value="2" id="btn">最热</li>
                          <!-- <li value="3" id="btn">最没</li> -->
                        </ul>
                      </div>
                      <div class="transform-inside-information-header-right">
                        <el-tooltip
                          effect="dark"
                          content="还未开发"
                          placement="top"
                        >
                          <el-button
                            type="primary"
                            size="mini"
                            @click="uploadtestpaper"
                            >上传试卷</el-button
                          >
                        </el-tooltip>
                        <el-dialog
                          title="提交试卷信息"
                          :visible.sync="testpapervalue"
                        >
                          <el-form :model="testpaper">
                            <el-form-item
                              label="试卷名称"
                              :label-width="formLabelWidth"
                            >
                              <el-input
                                v-model="testpaper.title"
                                autocomplete="off"
                              ></el-input>
                            </el-form-item>
                            <el-form-item
                              label="试卷标签"
                              :label-width="formLabelWidth"
                            >
                              <el-select
                                v-model="testpaper.tag"
                                multiple
                                filterable
                                allow-create
                                default-first-option
                                placeholder="请选择文章标签"
                              >
                                <el-option
                                  v-for="item in options"
                                  :key="item.value"
                                  :label="item.label"
                                  :value="item.value"
                                >
                                </el-option>
                              </el-select>
                              <imgupload
                                imgvalue="请上传试卷"
                                @custom="father"
                              ></imgupload>
                              {{ updateTitlea }}
                            </el-form-item>
                          </el-form>
                          <div slot="footer" class="dialog-footer">
                            <el-button @click="testpapervalue = false"
                              >取 消</el-button
                            >
                            <el-button type="primary" @click="testpapervaluea()"
                              >确 定</el-button
                            >
                          </div>
                        </el-dialog>
                      </div>
                    </div>
                    <div class="tab-all">
                      <div class="tab-1" style="display: block">
                        <div class="testpaper-tab-1">
                          <div
                            class="testpaper-tab-1-frame"
                            v-for="testpapernew in testpaperold"
                            :key="testpapernew.id"
                          >
                            <div class="testpaper-tab-1-frame-inside">
                              <div class="testpaper-tab-1-frame-inside-title">
                                <div
                                  class="testpaper-tab-1-frame-inside-title-information"
                                >
                                  <!-- <span @click="testtitle(testpapernew)"
                                    ><el-link>{{ testpapernew.title }}</el-link>
                                  </span> -->
                                  <a
                                    :href="testpapernew.img"
                                    download="test.png"
                                    >{{ testpapernew.title }}</a
                                  >
                                </div>
                              </div>
                              <div class="testpaper-tab-1-frame-inside-img">
                                <div
                                  class="testpaper-tab-1-frame-inside-img-information"
                                >
                                  <img :src="testpapernew.img" alt="百度" />
                                </div>
                              </div>
                              <div class="testpaper-tab-1-frame-inside-data">
                                <div
                                  class="testpaper-tab-1-frame-inside-data-information"
                                >
                                  <ul>
                                    <!-- <li
                                      class="testpaper-tab-1-frame-inside-data-information-li"
                                    >
                                      {{ testpapernew.paper_data }}
                                    </li> -->
                                    <li>
                                      <el-link :underline="false"
                                        >{{ testpapernew.viewNum
                                        }}<i
                                          class="el-icon-view el-icon--right"
                                        ></i>
                                      </el-link>
                                    </li>
                                  </ul>
                                </div>
                              </div>
                              <div
                                class="testpaper-tab-1-frame-inside-describe"
                              >
                                <button v-if="testpapernew.tag[0] != null">
                                  {{ testpapernew.tag[0] }}
                                </button>
                                <button v-if="testpapernew.tag[1] != null">
                                  {{ testpapernew.tag[1] }}
                                </button>
                                <button v-if="testpapernew.tag[2] != null">
                                  {{ testpapernew.tag[2] }}
                                </button>
                              </div>
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>
                    <div class="testpage-pagination">
                      <div class="block">
                        <!-- <span class="demonstration">显示总数</span> -->
                        <el-pagination
                          background
                          @size-change="handleSizeChange"
                          @current-change="handleCurrentChange"
                          :current-page.sync="currentPage1"
                          :page-size="5"
                          layout="total, prev, pager, next"
                          :total="total"
                        >
                        </el-pagination>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
            <div class="testpaper-main-paging"></div>
          </div>
        </el-main>
      </el-container>
    </div>
    <!-- <Floor></Floor> -->
  </div>
</template>

<script>
// import Vue from 'vue'
import "../css/testpaper.css";
import "../css/public.css";

export default {
  name: "WorkspaceJsonTestpaper",

  data() {
    return {
      options: [
        {
          value: "c",
          label: "c",
        },
        {
          value: "java",
          label: "java",
        },
        {
          value: "python",
          label: "python",
        },
        {
          value: "前端",
          label: "前端",
        },
      ],
      value: [],
      updateTitlea: "",
      imgvaluepather: "上传试卷图片",
      formLabelWidth: "120px",
      //  options: [],
      // value: [],
      list: [],
      loading: false,
      // states: ["语文",'数学','英语','政治','c语言'],
      testpaper: {
        title: "",
        paperimg: "",
        tag: "",
        userId: "",
      },
      testpapervalue: false,
      state1: "",
      usertestpapernew: {},
      officaltestpaper: {},
      testpaperold: {},
      total: 1,
      currentPage1: 1,
      currentPage2: 5,
      currentPage3: 5,
      currentPage4: 4,
      testpaper_first: "",
    };
  },
  beforeMount() {
    // console.log(this)
  },
  mounted() {
    //       this.list = this.states.map(item => {
    //     return { value: `${item}`, label: `${item}` };
    //   });
    var that = this;
    this.restaurants = this.loadAll();
    console.log(this);
    this.$http({
      url: "http://localhost:3001/testpaper/papersearchall",
      methods: "get",
    })
      .then((res) => {
        console.log(res.data.data);
        this.testpaperold = res.data.data;
      })
      .catch((err) => {
        console.log(err);
      });

    //  for(i=0;i<=tag.length-1;i++){

    //     tag[i].onclick = function(){
    //          for(var j=0;j<=diva.length-1;j++){
    //     diva[j].className = "none";
    //     diva[j].setAttribute("index",j+1)
    //     console.log(this.getAttribute("index"))
    //     if(this.getAttribute("index") == diva[j].getAttribute('index')){
    //         diva[j].style.display="block";
    //         console.log(this)
    //     }else{
    //         diva[j].style.display="none"
    //     }
    // }
    //     }
    //  }

    // let li = document.querySelector('.transform-inside-information-header-left-ul').querySelectorAll('li')
    // let diva = document.querySelector('.tab-all').querySelectorAll('.tab-1')
    const btn = document.querySelectorAll("#btn");

    let i;
    let font;
    for (i = 0; i <= btn.length - 1; i++) {
      btn[i].onclick = function () {
        //   console.log(this.innerText)
        font = this.innerText;
        that
          .$http({
            url: "http://localhost:3001/users/thenewpaper",
            methods: "get",
            params: {
              font: font,
            },
          })
          .then((res) => {
            console.log(res),
              (that.total = res.data.length),
              (that.testpaperold = res.data);
          })
          .catch((err) => {
            console.log(err), alert("错误");
          });
        for (i = 0; i <= btn.length - 1; i++) {
          btn[i].className = "";
          this.className = "active";
        }
        // for(var j=0;j<=diva.length-1;j++){
        //     diva[j].className = "none";
        //     diva[j].setAttribute("index",j+1)

        //     if(this.value == diva[j].getAttribute('index')){
        //         diva[j].style.display="block";

        //     }else{
        //         diva[j].style.display="none"
        //     }
        // }
      };
    }
  },

  methods: {
    father(e) {
      console.log("e", e);
      this.updateTitlea = e.data;
      console.log(this.value);
    },
    testpapervaluea() {
      (this.testpapervalue = false), console.log("tag", this.tag);
      console.log("1111111", this.testpaper);
      this.testpaper.img = this.updateTitlea;

      this.testpaper.userId = this.$cookies.get("userId");
      this.$http
        .post(
          //请求的url
          "http://localhost:3001/testpaper/inserttextpaper",
          //请求参数，不能以get请求方式写：{params: {userName: "root123", passWord: "root123"}}
          this.testpaper,
          //解决跨域问题，不加无法跨域
          { emulateJSON: true }
        )
        .then((res) => {
          console.log(res),
            this.$message.success(res.data.mes),
            window.location.reload();
        })
        .catch((err) => {
          console.log(err);
        });
    },
    uploadtestpaper() {
      this.testpapervalue = true;
    },
    remoteMethod(query) {
      if (query !== "") {
        this.loading = true;
        setTimeout(() => {
          this.loading = false;
          this.options = this.list.filter((item) => {
            return item.label.toLowerCase().indexOf(query.toLowerCase()) > -1;
          });
        }, 200);
      } else {
        this.options = [];
      }
    },
    testtitle(item) {
      // this.$router.push({
      //   path: "testpapercontent",
      //   query: {
      //     title,
      //   },
      // });
      //    console.log(this.$route.query.title);
      const link = document.createElement("a");
      // 这里是将链接地址url转成blob地址，
      fetch(item.url)
        .then((res) => res.blob())
        .then((blob) => {
          link.href = URL.createObjectURL(blob);
          // 下载文件的名称及文件类型后缀
          link.download = "test.JPG";
          document.body.appendChild(link);
          link.click();
          //在资源下载完成后 清除 占用的缓存资源
          window.URL.revokeObjectURL(link.href);
          document.body.removeChild(link);
        });
    },
    querySearch(queryString, cb) {
      var restaurants = this.restaurants;
      var results = queryString
        ? restaurants.filter(this.createFilter(queryString))
        : restaurants;
      // 调用 callback 返回建议列表的数据
      cb(results);
    },
    createFilter(queryString) {
      return (restaurant) => {
        return (
          restaurant.value.toLowerCase().indexOf(queryString.toLowerCase()) ===
          0
        );
      };
    },
    loadAll() {
      return [
        { value: "python" },
        { value: "java" },
        { value: "前端" },
        { value: "c++" },
        { value: "c" },
      ];
    },
    handleSelect(item) {
      console.log(item);
      this.$http({
        methods: "get",
        url: "http://localhost:3001/users/searchpapervaluetag",
        params: {
          tag: this.state1,
        },
      })
        .then((res) => {
          console.log(res), (this.testpaperold = res.data);
        })
        .catch((err) => {
          console.log(err);
        });
    },
    searchpapervalue() {
      this.$http({
        methods: "get",
        url: "http://localhost:3001/users/searchpapervalue",
        params: {
          paper_tag: this.testpaper_first,
        },
      }).then((res) => {
        console.log(res), (this.testpaperold = res.data);
      });
    },
    handleSizeChange(val) {
      console.log(`每页 ${val} 条`);
    },
    handleCurrentChange(val) {
      console.log(`当前页: ${val}`);
      this.$http({
        methods: "",
        url: "http://localhost:3001/users/papersearchsome",
        params: {
          num: `${val}`,
        },
      })
        .then((res) => {
          console.log(res), (this.testpaperold = res.data);
        })
        .catch((err) => {
          console.log(err);
        });
      this.$http({
        methods: "",
        url: "http://localhost:3001/users/officialpapersearch",
        params: {
          num: `${val}`,
        },
      })
        .then((res) => {
          console.log(res);
          this.officaltestpaper = res.data;
        })
        .catch((err) => {
          console.log(err);
        });
      this.$http({
        methods: "",
        url: "http://localhost:3001/users/userpapersearch",
        params: {
          num: `${val}`,
        },
      })
        .then((res) => {
          console.log(res);
          this.usertestpapernew = res.data;
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>

<style lang="css" scoped>
a {
  text-decoration: none;
}
</style>