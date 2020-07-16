<template>
    <van-address-edit
            :area-list="areaList"
            show-delete
            @save="onSave"
            @delete="onDelete"
    />
</template>

<script>
    import AreaList from '../api/area';
    import { Toast } from 'vant';
    export default {
        name: "AddressNew",
        data() {
            return {
                areaList: AreaList
            }
        },
        methods: {
            onSave(item) {
                const _this = this
                axios.post('http://120.0.0.1:1636/address/address',item).then(function (resp) {
                    if(resp.data.code == 0){
                        let instance = Toast('添加成功');
                        setTimeout(() => {
                            instance.close();
                            _this.$router.push('/addressList')
                        }, 1000)
                    }
                })
            },
            onDelete() {
                history.go(-1)
            }
        }
    }
</script>

<style scoped>

</style>
