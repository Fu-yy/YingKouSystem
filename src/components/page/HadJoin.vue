<template>
    <div>
        <el-row :gutter="20" style="margin:auto;margin-top:10px">
            <el-col :span="24">
                <el-tabs type="border-card">
                    <el-tab-pane label="已排入板坯信息">
                        <el-row :gutter="20" style="margin:auto;margin-top:10px">
                            <el-col :span="24">
                                <el-card shadow="hover">
                                    <el-table
                                        :data="tableData3"
                                        ref="multipleTable"
                                        height="250"
                                        border
                                        @selection-change="handleSelectionChange"
                                        style="width: 100%"
                                        :default-sort="{prop: 'type'}"
                                    >
                                        <el-table-column type="selection" sortable></el-table-column>
                                        <el-table-column prop="long" label="坯长加尺" sortable></el-table-column>
                                        <el-table-column prop="type" label="坯型" sortable></el-table-column>
                                        <el-table-column prop="mold_thickness" label="模厚" sortable></el-table-column>
                                        <el-table-column prop="mold_width" label="模宽" sortable></el-table-column>
                                        <el-table-column prop="thickness" label="板坯厚度" sortable></el-table-column>
                                        <el-table-column prop="slabwidth" label="板坯宽度" sortable></el-table-column>
                                        <el-table-column prop="min_long" label="长度下限" sortable></el-table-column>
                                        <el-table-column prop="max_long" label="长度上限" sortable></el-table-column>
                                        <el-table-column prop="max_width" label="最大宽度" sortable></el-table-column>
                                        <el-table-column prop="min_width" label="最小宽度" sortable></el-table-column>
                                        <el-table-column prop="max_thick" label="最大厚度" sortable></el-table-column>
                                        <el-table-column prop="min_thick" label="最小厚度" sortable></el-table-column>
                                        <el-table-column prop="is_normal" label="是否常用" sortable></el-table-column>
                                    </el-table>
                                </el-card>
                            </el-col>
                        </el-row>
                    </el-tab-pane>
                    <el-tab-pane label="未排入合同信息">
                        <el-row :gutter="20" style="margin:auto;margin-top:10px">
                            <el-col :span="24">
                                <el-card shadow="hover">
                                    <el-table
                                        :data="tableData4"
                                        ref="multipleTable"
                                        height="250"
                                        border
                                        @selection-change="handleSelectionChange"
                                        style="width: 100%"
                                        :default-sort="{prop: 'type'}"
                                    >
                                        <el-table-column type="selection" sortable></el-table-column>
                                        <el-table-column prop="long" label="坯长加尺" sortable></el-table-column>
                                        <el-table-column prop="type" label="坯型" sortable></el-table-column>
                                        <el-table-column prop="mold_thickness" label="模厚" sortable></el-table-column>
                                        <el-table-column prop="mold_width" label="模宽" sortable></el-table-column>
                                        <el-table-column prop="thickness" label="板坯厚度" sortable></el-table-column>
                                        <el-table-column prop="slabwidth" label="板坯宽度" sortable></el-table-column>
                                        <el-table-column prop="min_long" label="长度下限" sortable></el-table-column>
                                        <el-table-column prop="max_long" label="长度上限" sortable></el-table-column>
                                        <el-table-column prop="max_width" label="最大宽度" sortable></el-table-column>
                                        <el-table-column prop="min_width" label="最小宽度" sortable></el-table-column>
                                        <el-table-column prop="max_thick" label="最大厚度" sortable></el-table-column>
                                        <el-table-column prop="min_thick" label="最小厚度" sortable></el-table-column>
                                        <el-table-column prop="is_normal" label="是否常用" sortable></el-table-column>
                                    </el-table>
                                </el-card>
                            </el-col>
                        </el-row>
                    </el-tab-pane>
                </el-tabs>
            </el-col>
        </el-row>
        <el-row :gutter="20" >
            <el-col :span="24">
                <el-row :gutter="20" style="margin:auto;margin-top:10px">
                    <el-col :span="24">
                        <el-card shadow="hover">
                            <el-table
                                :data="tableData3"
                                ref="multipleTable"
                                height="250"
                                border
                                @selection-change="handleSelectionChange"
                                style="width: 100%"
                                :default-sort="{prop: 'type'}"
                            >
                                <el-table-column type="selection" sortable></el-table-column>
                                <el-table-column prop="long" label="坯长加尺" sortable></el-table-column>
                                <el-table-column prop="type" label="坯型" sortable></el-table-column>
                                <el-table-column prop="mold_thickness" label="模厚" sortable></el-table-column>
                                <el-table-column prop="mold_width" label="模宽" sortable></el-table-column>
                                <el-table-column prop="thickness" label="板坯厚度" sortable></el-table-column>
                                <el-table-column prop="slabwidth" label="板坯宽度" sortable></el-table-column>
                                <el-table-column prop="min_long" label="长度下限" sortable></el-table-column>
                                <el-table-column prop="max_long" label="长度上限" sortable></el-table-column>
                                <el-table-column prop="max_width" label="最大宽度" sortable></el-table-column>
                                <el-table-column prop="min_width" label="最小宽度" sortable></el-table-column>
                                <el-table-column prop="max_thick" label="最大厚度" sortable></el-table-column>
                                <el-table-column prop="min_thick" label="最小厚度" sortable></el-table-column>
                                <el-table-column prop="is_normal" label="是否常用" sortable></el-table-column>
                            </el-table>
                        </el-card>
                    </el-col>
                </el-row>
            </el-col>
        </el-row>
    </div>
</template>

<script>
export default {
    name: 'hasJoin',
    data(){
        return{
             tableData3: [
                {
                    type: '01',
                    long: '30',
                    mold_thickness: '167',
                    mold_width: '1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long: '2400',
                    max_long: '4730',
                    max_width: '999999',
                    min_width: '0',
                    max_thick: '9999',
                    min_thick: '0',
                    is_normal: '0'
                },
                {
                    type: '01',
                    long: '30',
                    mold_thickness: '167',
                    mold_width: '1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long: '2400',
                    max_long: '4730',
                    max_width: '999999',
                    min_width: '0',
                    max_thick: '9999',
                    min_thick: '0',
                    is_normal: '0'
                },
                {
                    type: '01',
                    long: '30',
                    mold_thickness: '167',
                    mold_width: '1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long: '2400',
                    max_long: '4730',
                    max_width: '999999',
                    min_width: '0',
                    max_thick: '9999',
                    min_thick: '0',
                    is_normal: '0'
                },
                {
                    type: '01',
                    long: '30',
                    mold_thickness: '167',
                    mold_width: '1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long: '2400',
                    max_long: '4730',
                    max_width: '999999',
                    min_width: '0',
                    max_thick: '9999',
                    min_thick: '0',
                    is_normal: '0'
                },
                {
                    type: '01',
                    long: '30',
                    mold_thickness: '167',
                    mold_width: '1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long: '2400',
                    max_long: '4730',
                    max_width: '999999',
                    min_width: '0',
                    max_thick: '9999',
                    min_thick: '0',
                    is_normal: '0'
                },
                {
                    type: '01',
                    long: '30',
                    mold_thickness: '167',
                    mold_width: '1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long: '2400',
                    max_long: '4730',
                    max_width: '999999',
                    min_width: '0',
                    max_thick: '9999',
                    min_thick: '0',
                    is_normal: '0'
                },
                {
                    type: '01',
                    long: '30',
                    mold_thickness: '167',
                    mold_width: '1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long: '2400',
                    max_long: '4730',
                    max_width: '999999',
                    min_width: '0',
                    max_thick: '9999',
                    min_thick: '0',
                    is_normal: '0'
                },
                {
                    type: '02',
                    long: '30',
                    mold_thickness: '167',
                    mold_width: '1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long: '2400',
                    max_long: '4730',
                    max_width: '999999',
                    min_width: '0',
                    max_thick: '9999',
                    min_thick: '0',
                    is_normal: '0'
                },
                {
                    type: '03',
                    long: '30',
                    mold_thickness: '167',
                    mold_width: '1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long: '2400',
                    max_long: '4730',
                    max_width: '999999',
                    min_width: '0',
                    max_thick: '9999',
                    min_thick: '0',
                    is_normal: '0'
                },
                {
                    type: '04',
                    long: '30',
                    mold_thickness: '167',
                    mold_width: '1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long: '2400',
                    max_long: '4730',
                    max_width: '999999',
                    min_width: '0',
                    max_thick: '9999',
                    min_thick: '0',
                    is_normal: '0'
                },
                {
                    type: '05',
                    long: '30',
                    mold_thickness: '167',
                    mold_width: '1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long: '2400',
                    max_long: '4730',
                    max_width: '999999',
                    min_width: '0',
                    max_thick: '9999',
                    min_thick: '0',
                    is_normal: '0'
                },
                {
                    type: '06',
                    long: '30',
                    mold_thickness: '167',
                    mold_width: '1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long: '2400',
                    max_long: '4730',
                    max_width: '999999',
                    min_width: '0',
                    max_thick: '9999',
                    min_thick: '0',
                    is_normal: '0'
                },
                {
                    type: '07',
                    long: '30',
                    mold_thickness: '167',
                    mold_width: '1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long: '2400',
                    max_long: '4730',
                    max_width: '999999',
                    min_width: '0',
                    max_thick: '9999',
                    min_thick: '0',
                    is_normal: '0'
                }
            ],
            tableData4: [
                {
                    type: '999',
                    long: '20',
                    mold_thickness: '167',
                    mold_width: '5',
                    thickness: '250',
                    slabwidth: '20',
                    min_long: '2400',
                    max_long: '4730',
                    max_width: '90',
                    min_width: '0',
                    max_thick: '9999',
                    min_thick: '0',
                    is_normal: '0'
                },
                {
                    type: '02',
                    long: '71',
                    mold_thickness: '167',
                    mold_width: '1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long: '2400',
                    max_long: '4730',
                    max_width: '82',
                    min_width: '0',
                    max_thick: '9999',
                    min_thick: '0',
                    is_normal: '0'
                },
                {
                    type: '90',
                    long: '30',
                    mold_thickness: '167',
                    mold_width: '1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long: '2400',
                    max_long: '4730',
                    max_width: '999999',
                    min_width: '0',
                    max_thick: '9999',
                    min_thick: '0',
                    is_normal: '0'
                },
                {
                    type: '80',
                    long: '30',
                    mold_thickness: '167',
                    mold_width: '1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long: '2400',
                    max_long: '4730',
                    max_width: '999999',
                    min_width: '0',
                    max_thick: '9999',
                    min_thick: '0',
                    is_normal: '0'
                },
                {
                    type: '70',
                    long: '30',
                    mold_thickness: '167',
                    mold_width: '1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long: '2400',
                    max_long: '4730',
                    max_width: '999999',
                    min_width: '0',
                    max_thick: '9999',
                    min_thick: '0',
                    is_normal: '0'
                },
                {
                    type: '60',
                    long: '30',
                    mold_thickness: '167',
                    mold_width: '1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long: '2400',
                    max_long: '4730',
                    max_width: '999999',
                    min_width: '0',
                    max_thick: '9999',
                    min_thick: '0',
                    is_normal: '0'
                },
                {
                    type: '20',
                    long: '30',
                    mold_thickness: '167',
                    mold_width: '1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long: '2400',
                    max_long: '4730',
                    max_width: '999999',
                    min_width: '0',
                    max_thick: '9999',
                    min_thick: '0',
                    is_normal: '0'
                },
                {
                    type: '50',
                    long: '30',
                    mold_thickness: '167',
                    mold_width: '1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long: '2400',
                    max_long: '4730',
                    max_width: '999999',
                    min_width: '0',
                    max_thick: '9999',
                    min_thick: '0',
                    is_normal: '0'
                },
                {
                    type: '40',
                    long: '30',
                    mold_thickness: '167',
                    mold_width: '1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long: '2400',
                    max_long: '4730',
                    max_width: '999999',
                    min_width: '0',
                    max_thick: '9999',
                    min_thick: '0',
                    is_normal: '0'
                },
                {
                    type: '30',
                    long: '30',
                    mold_thickness: '167',
                    mold_width: '1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long: '2400',
                    max_long: '4730',
                    max_width: '999999',
                    min_width: '0',
                    max_thick: '9999',
                    min_thick: '0',
                    is_normal: '0'
                },
                {
                    type: '20',
                    long: '30',
                    mold_thickness: '167',
                    mold_width: '1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long: '2400',
                    max_long: '4730',
                    max_width: '999999',
                    min_width: '0',
                    max_thick: '9999',
                    min_thick: '0',
                    is_normal: '0'
                },
                {
                    type: '21',
                    long: '30',
                    mold_thickness: '167',
                    mold_width: '1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long: '2400',
                    max_long: '4730',
                    max_width: '999999',
                    min_width: '0',
                    max_thick: '9999',
                    min_thick: '0',
                    is_normal: '0'
                },
                {
                    type: '23',
                    long: '30',
                    mold_thickness: '167',
                    mold_width: '1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long: '2400',
                    max_long: '4730',
                    max_width: '999999',
                    min_width: '0',
                    max_thick: '9999',
                    min_thick: '0',
                    is_normal: '0'
                }
            ]
        }
    }
};
</script>

<style>
</style>