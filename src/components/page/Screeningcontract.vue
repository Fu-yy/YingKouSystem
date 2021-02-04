<template>
    <div>
        <el-row :gutter="20" style="margin:auto">
            <el-row :gutter="20" style="margin:auto">
                <el-col :span="15">
                    <el-container>
                        <el-header style="text-align: left;">搜索</el-header>

                        <el-card shadow="hover">
                            <el-form
                                :model="ruleForm2"
                                status-icon
                                ref="ruleForm2"
                                label-width="110px"
                            >
                                <el-row :gutter="5">
                                    <el-col :span="8">
                                        <el-form-item label="订单号" prop="criticalValue">
                                            <el-input v-model.number="ruleForm2.criticalValue"></el-input>
                                        </el-form-item>
                                    </el-col>
                                    <el-col :span="8">
                                        <el-form-item label="合同号" prop="criticalValue">
                                            <el-input v-model.number="ruleForm2.criticalValue"></el-input>
                                        </el-form-item>
                                    </el-col>
                                    <el-col :span="8">
                                        <el-form-item label="订单号-项次" prop="criticalValue">
                                            <el-input v-model.number="ruleForm2.criticalValue"></el-input>
                                        </el-form-item>
                                    </el-col>
                                    <el-col :span="8">
                                        <el-form-item label="合同号-项次" prop="criticalValue">
                                            <el-input v-model.number="ruleForm2.criticalValue"></el-input>
                                        </el-form-item>
                                    </el-col>
                                    <el-col :span="8">
                                        <el-form-item label="产线" prop="criticalValue">
                                            <el-input v-model.number="ruleForm2.criticalValue"></el-input>
                                        </el-form-item>
                                    </el-col>
                                    <el-col :span="8">
                                        <el-form-item label="订单长度范围" prop="criticalValue">
                                            <el-row :gutter="4" type="flex" justify="space-between">
                                                <el-col :span="11">
                                                    <el-input
                                                        v-model.number="ruleForm2.criticalValue"
                                                    ></el-input>
                                                </el-col>
                                                <el-col :span="11">
                                                    <el-input
                                                        v-model.number="ruleForm2.criticalValue"
                                                    ></el-input>
                                                </el-col>
                                            </el-row>
                                        </el-form-item>
                                    </el-col>
                                </el-row>
                                <el-row :gutter="5">
                                    <el-col :span="8">
                                        <el-form-item label="订单厚度范围" prop="criticalValue">
                                            <el-row :gutter="4" type="flex" justify="space-between">
                                                <el-col :span="11">
                                                    <el-input
                                                        v-model.number="ruleForm2.criticalValue"
                                                    ></el-input>
                                                </el-col>
                                                <el-col :span="11">
                                                    <el-input
                                                        v-model.number="ruleForm2.criticalValue"
                                                    ></el-input>
                                                </el-col>
                                            </el-row>
                                        </el-form-item>
                                    </el-col>

                                    <el-col :span="8">
                                        <el-form-item label="订单宽度范围" prop="criticalValue">
                                            <el-row :gutter="4" type="flex" justify="space-between">
                                                <el-col :span="11">
                                                    <el-input
                                                        v-model.number="ruleForm2.criticalValue"
                                                    ></el-input>
                                                </el-col>
                                                <el-col :span="11">
                                                    <el-input
                                                        v-model.number="ruleForm2.criticalValue"
                                                    ></el-input>
                                                </el-col>
                                            </el-row>
                                        </el-form-item>
                                    </el-col>
                                </el-row>

                                <el-row>
                                    <el-col :span="24">
                                        <el-form-item label="合同分配日期" prop="criticalValue">
                                            <el-date-picker
                                                v-model="contracDatetimerange"
                                                type="datetimerange"
                                                align="right"
                                                unlink-panels
                                                range-separator="至"
                                                start-placeholder="开始日期"
                                                end-placeholder="结束日期"
                                                :picker-options="pickerOptions2"
                                            ></el-date-picker>
                                        </el-form-item>
                                    </el-col>
                                </el-row>
                                <el-row>
                                    <el-col :span="24">
                                        <el-form-item label="交货日期范围" prop="criticalValue">
                                            <el-date-picker
                                                v-model="deliveryDatetimerange"
                                                type="datetimerange"
                                                align="right"
                                                unlink-panels
                                                range-separator="至"
                                                start-placeholder="开始日期"
                                                end-placeholder="结束日期"
                                                :picker-options="pickerOptions2"
                                            ></el-date-picker>
                                        </el-form-item>
                                    </el-col>
                                </el-row>

                                <el-row :gutter="5" type="flex" justify="center">
                                    <el-button type="primary">搜索</el-button>
                                </el-row>
                            </el-form>
                        </el-card>
                    </el-container>
                </el-col>
                <el-col :span="9">
                    <el-container>
                        <el-header style="text-align: left;">筛选</el-header>

                        <el-card shadow="hover">
                            <el-form
                                :model="ruleForm2"
                                status-icon
                                ref="ruleForm2"
                                label-width="110px"
                            >
                                <el-row :gutter="5">
                                    <el-col :span="24">
                                        <div style="height:40px"></div>
                                    </el-col>
                                    <el-col :span="20">
                                        <el-form-item label="是否有欠" prop="criticalValue">
                                            <el-input v-model.number="ruleForm2.criticalValue"></el-input>
                                        </el-form-item>
                                    </el-col>
                                    <el-col :span="20">
                                        <el-form-item label="GK码" prop="criticalValue">
                                            <el-input v-model.number="ruleForm2.criticalValue"></el-input>
                                        </el-form-item>
                                    </el-col>
                                    <el-col :span="20">
                                        <el-form-item label="牌号" prop="criticalValue">
                                            <el-row :gutter="4" type="flex" justify="space-between">
                                                <el-col :span="11">
                                                    <el-input
                                                        v-model.number="ruleForm2.criticalValue"
                                                    ></el-input>
                                                </el-col>
                                                <el-col :span="11">
                                                    <el-input
                                                        v-model.number="ruleForm2.criticalValue"
                                                    ></el-input>
                                                </el-col>
                                            </el-row>
                                        </el-form-item>
                                    </el-col>
                                    <el-col :span="24">
                                        <div style="height:58px"></div>
                                    </el-col>
                                </el-row>

                                <el-row :gutter="5" type="flex" justify="center">
                                    <el-button type="primary">清除筛选条件</el-button>
                                    <el-button type="primary">筛选</el-button>
                                </el-row>
                            </el-form>
                        </el-card>
                    </el-container>
                </el-col>
            </el-row>
            <el-row :gutter="20" style="margin:auto;margin-top:10px">
                <el-col :span="18">
                    <el-card shadow="hover">
                        <el-table
                            :data="tableData3"
                            ref="multipleTable"
                            height="350"
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

                        <el-row :gutter="0" type="flex" justify="center" style="margin-top:10px">
                            <el-col :span="6" :offset="6">
                                <el-button type="primary">确认</el-button>
                            </el-col>
                            <el-col :span="6">
                                <download-excel
                                    :data="json_data"
                                    :fields="json_fields"
                                    worksheet="My Worksheet"
                                    name="测试表格"
                                >
                                    <el-button type="success">导出数据</el-button>
                                </download-excel>
                            </el-col>
                        </el-row>
                    </el-card>
                </el-col>
                <el-col :span="6">
                    <el-card shadow="hover">
                        <el-table
                            :data="tableData3"
                            ref="multipleTable"
                            height="355"
                            border
                            @selection-change="handleSelectionChange"
                            style="width: 100%"
                            :default-sort="{prop: 'type'}"
                        >
                            <el-table-column type="selection" sortable></el-table-column>
                            <el-table-column prop="long" label="GK码-钢牌" sortable></el-table-column>
                            <el-table-column prop="type" label="硬度值" sortable></el-table-column>
                        </el-table>
                        <el-row :gutter="0" type="flex" justify="center" style="margin-top:10px">
                            <el-col :span="6" :offset="6">
                                <el-button type="primary">添加</el-button>
                            </el-col>
                            <el-col :span="6" :offset="6">
                                <el-button type="primary">插入</el-button>
                            </el-col>
                        </el-row>
                    </el-card>
                </el-col>
            </el-row>
        </el-row>
    </div>
</template>

<script>
export default {
    name: 'screeningcontract',
    data() {
        return {
            contracDatetimerange: '', //合同分配日期
            deliveryDatetimerange: '', //交货日期范围
            pickerOptions2: {
                //日期选择范围
                shortcuts: [
                    {
                        text: '最近一周',
                        onClick(picker) {
                            const end = new Date();
                            const start = new Date();
                            start.setTime(start.getTime() - 3600 * 1000 * 24 * 7);
                            picker.$emit('pick', [start, end]);
                        }
                    },
                    {
                        text: '最近一个月',
                        onClick(picker) {
                            const end = new Date();
                            const start = new Date();
                            start.setTime(start.getTime() - 3600 * 1000 * 24 * 30);
                            picker.$emit('pick', [start, end]);
                        }
                    },
                    {
                        text: '最近三个月',
                        onClick(picker) {
                            const end = new Date();
                            const start = new Date();
                            start.setTime(start.getTime() - 3600 * 1000 * 24 * 90);
                            picker.$emit('pick', [start, end]);
                        }
                    }
                ]
            },

            ruleForm2: {
                criticalValue: '', //临界值
                threshold: '', //阈值
                maxLength: '', //最大长度
                maxWidth: '' //最大跳宽
            },
            json_fields: {
                类型: 'type',
                长度: 'long',
                mold_thickness: 'mold_thickness'
                // 'Telephone 2': 'phone.landline'
                // 'Telephone 2': {
                //     field: 'phone.landline',
                //     callback: value => {
                //         return `Landline Phone - ${value}`;
                //     }
                // }
            },
            json_data: [
                // {
                //     name: 'Tony Peña',
                //     city: 'New York',
                //     country: 'United States',
                //     birthdate: '1978-03-15',
                //     phone: {
                //         mobile: '1-541-754-3010',
                //         landline: '(541) 754-3010'
                //     }
                // },
                // {
                //     name: 'Thessaloniki',
                //     city: 'Athens',
                //     country: 'Greece',
                //     birthdate: '1987-11-23',
                //     phone: {
                //         mobile: '+1 855 275 5071',
                //         landline: '(2741) 2621-244'
                //     }
                // }
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
            ]
        };
    },
    methods: {
        handleSelectionChange(val) {
            // this.multipleSelection = val;
            // console.log(this.tableData4);
            // if(tableData4.type == val.type){

            // }
            this.json_data = val;
            // console.log(val);
            // val.forEach(valItem => {
            //     this.tableData4.forEach(element => {
            //         if (element.type == valItem.type) {
            //             element.data.forEach(dataItem => {
            //                 console.log(dataItem);
            //                 console.log('dataItem');
            //                 var dataItemTest = {};
            //                 dataItemTest.type = element.type;
            //                 dataItemTest.code = dataItem.code;
            //                 dataItemTest.thickness = dataItem.thickness;
            //                 this.multipleSelection.push(dataItemTest);
            //             });
            //         }
            //     });
            // });

            console.log(this.json_data);
        }
    }
};
</script>

<style scoped>
.el-header {
    background-color: #b3c0d1;
    color: #333;
    text-align: center;
    height: 30px;
    line-height: 60px;
}
</style>