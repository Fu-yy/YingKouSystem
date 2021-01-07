<template>
    <div>
        <el-button @click="add">添加</el-button>
        <el-button @click="submitBtn">测试提交</el-button>
        <el-table :data="data">
            <el-table-column prop="name" label="名称">
                <template slot-scope="scope">
                    <el-select
                        v-model="data[scope.$index].name"
                        @change="selectNameFunc(data[scope.$index].name)"
                    >
                        <el-option
                            v-for="(option)  in propertiesList"
                            :label="option.name"
                            :value="option.name"
                            :key="option.id"
                            :disabled="option.disabled"
                        ></el-option>
                    </el-select>
                </template>
            </el-table-column>
            <el-table-column prop="age" label="筛选方式">
                <template slot-scope="scope">
                    <!-- <el-input v-model="data[scope.$index].age"></el-input> -->

                    <el-select
                        v-model="data[scope.$index].type"
                        @change="test(scope.$index,data[scope.$index].type)"
                    >
                        <el-option
                            v-for="(option)  in options"
                            :label="option.name"
                            :value="option.name"
                            :key="option.id"
                        ></el-option>
                    </el-select>
                </template>
            </el-table-column>

            <el-table-column prop="age" label="值">
                <template slot-scope="scope">
                    <el-input
                        v-if="data[scope.$index].type!='范围'"
                        placeholder="请输入值"
                        v-model="data[scope.$index].equalum"
                    ></el-input>

                    <el-row v-if="data[scope.$index].type == '范围'" type="flex" justify="center">
                        <el-col :span="8">
                            <el-input placeholder="最小值" v-model="data[scope.$index].minNum"></el-input>
                        </el-col>
                        <!-- 横线 -->
                        <el-col :span="8">
                            <div style="margin:0 auto;text-align:center">
                                <i class="el-icon-minus" ></i>
                                <i class="el-icon-minus" ></i>
                                <i class="el-icon-minus" ></i>
                                <i class="el-icon-minus" ></i>
                            </div>
                        </el-col>
                        <el-col :span="8">
                            <el-input placeholder="最大值" v-model="data[scope.$index].maxNum"></el-input>
                        </el-col>
                    </el-row>
                </template>
            </el-table-column>

            <el-table-column label="操作">
                <template slot-scope="scope">
                    <el-button @click="deleteRow(scope.$index)">删除</el-button>
                </template>
            </el-table-column>
        </el-table>
    </div>
</template>

<script>
export default {
    name: 'testAdd',
    // data:{
    //     data:data
    // },
    data() {
        return {
            data: [],
            propertiesList: [
                {
                    name: 'id',
                    id: '1',
                    disabled: false
                },
                {
                    name: '厚度',

                    id: '2',
                    disabled: false
                },
                {
                    name: '长度',

                    id: '3',
                    disabled: false
                },
                {
                    name: '宽度',

                    id: '4',
                    disabled: false
                }
            ],
            options: [
                {
                    name: '范围',
                    id: '1'
                },
                {
                    name: '等于',
                    id: '2'
                },
                {
                    name: '大于',

                    id: '3'
                },
                {
                    name: '小于',

                    id: '4'
                }
            ]
        };
    },
    methods: {
        add() {
            this.data.push({});
            console.log(this.data);
        },
        deleteRow(index) {
            const propertiesName = this.data[index].name;

            this.propertiesList.forEach(element => {
                console.log(element);

                if (propertiesName == element.name) {
                    element.disabled = false;
                }
            });

            // for (let index = 0; index < this.propertiesList.length; index++) {
            //   const element = this.propertiesList[index];
            //   if(propertiesName == element.name){
            //     this.propertiesList[index].disabled = false;
            //   }
            // }
            this.data.splice(index, 1);
        },
        test(index, data) {
            console.log(this.data);
            console.log('********************');
            console.log(data);
            // if("范围" === data){
            console.log('*************');
            // for (let i = 0; i < this.data.length; i++) {
            //   const element = this.data[i];
            //   if (index == i) {
            //     this.data.i.typeBoolean = true;
            //   } else {
            //     this.data.i.typeBoolean = false;
            //   }
            // }
            // this.isshow2 = true;
            // this.isshow1 = false;
            // }else{
            //   console.log("dasdasd");
            //   this.isshow1 = true;
            //     this.isshow2 = false;
            // }
        },
        selectNameFunc(name) {
            // for (let index = 0; index < this.propertiesList.length; index++) {
            //   const element = this.propertiesList[index];
            //   if(name == element.name){
            //     this.propertiesList[index].disabled = true;
            //   }
            // }

            this.propertiesList.forEach(element => {
                console.log('遍历元素');
                console.log(element);
                if (name == element.name) {
                    element.disabled = true;
                }
            });
            console.log(name);
        },
        submitBtn() {
            console.log('提交');
            console.log(this.data);
            this.data.forEach(element => {
                console.log();
                if ('范围' == element.type) {
                    console.log(element.name + ':' + element.type + '-' + element.minNum + '~' + element.maxNum);
                } else {
                    console.log(element.name + ':' + element.type + '-' + element.equalum);
                }
            });
        }
    }
};
</script>

<style>
</style>