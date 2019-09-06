<template>
  <div class="container">
    <el-container>
      <el-header>好好学习 天天向上</el-header>
      <el-container>
        <el-aside  :width="changeCollapse?'80px':'200px'">
          <el-row class="tac">
            <el-col :span="24">
              <i class="nav cursor-pointer" @click="changeColl">|||</i>
              <el-menu
                default-active="1"
                background-color="#545c64"
                text-color="#fff"
                active-text-color="#ffd04b"
                :collapse="changeCollapse"
                :collapse-transition="false"
                unique-opened
              >
                <el-submenu index="1">
                  <template slot="title">
                    <i class="el-icon-location"></i>
                    <span>星期一</span>
                  </template>
                  <el-menu-item-group>
                    <el-menu-item index="1-1" @click="goAbout">选项1</el-menu-item>
                  </el-menu-item-group>
                  </el-submenu>
                <el-submenu index="2">
                 <template slot="title">
                   <i class="el-icon-menu"></i>
                   <span slot="title">星期二</span>
                 </template>
                  <el-menu-item-group>
                    <el-menu-item index="1-1" @click="goNews">选项1</el-menu-item>
                  </el-menu-item-group>
                </el-submenu>
                <el-submenu index="3">
                  <template slot="title">
                  <i class="el-icon-document"></i>
                  <span slot="title">星期三</span>
                  </template>
                  <el-menu-item-group>
                    <el-menu-item index="1-1">选项1</el-menu-item>
                  </el-menu-item-group>
                </el-submenu>
                <el-submenu index="4">
                  <template slot="title">
                    <i class="el-icon-setting"></i>
                    <span slot="title">星期四</span>
                  </template>
                  <el-menu-item-group>
                    <el-menu-item index="1-1">选项1</el-menu-item>
                  </el-menu-item-group>
                </el-submenu>
                <el-submenu index="5">
                  <template slot="title">
                    <i class="el-icon-user-solid"></i>
                    <span slot="title">星期五</span>
                  </template>
                  <el-menu-item-group>
                    <el-menu-item index="1-1">选项1</el-menu-item>
                  </el-menu-item-group>
                </el-submenu>
                <el-submenu index="6">
                  <template slot="title">
                    <i class="el-icon-star-on"></i>
                    <span slot="title">星期六</span>
                  </template>
                  <el-menu-item-group>
                    <el-menu-item index="1-1">选项1</el-menu-item>
                  </el-menu-item-group>
                </el-submenu>
                <el-submenu index="7">
                  <template slot="title">
                    <i class="el-icon-star-on"></i>
                    <span slot="title">星期日</span>
                  </template>
                  <el-menu-item-group>
                    <el-menu-item index="1-1">选项1</el-menu-item>
                  </el-menu-item-group>
                </el-submenu>
              </el-menu>
            </el-col>
          </el-row>
        </el-aside>
        <el-main>
            <div class="my-4">
              <el-button type="success" @click="changeDialogVisible=!changeDialogVisible">点击添加书籍</el-button>
              <!--            <el-button type="info" >跳转到About页面</el-button>-->
            </div>
          <el-dialog
            title="添加文学著作"
            :visible.sync="changeDialogVisible"
            width="50%">
            <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm">
              <el-form-item label="文学著作" prop="book">
                <el-input v-model="ruleForm.book"></el-input>
              </el-form-item>
              <el-form-item label="作者" prop="name">
                <el-input v-model="ruleForm.name"></el-input>
              </el-form-item>
              <el-form-item label="发布日期" prop="data">
                <el-input v-model="ruleForm.data"></el-input>
              </el-form-item>
            </el-form>
            <span slot="footer" class="dialog-footer">
            <el-button @click="changeDialogVisible = false">取 消</el-button>
            <el-button type="primary" @click="changeDialogVisible = false">确 定</el-button>
          </span>
          </el-dialog>

          <el-table
            :data="tableData"
            style="width: 100%"
            border
            stripe
            highlight-current-row
          >
            <el-table-column
              prop="book"
              label="文学著作"
              width="150">
            </el-table-column>
            <el-table-column
              prop="name"
              label="作者"
              width="120">
            </el-table-column>
            <el-table-column
              prop="data"
              label="发布日期">
            </el-table-column>
            <el-table-column>
              <el-button type="success" size="small" @click="editDialog">
                编辑
              </el-button>
            <el-button type="primary" size="small" @click="removeDialog">
              删除
            </el-button>
            </el-table-column>
          </el-table>

          <el-dialog
            title="编辑"
            :visible.sync="editDialogVisible"
            width="50%"
            >
            <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm">
              <el-form-item label="文学著作" prop="book">
                <el-input v-model="ruleForm.book"></el-input>
              </el-form-item>
              <el-form-item label="作者" prop="name">
                <el-input v-model="ruleForm.name"></el-input>
              </el-form-item>
              <el-form-item label="发布日期" prop="data">
                <el-input v-model="ruleForm.data"></el-input>
              </el-form-item>
            </el-form>
            <span slot="footer" class="dialog-footer">
            <el-button @click="editDialogVisible = false">取 消</el-button>
            <el-button type="primary" @click="editDialogVisible = false">确 定</el-button>
          </span>
          </el-dialog>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>

export default {
  components: {
  },
  data() {
      return {
          changeDialogVisible: false,
          changeCollapse: false,
          editDialogVisible: false,
          tableData: [{
              book: '红楼梦',
          name: '王小虎',
              data: '1999-01-01'
      }, {
              book: '西游记',
          name: '王小虎',
              data: '1999-01-01'
      }, {
              book: '水浒传',
          name: '王小虎',
              data: '1999-01-01'
      }, {
              book: '三国演义',
          name: '王小虎',
              data: '1999-01-01'
      }, {
                  book: '安徒生童话',
                  name: '王小虎',
                  data: '1999-01-01'
          }, {
              book: '鲁滨逊漂游记',
              name: '王小虎',
              data: '1999-01-01'
          },],
          ruleForm: {

          },
          rules: {

          },
      }
  },
    methods: {
        changeColl() {
            this.changeCollapse = !this.changeCollapse
        },
        editDialog() {
            this.editDialogVisible = !this.editDialogVisible
        },
        removeDialog() {
            this.$confirm('此操作将永久删除该文件, 是否继续?', '提示', {
                confirmButtonText: '确定',
                cancelButtonText: '取消',
                type: 'warning'
            }).then(() => {
                this.$message({
                    type: 'success',
                    message: '删除成功!'
                });
            }).catch(() => {
                this.$message({
                    type: 'info',
                    message: '已取消删除'
                });
            });
        },
        goAbout() {
            this.$router.push({
                name: 'about',
                params: {
                    id: '123'
                }
            })
        },
        goNews() {
            this.$router.push({
                path: '/news',
                query: {
                    id: 456
                }
            })
        },

    }
}
</script>

<style scoped>
.el-header {
 background-color: #2b4b6b;
  text-align: center;
  line-height: 60px;
  color: #fff;
}

  .el-aside {
    width: 30%;
    background-color: #545c64;
    height: 500px;
  }

  .el-main {
    padding: 0 10px;
    width: 70%;
    background-color: #fff;
    height: 500px;
  }

  .nav {
    display: block;
    width: 100%;
    text-align: center;
    line-height: 21px;
    background-color: gray;
  }

  .el-table .el-button {
    margin: 0;
  }
</style>
