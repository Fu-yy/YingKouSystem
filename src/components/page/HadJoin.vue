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

                    <el-tab-pane label="厚板最大长度表维护">
                        <el-form :model="ruleForm2" status-icon ref="ruleForm2" label-width="130px">
                            <el-row :gutter="20">
                                <el-col :span="8">
                                    <el-form-item label="板材硬度下限" prop="lowerHardness">
                                        <el-input v-model.number="ruleForm2.lowerHardness"></el-input>
                                    </el-form-item>
                                </el-col>
                                <el-col :span="8">
                                    <el-form-item label="板材硬度上限" prop="upperHardness">
                                        <el-input v-model.number="ruleForm2.upperHardness"></el-input>
                                    </el-form-item>
                                </el-col>
                                <el-col :span="8">
                                    <el-form-item label="板材厚度上限" prop="upperThickness">
                                        <el-input v-model.number="ruleForm2.upperThickness"></el-input>
                                    </el-form-item>
                                </el-col>
                                <el-col :span="8">
                                    <el-form-item label="板材厚度下限" prop="lowerThickness">
                                        <el-input v-model.number="ruleForm2.lowerThickness"></el-input>
                                    </el-form-item>
                                </el-col>
                                <el-col :span="8">
                                    <el-form-item label="板材宽度上限" prop="upperWidth">
                                        <el-input v-model.number="ruleForm2.upperWidth"></el-input>
                                    </el-form-item>
                                </el-col>
                                <el-col :span="8">
                                    <el-form-item label="板材宽度下限" prop="lowerWidth">
                                        <el-input v-model.number="ruleForm2.lowerWidth"></el-input>
                                    </el-form-item>
                                </el-col>
                                <el-col :span="8">
                                    <el-form-item label="大于等于厚度下限" prop="greaterThanLowerLimit">
                                        <el-input v-model.number="ruleForm2.greaterThanLowerLimit"></el-input>
                                    </el-form-item>
                                </el-col>
                                <el-col :span="8">
                                    <el-form-item label="大于等于厚度上限" prop="greaterThanUpperLimit">
                                        <el-input v-model.number="ruleForm2.greaterThanUpperLimit"></el-input>
                                    </el-form-item>
                                </el-col>
                                <el-col :span="8">
                                    <el-form-item label="板宽最大长度" prop="maximumLength">
                                        <el-input v-model.number="ruleForm2.maximumLength"></el-input>
                                    </el-form-item>
                                </el-col>
                            </el-row>

                            <el-row :gutter="5" type="flex" justify="center">
                                <el-button type="primary">插入数据</el-button>
                            </el-row>
                        </el-form>

                        <el-row :gutter="5">
                            <el-col :span="24">
                                <el-table
                                    :data="maxLengthTable"
                                    ref="multipleTable"
                                    height="250"
                                    border
                                    @selection-change="handleSelectionChange"
                                    style="width: 100%"
                                    :default-sort="{prop: 'type'}"
                                >
                                    <el-table-column type="selection" sortable></el-table-column>
                                    <el-table-column prop="lowerHardness" label="板材硬度下限" sortable></el-table-column>
                                    <el-table-column prop="upperHardness" label="板材硬度上限" sortable></el-table-column>
                                    <el-table-column prop="upperThickness" label="板材厚度上限" sortable></el-table-column>
                                    <el-table-column prop="lowerThickness" label="板材厚度下限" sortable></el-table-column>
                                    <el-table-column prop="lowerWidth" label="板材宽度上限" sortable></el-table-column>
                                    <el-table-column prop="upperWidth" label="板材宽度下限" sortable></el-table-column>
                                    <el-table-column
                                        prop="greaterThanLowerLimit"
                                        label="大于等于厚度下限"
                                        sortable
                                    ></el-table-column>
                                    <el-table-column
                                        prop="greaterThanUpperLimit"
                                        label="大于等于厚度上限"
                                        sortable
                                    ></el-table-column>
                                    <el-table-column prop="maximumLength" label="板宽最大长度" sortable></el-table-column>
                                </el-table>
                            </el-col>

                            <el-col :span="8">
                                <el-form-item label="订单宽度范围" prop="criticalValue">
                                    <el-row :gutter="4" type="flex" justify="space-between">
                                        <el-col :span="11">
                                            <el-input v-model.number="ruleForm2.criticalValue"></el-input>
                                        </el-col>
                                        <el-col :span="11">
                                            <el-input v-model.number="ruleForm2.criticalValue"></el-input>
                                        </el-col>
                                    </el-row>
                                </el-form-item>
                            </el-col>
                        </el-row>
                    </el-tab-pane>

                    <el-tab-pane label="切损表维护">
                        <el-form :model="ruleForm2" status-icon ref="ruleForm2" label-width="130px">
                            <el-row :gutter="20">
                                <el-col :span="8">
                                    <el-form-item label="订单类型" prop="lowerHardness">
                                        <el-input v-model.number="ruleForm2.lowerHardness"></el-input>
                                    </el-form-item>
                                </el-col>
                                <el-col :span="8">
                                    <el-form-item label="切割方式" prop="upperHardness">
                                        <el-input v-model.number="ruleForm2.upperHardness"></el-input>
                                    </el-form-item>
                                </el-col>
                                <el-col :span="8">
                                    <el-form-item label="展宽比" prop="upperThickness">
                                        <el-input v-model.number="ruleForm2.upperThickness"></el-input>
                                    </el-form-item>
                                </el-col>
                                <el-col :span="8">
                                    <el-form-item label="厚板厚度" prop="lowerThickness">
                                        <el-input v-model.number="ruleForm2.lowerThickness"></el-input>
                                    </el-form-item>
                                </el-col>
                                <el-col :span="8">
                                    <el-form-item label="切边" prop="upperWidth">
                                        <el-input v-model.number="ruleForm2.upperWidth"></el-input>
                                    </el-form-item>
                                </el-col>
                                <el-col :span="8">
                                    <el-form-item label="切头尾" prop="lowerWidth">
                                        <el-input v-model.number="ruleForm2.lowerWidth"></el-input>
                                    </el-form-item>
                                </el-col>
                            </el-row>

                            <el-row :gutter="5" type="flex" justify="center">
                                <el-button type="primary">插入数据</el-button>
                            </el-row>
                        </el-form>

                        <el-row :gutter="5">
                            <el-col :span="24">
                                <el-table
                                    :data="maxLengthTable"
                                    ref="multipleTable"
                                    height="250"
                                    border
                                    @selection-change="handleSelectionChange"
                                    style="width: 100%"
                                    :default-sort="{prop: 'type'}"
                                >
                                    <el-table-column type="selection" sortable></el-table-column>
                                    <el-table-column prop="lowerHardness" label="订单类型" sortable></el-table-column>
                                    <el-table-column prop="upperHardness" label="切割方式" sortable></el-table-column>
                                    <el-table-column prop="upperThickness" label="展宽比" sortable></el-table-column>
                                    <el-table-column prop="lowerThickness" label="厚板厚度" sortable></el-table-column>
                                    <el-table-column prop="lowerWidth" label="切边" sortable></el-table-column>
                                    <el-table-column prop="upperWidth" label="切头尾" sortable></el-table-column>
                                </el-table>
                            </el-col>

                            <el-col :span="8">
                                <el-form-item label="订单宽度范围" prop="criticalValue">
                                    <el-row :gutter="4" type="flex" justify="space-between">
                                        <el-col :span="11">
                                            <el-input v-model.number="ruleForm2.criticalValue"></el-input>
                                        </el-col>
                                        <el-col :span="11">
                                            <el-input v-model.number="ruleForm2.criticalValue"></el-input>
                                        </el-col>
                                    </el-row>
                                </el-form-item>
                            </el-col>
                        </el-row>
                    </el-tab-pane>
                </el-tabs>
            </el-col>
        </el-row>
        <el-row :gutter="20">
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
    data() {
        return {
            ruleForm2: {
                lowerHardness: '', //硬度下限
                upperHardness: '', //硬度上限
                upperThickness: '', //厚度上限
                lowerThickness: '', //厚度下限
                lowerWidth: '', //宽度下限
                upperWidth: '', //宽度上限
                greaterThanLowerLimit: '', //大于等于厚度下限
                greaterThanUpperLimit: '', //大于等于厚度上限
                maximumLength: '' //板宽最大长度
            },
            maxLengthTable: [
                {
                    lowerHardness: '20', //硬度下限
                    upperHardness: '5', //硬度上限
                    upperThickness: '10', //厚度上限
                    lowerThickness: '16', //厚度下限
                    lowerWidth: '15', //宽度下限
                    upperWidth: '265', //宽度上限
                    greaterThanLowerLimit: '16', //大于等于厚度下限
                    greaterThanUpperLimit: '5', //大于等于厚度上限
                    maximumLength: '5' //板宽最大长度
                },
                {
                    lowerHardness: '20', //硬度下限
                    upperHardness: '5', //硬度上限
                    upperThickness: '10', //厚度上限
                    lowerThickness: '16', //厚度下限
                    lowerWidth: '15', //宽度下限
                    upperWidth: '265', //宽度上限
                    greaterThanLowerLimit: '16', //大于等于厚度下限
                    greaterThanUpperLimit: '5', //大于等于厚度上限
                    maximumLength: '5' //板宽最大长度
                },
                {
                    lowerHardness: '20', //硬度下限
                    upperHardness: '5', //硬度上限
                    upperThickness: '10', //厚度上限
                    lowerThickness: '16', //厚度下限
                    lowerWidth: '15', //宽度下限
                    upperWidth: '265', //宽度上限
                    greaterThanLowerLimit: '16', //大于等于厚度下限
                    greaterThanUpperLimit: '5', //大于等于厚度上限
                    maximumLength: '5' //板宽最大长度
                },
                {
                    lowerHardness: '20', //硬度下限
                    upperHardness: '5', //硬度上限
                    upperThickness: '10', //厚度上限
                    lowerThickness: '16', //厚度下限
                    lowerWidth: '15', //宽度下限
                    upperWidth: '265', //宽度上限
                    greaterThanLowerLimit: '16', //大于等于厚度下限
                    greaterThanUpperLimit: '5', //大于等于厚度上限
                    maximumLength: '5' //板宽最大长度
                }
            ],

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
        };
    }
};
</script>

<style>
</style>