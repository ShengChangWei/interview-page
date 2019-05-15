<style src="./lib/highlight/styles/atom-one-light.css"></style>
<style>
html,
body {
  height: 100%;
  margin: 0;
}
.page-wrapper {
  background: #f1f4f9;
  padding: 1rem 4rem 4rem 4rem;
}
.ex-header {
  display: flex;
  height: 4rem;
  width: 100%;
  padding: 0 3rem;
  z-index: 999;
  background: #2db7f5;
  box-sizing: border-box;
}
.ex-header-logo {
  padding-top: 0.5rem;
  width: 12rem;
}
.ex-header-logo-img {
  display: none;
  height: 2rem;
  margin: 1rem 1rem 0 0;
}
.ex-header-logo-text {
  color: #fff;
  font-size: 1.5rem;
  font-weight: 700;
  line-height: 3rem;
}
.ex-header-nav {
  display: flex;
  justify-content: flex-end;
  width: 100%;
}
.ex-header-nav-item {
  color: #fff;
  text-align: center;
  font-size: 0.9rem;
  line-height: 3.9rem;
  min-width: 4rem;
  cursor: pointer;
}
.ex-header-nav-item.active,
.ex-header-nav-item:hover {
  color: #fff;
  border-bottom: 0.2rem solid #fff;
}
.container {
  position: relative;
  display: flex;
  height: 100%;
  background: #fff;
  box-sizing: border-box;
  overflow-x: hidden;
}
.sidebar {
  width: 15rem;
  height: 100%;
  margin-bottom: 5rem;
  background-color: #fff;
  flex-shrink: 0;
}
.content {
  min-width: 40rem;
  height: 100%;
  padding: 1rem;
  background: #fff;
  border-left: 1px solid #f7f7f7;
}
.ex-container {
  display: flex;
}
.ex-menu-container {
  min-height: 40rem;
}
.ex-menu-item {
  position: relative;
  cursor: pointer;
}
.ex-menu-title-container {
  font-size: 1rem;
  padding: 1rem 1.5rem;
}
.ex-menu-sub-title,
.ex-sub-menu-sub-title {
  color: #666;
  opacity: 0.67;
}
.ex-menu-title:hover,
.ex-sub-menu-item:hover {
  background: #eaf8fe;
}
.ex-sub-menu-item {
  padding: 1rem 2rem;
  font-size: 0.8rem;
  cursor: pointer;
}
.ex-menu-title-arrow {
  position: absolute;
  font-size: 0.5rem;
  right: 1rem;
  top: 1.25rem;
  transform: rotate(0);
  transition: transform 0.2s ease;
}
.ex-menu-item.open .ex-menu-title-arrow {
  transform: rotate(180deg);
}
.ex-sub-menu-item.active {
  color: #2db7f5;
}
.ex-card {
  margin: 2rem 1rem;
}
.ex-menu-group-title {
    color: #2db7f5;
    font-size: 0.9rem;
    padding-left: 1.5rem;
}
.show-slider {
  display: none;
  position: fixed;
  font-size: 2rem;
  z-index: 3;
  color: #fff;
  width: 4rem;
  text-align: center;
  height: 4rem;
  line-height: 4rem;
  top: 0;
  right: 0;
}
.ex-footer {
  display: flex;
  padding: 2rem 4rem 5rem 4rem;
  background-color: #67cdfb;
}
.ex-footer-nav {
  display: flex;
  width: 50%;
}
.ex-footer-info {
  color: #fff;
  font-size: 0.8rem;
  width: 50%;
  text-align: right;
}
.ex-footer-nav-item {
  flex: 1;
}
.ex-footer-nav-title {
  color: #fff;
}
.ex-footer-nav-link {
  font-size: 0.8rem;
  margin: 0.25rem 0;
}
.ex-footer-nav-link-a {
  color: #fff;
}
.ex-footer-nav-link-description {
  color: #fff;
}
.demo-content {
  width: 20rem;
}
.slide-left-transition {
  transition: transform 0.3s ease;
  transform: translateX(0);
}
.slide-left-enter,
.slide-left-leave {
  transform: translateX(-100%);
}
@media screen and (max-width: 1000px) {
  .ex-header {
    padding: 0 1rem;
    position: fixed;
  }
  .page-wrapper {
    padding: 0;
  }
  .container {
    padding-left: 0;
  }
  .content {
    min-width: initial;
    padding: 4rem 1rem;
    box-sizing: border-box;
    overflow: hidden;
  }
  .show-slider {
    display: inline-block;
    width: 4rem;
    text-align: center;
    height: 4rem;
    line-height: 4rem;
    top: 0;
    right: 0;
  }
  .sidebar {
    position: fixed;
    z-index: 1000;
    top: 0;
    overflow-y: auto;
  }
  .ex-header-nav {
    display: none;
  }
  .ex-footer {
    padding: 0.5rem 1rem;
    font-size: 0.8rem;
    flex-wrap: wrap;
  }
  .ex-footer-nav {
    width: 100%;
  }
  .ex-footer-nav-item {
    text-align: center;
  }
  .ex-footer-info {
    width: 100%;
    text-align: center;
  }
  .ex-footer-nav-link {
    font-size: 0.6rem;
  }
}
</style>
<template>
    <div>
        <header class="ex-header">
            <a v-link="{ path: '/' }">
                <div class="ex-header-logo">
                    <span class="ex-header-logo-text">圣墨</span>
                </div>
            </a>
            <div class="show-slider" @click="sliderShow = !sliderShow">
                <span class="ion-navicon"></span>
            </div>
            <nav class="ex-header-nav">
                <a v-for="item in header.nav" v-link="item.route">
                    <div class="ex-header-nav-item" :class="{ 'active': item.active }">
                        <span class="ex-header-nav-text">{{item.title}}</span>
                    </div>
                </a>
                 <a  href="https://github.com/ShengChangWei?tab=repositories" target="_blank">
                    <div class="ex-header-nav-item" >
                        <span class="ex-header-nav-text">github</span>
                    </div>
                </a>
               
            </nav>
        </header>
        <div class="page-wrapper">
            <div class="container">
                <div class="sidebar" v-show="sliderShow" transition="slide-left">
                    <div class="ex-menu-container">
                        <menu :menu="menu" @click="mobileClick"></menu>
                    </div>
                </div>
                <div class="content">
                    <router-view></router-view>
                </div>
                <rd-modal></rd-modal>
                <rd-notification></rd-notification>
                <rd-preview></rd-preview>
                <rd-loadingbar></rd-loadingbar>
            </div>
        </div>
        <footer class="ex-footer">
            <nav class="ex-footer-nav">
                <div class="ex-footer-nav-item" v-for="item in footer.nav">
                    <span class="ex-footer-nav-title">{{item.title}}</span>
                    <div class="ex-footer-nav-link" v-for="link in item.links">
                        <a class="ex-footer-nav-link-a" :href="link.link">{{link.title}}</a>
                        <span class="ex-footer-nav-link-description">{{link.sub}}</span>
                    </div>
                </div>
            </nav>
            <div class="ex-footer-info">
                <p>©2019 圣墨出品，必属精品</p>
            </div>
        </footer>
    </div>

</template>
<script>
import Menu from "./components/menu.vue";

export default {
  data() {
    return {
      sliderShow: document.body.offsetWidth > 1000,
      menu: [
        {
          title: "前端面试宝典",
          link: "/"
        },
         {
          title: "一、前言",
          link: "/",
          showSub: true,
          group: true,
         },
        {
          title: "二、前端三剑客",
          link: "form",
          showSub: true,
          group: true,
          subMenu: [
            {
              title: "1、基础部分",
              group: [
                {
                  title: "1.1 技术起源理论题",
                  subTitle: "",
                  link: "basic/drop-button"
                },
                {
                  title: "1.2 Html4/5 常见问题",
                  subTitle: "",
                  link: "basic/tag"
                },
                {
                  title: "1.3 Css2/3",
                  subTitle: "",
                  link: "basic/table"
                },
                {
                  title: "1.4 javascript",
                  subTitle: "",
                  link: "basic/card"
                }
              ]
            },
            // {
            //   title: "css",
            //   group: [
            //     {
            //       title: "Checkbox",
            //       subTitle: "多选框",
            //       link: "form/checkbox"
            //     },
            //     {
            //       title: "Radio",
            //       subTitle: "单选框",
            //       link: "form/radio"
            //     },
            //     {
            //       title: "Textfield",
            //       subTitle: "输入框",
            //       link: "form/textfield"
            //     },
            //     {
            //       title: "Number",
            //       subTitle: "数字输入框",
            //       link: "form/number"
            //     },
            //     {
            //       title: "Switch",
            //       subTitle: "开关",
            //       link: "form/switch"
            //     },
            //     {
            //       title: "Slider",
            //       subTitle: "滑动输入",
            //       link: "form/slider"
            //     },
            //     {
            //       title: "Datepicker",
            //       subTitle: "日期选择",
            //       link: "form/datepicker"
            //     },
            //     {
            //       title: "Select",
            //       subTitle: "选择器",
            //       link: "form/select"
            //     },
            //     {
            //       title: "Cascader",
            //       subTitle: "级联选择器",
            //       link: "form/cascader"
            //     },
            //     {
            //       title: "AutoSearch",
            //       subTitle: "查找输入内容",
            //       link: "form/autosearch"
            //     }
            //   ]
            // },
            // {
            //   title: "javascript",
            //   group: [
            //     {
            //       title: "Alert",
            //       subTitle: "警告提示",
            //       link: "common/alert"
            //     },
            //     {
            //       title: "Timeline",
            //       subTitle: "时间线",
            //       link: "common/timeline"
            //     },
            //     {
            //       title: "Tooltip",
            //       subTitle: "提示框",
            //       link: "common/tooltip"
            //     },
            //     {
            //       title: "Spin",
            //       subTitle: "加载中",
            //       link: "common/spin"
            //     },
            //     {
            //       title: "Upload",
            //       subTitle: "上传",
            //       link: "common/upload"
            //     },
            //     {
            //       title: "AudioPlayer",
            //       subTitle: "音频播放器",
            //       link: "common/audio"
            //     },
            //     {
            //       title: "Progress",
            //       subTitle: "进度条",
            //       link: "common/progress"
            //     },
            //     {
            //       title: "Tree",
            //       subTitle: "树选择",
            //       link: "common/tree"
            //     }
            //   ]
            // },
            // {
            //   title: "Global",
            //   group: [
            //     {
            //       title: "Modal",
            //       subTitle: "对话框",
            //       link: "global/modal"
            //     },
            //     {
            //       title: "Notification",
            //       subTitle: "通知",
            //       link: "global/notification"
            //     },
            //     {
            //       title: "Preview",
            //       subTitle: "图片预览",
            //       link: "global/preview"
            //     },
            //     {
            //       title: "LoadingBar",
            //       subTitle: "加载进度条",
            //       link: "global/loadingbar"
            //     }
            //   ]
            // },
            // {
            //   title: "Navigation",
            //   group: [
            //     {
            //       title: "Breadcrumb",
            //       subTitle: "面包屑",
            //       link: "navigation/breadcrumb"
            //     },
            //     {
            //       title: "Pagination",
            //       subTitle: "分页",
            //       link: "navigation/pagination"
            //     }
            //   ]
            // }
          ]
        },
         {
          title: "三、框架部分",
          link: "form",
          showSub: true,
          group: true,
          subMenu: [
            {
              title: "1、Vue",
              group: [
                {
                  title: "1.1 vue基础",
                  subTitle: "",
                  link: "form/checkbox"
                },
                // {
                //   title: "Radio",
                //   subTitle: "单选框",
                //   link: "form/radio"
                // },
                // {
                //   title: "Textfield",
                //   subTitle: "输入框",
                //   link: "form/textfield"
                // },
                // {
                //   title: "Number",
                //   subTitle: "数字输入框",
                //   link: "form/number"
                // },
                // {
                //   title: "Switch",
                //   subTitle: "开关",
                //   link: "form/switch"
                // },
                // {
                //   title: "Slider",
                //   subTitle: "滑动输入",
                //   link: "form/slider"
                // },
                // {
                //   title: "Datepicker",
                //   subTitle: "日期选择",
                //   link: "form/datepicker"
                // },
                // {
                //   title: "Select",
                //   subTitle: "选择器",
                //   link: "form/select"
                // },
                // {
                //   title: "Cascader",
                //   subTitle: "级联选择器",
                //   link: "form/cascader"
                // },
                // {
                //   title: "AutoSearch",
                //   subTitle: "查找输入内容",
                //   link: "form/autosearch"
                // }
              ]
            },
            // {
            //   title: "javascript",
            //   group: [
            //     {
            //       title: "Alert",
            //       subTitle: "警告提示",
            //       link: "common/alert"
            //     },
            //     {
            //       title: "Timeline",
            //       subTitle: "时间线",
            //       link: "common/timeline"
            //     },
            //     {
            //       title: "Tooltip",
            //       subTitle: "提示框",
            //       link: "common/tooltip"
            //     },
            //     {
            //       title: "Spin",
            //       subTitle: "加载中",
            //       link: "common/spin"
            //     },
            //     {
            //       title: "Upload",
            //       subTitle: "上传",
            //       link: "common/upload"
            //     },
            //     {
            //       title: "AudioPlayer",
            //       subTitle: "音频播放器",
            //       link: "common/audio"
            //     },
            //     {
            //       title: "Progress",
            //       subTitle: "进度条",
            //       link: "common/progress"
            //     },
            //     {
            //       title: "Tree",
            //       subTitle: "树选择",
            //       link: "common/tree"
            //     }
            //   ]
            // },
            // {
            //   title: "Global",
            //   group: [
            //     {
            //       title: "Modal",
            //       subTitle: "对话框",
            //       link: "global/modal"
            //     },
            //     {
            //       title: "Notification",
            //       subTitle: "通知",
            //       link: "global/notification"
            //     },
            //     {
            //       title: "Preview",
            //       subTitle: "图片预览",
            //       link: "global/preview"
            //     },
            //     {
            //       title: "LoadingBar",
            //       subTitle: "加载进度条",
            //       link: "global/loadingbar"
            //     }
            //   ]
            // },
            // {
            //   title: "Navigation",
            //   group: [
            //     {
            //       title: "Breadcrumb",
            //       subTitle: "面包屑",
            //       link: "navigation/breadcrumb"
            //     },
            //     {
            //       title: "Pagination",
            //       subTitle: "分页",
            //       link: "navigation/pagination"
            //     }
            //   ]
            // }
          ]
        }
      ],
      header: {
        nav: [
          {
            title: "首页",
            route: {
              name: "index"
            },
            active: true
          }
        ]
      },
      footer: {
        nav: [
          // {
          //   title: "源码",
          //   links: [
          //     {
          //       title: "仓库",
          //       link: "https://github.com/luojilab/radon-ui",
          //       sub: "- Github"
          //     }
          //   ]
          // },
          {
            title: "相关链接",
            links: [
              {
                title: "Vue.js",
                link: "http://vuejs.org/"
              },
              {
                title: "W3school",
                link: "http://www.w3school.com.cn/html/index.asp"
              },
              {
                title: "JavaScript教程",
                link: "https://www.liaoxuefeng.com/wiki/001434446689867b27157e896e74d51a89c25cc8b43bdb3000"
              }
            ]
          },
          {
            title: "联系圣墨",
            links: [
              {
                title: "QQ：2367896538",
              },
              {
                title: "tel：13661174052",
              },
            ]
          }
        ]
      },
      state: {
        timer: null
      }
    };
  },
  ready() {
    window.addEventListener("resize", this.resizeCheck);
  },
  components: {
    Menu
  },
  methods: {
    resizeCheck() {
      if (this.state.timer) {
        clearTimeout(this.state.timer);
        this.state.timer = null;
      }
      this.state.timer = setTimeout(() => {
        if (document.body.offsetWidth > 768) {
          this.sliderShow = true;
        }
      }, 200);
    },
    mobileClick() {
      if (document.body.offsetWidth < 768) {
        this.sliderShow = false;
      }
    }
  }
};
</script>
