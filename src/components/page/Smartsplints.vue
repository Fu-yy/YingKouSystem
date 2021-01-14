<template>
    <div>
        <el-row :gutter="20">
            <el-col :span="24">
                <el-card shadow="hover">
                    <!--     
                        :span-method="objectSpanMethod"
                    -->
                    <!-- <el-row type="flex" :gutter="10" justify="center" style="width:100%">
                        <el-col :span="6">
                            <el-button size="medium">全选</el-button>
                        </el-col>
                        <el-col :span="6">
                            <el-button size="medium">反选</el-button>
                        </el-col>
                        <el-col :span="6">
                            <el-button size="medium">新增</el-button>
                        </el-col>
                        <el-col :span="6">
                            <el-button size="medium">删除</el-button>
                        </el-col>
                    </el-row>-->

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

            <!-- <el-col :span="12">
                <el-card shadow="hover">
                    <el-table
                        :data="multipleSelection"
                        style="width: 100%"
                        height="250"
                        border
                        :default-sort="{prop: 'type'}"
                        @selection-change="handleSelectionChange1"
                    >
                        <el-table-column type="selection" width="55" sortable></el-table-column>
                        <el-table-column prop="type" label="坯型" sortable width="180"></el-table-column>
                        <el-table-column prop="code" label="坯料代码" sortable width="180"></el-table-column>
                        <el-table-column prop="thickness" label="板坯厚度" sortable width="180"></el-table-column>
                    </el-table>
                </el-card>
            </el-col>-->
        </el-row>

        <el-row :gutter="10">
            <el-col :span="24">
                <el-card shadow="hover">
                    <el-form
                        :model="ruleForm2"
                        status-icon
                        :rules="rules2"
                        ref="ruleForm2"
                        label-width="110px"
                        class="demo-ruleForm"
                    >
                        <el-form-item label="部分宽度临界值" prop="criticalValue">
                            <el-input v-model.number="ruleForm2.criticalValue">
                                <template slot="append">毫米(mm)</template>
                            </el-input>
                        </el-form-item>

                        <el-form-item label="超厚板阈值" prop="threshold">
                            <el-input v-model.number="ruleForm2.threshold">
                                <template slot="append">毫米(mm)</template>
                            </el-input>
                        </el-form-item>

                        <el-form-item label="超厚板最大长度" prop="maxLength">
                            <el-input v-model.number="ruleForm2.maxLength">
                                <template slot="append">毫米(mm)</template>
                            </el-input>
                        </el-form-item>

                        <el-form-item label="钢板内最大跳宽" prop="maxWidth">
                            <el-input v-model.number="ruleForm2.maxWidth">
                                <template slot="append">毫米(mm)</template>
                            </el-input>
                        </el-form-item>
                        <el-form-item>
                            <el-button type="primary" @click="submitForm('ruleForm2')">智能拼版</el-button>
                            <el-button type="primary" @click="submitForm2('ruleForm2')">方案调整</el-button>
                            <el-button type="primary" @click="submitForm3('ruleForm2')">违规检查</el-button>
                            <el-button type="primary" @click="submitForm4('ruleForm2')">方案确认</el-button>
                            <el-button @click="resetForm('ruleForm2')">重置</el-button>
                        </el-form-item>
                    </el-form>
                </el-card>
            </el-col>

            <el-col :span="12">
                <el-card shadow="hover">
                    <div>
                        <p>{{text}}</p>
                    </div>
                    <!-- <el-button type="primary" @click="dialogTableVisible = true">筛选合同</el-button> -->
                    <!-- <router-link to="/403.vue">
     <button class="btn btn-default">点击跳转</button>
                    </router-link>-->

                    
                </el-card>
            </el-col>
        </el-row>
    </div>
</template>

<script>
import bus from '../common/bus';
export default {
    name: 'smartsplints',
    data() {
        var validateCriticalValue = (rule, value, callback) => {
            if (value === '') {
                callback(new Error('请输入部分宽度临界值'));
            }
        };

        var validateThreshold = (rule, value, callback) => {
            if (value === '') {
                callback(new Error('请输入超厚板阈值'));
            }
        };

        var validateMaxLength = (rule, value, callback) => {
            if (value === '') {
                callback(new Error('请输入超厚板最大长度'));
            }
        };

        var validateMaxWidth = (rule, value, callback) => {
            if (value === '') {
                callback(new Error('请输入钢板内最大跳宽'));
            }
        };

        return {
            dialogTableVisible: false,
            multipleSelection: [],
            multipleSelectionResult: [],
            text: '',
            tableData4: [
                {
                    type: '01',
                    data: [
                        {
                            code: 'E123EE',
                            thickness: '250'
                        },
                        {
                            code: 'AAAAAAA',
                            thickness: '250'
                        }
                    ]
                },
                {
                    type: '02',
                    data: [
                        {
                            code: 'E12gdfgdfg3EE',
                            thickness: '300'
                        },
                        {
                            code: 'AAAAcccccAAA',
                            thickness: '300'
                        }
                    ]
                },
                {
                    type: '03',
                    data: [
                        {
                            code: 'E12GHGfg3EE',
                            thickness: '300'
                        },
                        {
                            code: 'AAWEccAAA',
                            thickness: '300'
                        }
                    ]
                },
                {
                    type: '04',
                    data: [
                        {
                            code: 'E12GGQ3EE',
                            thickness: '300'
                        },
                        {
                            code: 'QQAAA',
                            thickness: '300'
                        }
                    ]
                },
                {
                    type: '05',
                    data: [
                        {
                            code: 'ETTTQ3EE',
                            thickness: '300'
                        },
                        {
                            code: 'QQQQTD03A',
                            thickness: '300'
                        }
                    ]
                }
            ],
            tableData3: [
                {
                    type: '01',
                    long:'30',
                    mold_thickness:'167',
                    mold_width:'1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long:'2400',
                    max_long:'4730',
                    max_width:'999999',
                    min_width:'0',
                    max_thick:'9999',
                    min_thick:'0',
                    is_normal:'0'
                },
                {
                    type: '02',
                     long:'30',
                    mold_thickness:'167',
                    mold_width:'1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long:'2400',
                    max_long:'4730',
                    max_width:'999999',
                    min_width:'0',
                    max_thick:'9999',
                    min_thick:'0',
                    is_normal:'0'
                },
                {
                    type: '03',
                    long:'30',
                    mold_thickness:'167',
                    mold_width:'1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long:'2400',
                    max_long:'4730',
                    max_width:'999999',
                    min_width:'0',
                    max_thick:'9999',
                    min_thick:'0',
                    is_normal:'0'
                },
                {
                    type: '04',
                     long:'30',
                    mold_thickness:'167',
                    mold_width:'1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long:'2400',
                    max_long:'4730',
                    max_width:'999999',
                    min_width:'0',
                    max_thick:'9999',
                    min_thick:'0',
                    is_normal:'0'
                },
                {
                    type: '05',
                    long:'30',
                    mold_thickness:'167',
                    mold_width:'1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long:'2400',
                    max_long:'4730',
                    max_width:'999999',
                    min_width:'0',
                    max_thick:'9999',
                    min_thick:'0',
                    is_normal:'0'
                },
                {
                    type: '06',
                    long:'30',
                    mold_thickness:'167',
                    mold_width:'1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long:'2400',
                    max_long:'4730',
                    max_width:'999999',
                    min_width:'0',
                    max_thick:'9999',
                    min_thick:'0',
                    is_normal:'0'
                },
                {
                    type: '07',
                    long:'30',
                    mold_thickness:'167',
                    mold_width:'1550',
                    thickness: '250',
                    slabwidth: '2000',
                    min_long:'2400',
                    max_long:'4730',
                    max_width:'999999',
                    min_width:'0',
                    max_thick:'9999',
                    min_thick:'0',
                    is_normal:'0'
                }
            ],
            ruleForm2: {
                criticalValue: '', //临界值
                threshold: '', //阈值
                maxLength: '', //最大长度
                maxWidth: '' //最大跳宽
            },
            rules2: {
                criticalValue: [{ validator: validateCriticalValue, trigger: 'blur' }],
                threshold: [{ validator: validateThreshold, trigger: 'blur' }],
                maxLength: [{ validator: validateMaxLength, trigger: 'blur' }],
                maxWidth: [{ validator: validateMaxWidth, trigger: 'blur' }]
            }
        };
    },
    components: {},
    computed: {},
    methods: {
        formatter(row, column) {
            console.log(row);
            console.log(column);
            return row.address;
        },
        // 合并相同行
        objectSpanMethod({ row, column, rowIndex, columnIndex }) {
            if (columnIndex === 2) {
                if (rowIndex % 2 === 0) {
                    return {
                        rowspan: 2,
                        colspan: 1
                    };
                } else {
                    return {
                        rowspan: 0,
                        colspan: 0
                    };
                }
            }
        },
        handleSelectionChange(val) {
            // this.multipleSelection = val;
            // console.log(this.tableData4);
            // if(tableData4.type == val.type){

            // }
            this.multipleSelection = [];
            // console.log(val);
            val.forEach(valItem => {
                this.tableData4.forEach(element => {
                    if (element.type == valItem.type) {
                        element.data.forEach(dataItem => {
                            console.log(dataItem);
                            console.log('dataItem');
                            var dataItemTest = {};
                            dataItemTest.type = element.type;
                            dataItemTest.code = dataItem.code;
                            dataItemTest.thickness = dataItem.thickness;
                            this.multipleSelection.push(dataItemTest);
                        });
                    }
                });
            });

            console.log(this.multipleSelection);
        },

        handleSelectionChange1(val) {
            this.multipleSelectionResult = val;
            this.text = '选中的代码为：';
            this.multipleSelectionResult.forEach(element => {
                this.text += element.code + ',';
            });
        },
        submitForm(formName) {
            this.$refs[formName].validate(valid => {
                if (valid) {
                    alert('submit!');
                } else {
                    console.log('error submit!!');
                    return false;
                }
            });
        },
        resetForm(formName) {
            this.$refs[formName].resetFields();
        }
    }
};
</script>


<style scoped>
.el-row {
    margin-bottom: 20px;
}

.grid-content {
    display: flex;
    align-items: center;
    height: 100px;
}

.grid-cont-right {
    flex: 1;
    text-align: center;
    font-size: 14px;
    color: #999;
}

.grid-num {
    font-size: 30px;
    font-weight: bold;
}

.grid-con-icon {
    font-size: 50px;
    width: 100px;
    height: 100px;
    text-align: center;
    line-height: 100px;
    color: #fff;
}

.grid-con-1 .grid-con-icon {
    background: rgb(45, 140, 240);
}

.grid-con-1 .grid-num {
    color: rgb(45, 140, 240);
}

.grid-con-2 .grid-con-icon {
    background: rgb(100, 213, 114);
}

.grid-con-2 .grid-num {
    color: rgb(45, 140, 240);
}

.grid-con-3 .grid-con-icon {
    background: rgb(242, 94, 67);
}

.grid-con-3 .grid-num {
    color: rgb(242, 94, 67);
}

.user-info {
    display: flex;
    align-items: center;
    padding-bottom: 20px;
    border-bottom: 2px solid #ccc;
    margin-bottom: 20px;
}

.user-avator {
    width: 120px;
    height: 120px;
    border-radius: 50%;
}

.user-info-cont {
    padding-left: 50px;
    flex: 1;
    font-size: 14px;
    color: #999;
}

.user-info-cont div:first-child {
    font-size: 30px;
    color: #222;
}

.user-info-list {
    font-size: 14px;
    color: #999;
    line-height: 25px;
}

.user-info-list span {
    margin-left: 70px;
}

.mgb20 {
    margin-bottom: 20px;
}

.todo-item {
    font-size: 14px;
}

.todo-item-del {
    text-decoration: line-through;
    color: #999;
}

.schart {
    width: 100%;
    height: 300px;
}
</style>
