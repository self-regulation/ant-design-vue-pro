<template>
    <div>
        <a-drawer placement="right" :closable="false" @close="onClose" :visible="visible" width="300px">
            <template v-slot:handle>
                <div class="handle" @click="visible = !visible">
                    <a-icon :type="visible?'close-circle':'setting'"></a-icon>
                </div>
            </template>
            <div>
                <h3>整体风格</h3>
                <a-radio-group :value="$route.query.navTheme || 'dark'"
                    @change="e => handleSettingChang('navTheme',e.target.value)">
                    <a-radio value="dark">黑色</a-radio>
                    <a-radio value="linght">白色</a-radio>
                </a-radio-group>
            </div>
            <div>
                <h3>导航风格</h3>
                <a-radio-group :value="$route.query.navLayout || 'left'"
                    @change="e => handleSettingChang('navLayout',e.target.value)">
                    <a-radio value="left">左侧</a-radio>
                    <a-radio value="top">顶部</a-radio>
                </a-radio-group>
            </div>
        </a-drawer>
    </div>
</template>
<script>
    export default {
        data() {
            return {
                visible: false,
            }
        },
        methods: {
            onClose() {
                this.visible = false
            },
            handleSettingChang(type, value) {
                this.$router.push({
                    query: {
                        ...this.$route,
                        [type]: value
                    }
                });
            }
        },
    }
</script>
<style scoped>
    .handle {
        position: absolute;
        top: 50%;
        right: 300px;
        width: 48px;
        height: 48px;
        background: #1980ff;
        color: #fff;
        text-align: center;
        line-height: 48px;
        border-radius: 5px;
    }
</style>