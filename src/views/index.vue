<style scoped lang="less">
.layout {
  background: #f5f7f9;
  position: relative;
  border-radius: 4px;
  overflow: hidden;
  height: 100%;
}
.layout-logo {
  width: 100px;
  height: 30px;
  background: #5b6270;
  border-radius: 3px;
  float: left;
  position: relative;
  top: 15px;
  left: 20px;
}
.layout-nav {
  width: 420px;
  margin: 0 auto;
  margin-right: 20px;
}
</style>
<template>
  <div class="layout">
    <Layout :style="{minHeight:'100vh'}">
      <header>
        <Menu mode="horizontal" theme="dark" active-name="1">
          <div class="layout-logo"></div>
          <div class="layout-nav">
            <MenuItem name="1">
              <Icon type="ios-navigate"></Icon>Item1
            </MenuItem>
            <MenuItem name="2">
              <Icon type="ios-keypad"></Icon>Item2
            </MenuItem>
            <MenuItem name="3">
              <Icon type="ios-analytics"></Icon>Item3
            </MenuItem>
            <MenuItem name="4">
              <Icon type="ios-paper"></Icon>Item4
            </MenuItem>
          </div>
        </Menu>
      </header>
      <Layout>
        <Sider hide-tigger :style="{background:'#fff'}">
          <Menu
            :active-name="activeName"
            theme="light"
            width="auto"
            :open-names="openNames"
            @on-select="handleSelect"
            :accordion="true"
          >
            <template v-for="(item, index) in items">
              <side-menu-item
                :parent-item="item"
                v-if="item.children&&item.children.length!==0"
                :name="index+''"
                :index="index"
                v-bind:key="index"
              ></side-menu-item>
              <menu-item v-else :name="index+''" :to="item.path" v-bind:key="index">
                <Icon :type="item.icon" :size="15" />
                <span>{{item.title}}</span>
              </menu-item>
            </template>
          </Menu>
        </Sider>
        <Layout :style="{padding: '0 24px 24px'}">
          <Breadcrumb :style="{margin: '24px 0'}">
            <BreadcrumbItem>Home</BreadcrumbItem>
            <BreadcrumbItem>Components</BreadcrumbItem>
            <BreadcrumbItem>Layout</BreadcrumbItem>
          </Breadcrumb>
          <Content :style="{padding:'24px',minHeight:'280px',background:'#fff'}">
            <div></div>
          </Content>
        </Layout>
      </Layout>
    </Layout>
  </div>
</template>
<script>
import sideMenuItem from "./components/Menu/side-menu-item";
export default {
  name: "sideMenu",
  props: {
    activeName: {
      type: String,
      default: "auth"
    },
    openNames: {
      type: Array,
      default: () => ["other", "role", "auth"]
    },
    items: {
      type: Array,
      default: []
    }
  },
  data() {
    return {
      menus: [
        {
          name: "system",
          title: "数据看板",
          icon: "ios-analytics",
          children: [
            {
              name: "user",
              title: "用户管理",
              icon: "outlet",
              children: [
                { name: "auth", title: "权限管理1", icon: "outlet" },
                {
                  name: "auth",
                  title: "权限管理",
                  icon: "outlet",
                  children: [
                    { name: "334", title: "子菜单", icon: "outlet" },
                    { name: "453", title: "子菜单", icon: "outlet" }
                  ]
                }
              ]
            }
          ]
        },
        {
          name: "other",
          title: "其他管理",
          icon: "outlet"
        }
      ]
    };
  },
  components: {
    sideMenuItem
  },
  computed:{
      
  },
  methods: {
    handleSelect(name) {
      this.$emit("on-select", name);
    }
  }
};
</script>
