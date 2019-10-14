<!--  -->
<style scoped lang="less">
</style>
<template>
    <Submenu :name="index+''">
        <template slot="title">
            <Icon :type="parentItem.icon" :size="10"/>
            <span>{{ parentItem.title }}</span>
        </template>
        <template v-for="(item,i) in parentItem.children">
            <side-menu-item
                v-if="item.children&&item.children.length!==0"
                :parent-item="item"
                :to="item.path"
                :name="index+'-'+i"
                :index="index+'-'+i"
                v-bind:key="i">
            </side-menu-item>
            <menu-item v-else
                :name="index+'-'+i" :to="item.path"
                v-bind:key="i">
                <Icon :type="item.icon" :size="15"/>
                <span>{{ item.title }}</span>
            </menu-item>
        </template>
    </Submenu>
</template>

<script>

export default {
    name:'sideMenuItem',
    props:{
        parentItem:{
            type:Object,
            default:() => {}
        },
        index:{}
    },
    created:function(){
        console.log(this.parentItem);
    }
}
</script>