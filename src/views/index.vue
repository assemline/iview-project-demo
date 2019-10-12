<style scoped lang="less">
.layout{
    background:#f5f7f9;
    position:relative;
    border-radius: 4px;
    overflow: hidden;
    height:100%;
}
.layout-logo{
    width:100px;
    height:30px;
    background:#5b6270;
    border-radius: 3px;
    float:left;
    position:relative;
    top:15px;
    left:20px;
}
.layout-nav{
    width:420px;
    margin:0 auto;
    margin-right:20px;
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
                            <Icon type="ios-navigate"></Icon>
                            Item1
                        </MenuItem>
                        <MenuItem name="2">
                            <Icon type="ios-keypad"></Icon>
                            Item2
                        </MenuItem>
                        <MenuItem name="3">
                            <Icon type="ios-analytics"></Icon>
                            Item3
                        </MenuItem>
                        <MenuItem name="4">
                            <Icon type="ios-paper"></Icon>
                            Item4
                        </MenuItem>
                    </div>
                </Menu>
            </header>
            <Layout>
                <Sider hide-tigger :style="{background:'#fff'}">
                    <Menu :active-name="activeName" theme="light" width="auto" :open-names="openNames"
                        @on-select="handleSelect" :accordion="true">
                        <Submenu name="1">
                            <template slot="title">
                                <Icon type="ios-navigate"></Icon>
                                Item 1
                            </template>
                            <MenuItem name="1-1">Option 1</MenuItem>
                            <MenuItem name="1-2">Option 2</MenuItem>
                            <MenuItem name="1-3">Option 3</MenuItem>
                        </Submenu>
                        <Submenu name="2">
                            <template slot="title">
                                <Icon type="ios-keypad"></Icon>
                                Item 2
                            </template>
                            <MenuItem name="2-1">Option 1</MenuItem>
                            <MenuItem name="2-2">Option 2</MenuItem>
                            <MenuItem name="2-3">Option 3</MenuItem>
                        </Submenu>
                        <Submenu name="3">
                            <template slot="title">
                                <Icon type="ios-analytics"></Icon>
                                Item 3
                            </template>
                            <MenuItem name="3-1">Option 1</MenuItem>
                            <MenuItem name="3-2">Option 2</MenuItem>
                            <MenuItem name="3-3">Option 3</MenuItem>
                        </Submenu>
                    </Menu>
                </Sider>
                <Layout :style="{padding: '0 24px 24px'}">
                    <Breadcrumb :style="{margin: '24px 0'}">
                        <BreadcrumbItem>Home</BreadcrumbItem>
                        <BreadcrumbItem>Components</BreadcrumbItem>
                        <BreadcrumbItem>Layout</BreadcrumbItem>
                    </Breadcrumb>
                    <Content :style="{padding:'24px',minHeight:'280px',background:'#fff'}">
                        <div>
                            
                        </div>
                    </Content>
                </Layout>
            </Layout>
        </Layout>
    </div>
</template>
<script>
    export default {
        data(){
            return {

            };
        },
        computed:{
            
        },
        methods:{

        }
    }
</script>
