<template>
    <div>
        <div class="header">
            已发货订单
        </div>
        <div class="body">
            <el-table :data="tableData" style="width: 100%" class="table" border>
                <el-table-column prop="order_id" label="订单号" width="100" align="center">
                </el-table-column>
                
                <el-table-column prop="order_way" label="订购方式" width="100" align="center">
                </el-table-column>
                <el-table-column prop="cons_name" label="收件人姓名" width="100" align="center">
                </el-table-column>
                <el-table-column prop="cons_addre" label="收件地址" width="150" align="center">
                </el-table-column>
                <el-table-column prop="disp_id" label="送货员编号" width="120" align="center">
                </el-table-column>
                <el-table-column prop="disp_phone" label="送货员电话" width="120" align="center">
                </el-table-column>
                <el-table-column prop="deliver_time" label="预计送达时间" width="116" align="center">
                </el-table-column>
            </el-table>


        </div>
    </div>
</template>

<script>
export default {
    created() {
        this.getdata()
    },
    data() {
        return {
            tableData: [],
        }
    },
    methods: {
        getdata() {
            this.$axios.get("/api/user/sending").then((res) => {
                console.log(res.data);
                if (res.data.status == 200) {
                    this.tableData = res.data.tabledata;
                }
            })
        }
    }

}
</script>

<style scoped>
.header {
    width: 100%;
    height: 10%;
    text-align: center;
    line-height: 64px;
    font-size: 20px;
    font-weight: 800;
    border-bottom: 1px solid #e3e3e3;
}

.body {

    width: 68%;
    margin: auto;
    margin-top: 30px;
}
</style>