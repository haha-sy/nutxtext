<template>
  <div class="about">
    <div class="text-center my-5">
      <el-button type="primary"><nuxt-link to="/">返回Home页面</nuxt-link></el-button>
    </div>
    <el-row>
      <el-col :span="1"><div class="grid-content bg-purple-dark">
        <div class="nav-left">
          <ul class="text-l">
            <li>
              <i class="el-icon-s-shop"></i>
              <div>收银</div>
            </li>
            <li>
              <i class="el-icon-s-home"></i>
              <div>店铺</div>
            </li>
            <li>
              <i class="el-icon-s-goods"></i>
              <div>商品</div>
            </li>
            <li>
              <i class="el-icon-s-custom"></i>
              <div>会计</div>
            </li>
            <li>
              <i class="el-icon-s-data"></i>
              <div>统计</div>
            </li>
            <li>
              <i class="el-icon-s-tools"></i>
              <div>设置</div>
            </li>
          </ul>
        </div>
      </div></el-col>
      <el-col :span="8">
        <div class="mx-3 grid-content bg-purple-dark">
        <el-tabs class="tab-nav" type="card">
          <el-tab-pane label="点餐">
            <el-table
              :data="tableData"
              style="width: 100%"
              border
            >
              <el-table-column prop="goodsName" label="商品" width="120">
              </el-table-column>
              <el-table-column prop="count" label="数量" width="80">
              </el-table-column>
              <el-table-column prop="price" label="价格" width="80">
              </el-table-column>
              <el-table-column label="操作" fixed="right" width="150">
                <template slot-scope="scope">
                  <el-button type="success" size="mini">删除</el-button>
                  <el-button type="primary" size="mini">增加</el-button>
                </template>
              </el-table-column>
            </el-table>
            <div class="text-center my-5">
              <el-button type="warning" size="small">挂单</el-button>
              <el-button type="danger" size="small">删除</el-button>
              <el-button type="success" size="small">结账</el-button>
            </div>
          </el-tab-pane>
          <el-tab-pane label="挂单">挂单</el-tab-pane>
          <el-tab-pane label="外卖">外卖</el-tab-pane>
        </el-tabs>
      </div>
      </el-col>
      <el-col :span="15"><div class="grid-content bg-purple-dark">
        <div class="often-goods ">
          <div class="title h-8 pl-5">Hot 商品</div>
          <div class="often-goods-list">
            <ul>
              <li :key="item.goodsId" v-for="item in oftenGoods">
                <span>{{item.goodsName}}</span>
                <span class="price">￥{{item.price}}元</span>
              </li>
            </ul>
          </div>
        </div>
      </div></el-col>
    </el-row>
  </div>
</template>

<script>
    export default {
        data() {
            return {
                tableData: [{
                    goodsName: '可口可乐',
                    price: 8,
                    count:1
                }, {
                    goodsName: '香辣鸡腿堡',
                    price: 15,
                    count:1
                }, {
                    goodsName: '爱心薯条',
                    price: 8,
                    count:1
                }, {
                    goodsName: '甜筒',
                    price: 8,
                    count:1
                }],
                oftenGoods:[
                    {
                        goodsId:1,
                        goodsName:'香辣鸡腿堡',
                        price:18
                    }, {
                        goodsId:2,
                        goodsName:'田园鸡腿堡',
                        price:15
                    }, {
                        goodsId:3,
                        goodsName:'和风汉堡',
                        price:15
                    }, {
                        goodsId:4,
                        goodsName:'快乐全家桶',
                        price:80
                    }, {
                        goodsId:5,
                        goodsName:'脆皮炸鸡腿',
                        price:10
                    }, {
                        goodsId:6,
                        goodsName:'上校鸡块',
                        price:20
                    }, {
                        goodsId:7,
                        goodsName:'大杯可乐',
                        price:10
                    }, {
                        goodsId:8,
                        goodsName:'雪顶咖啡',
                        price:18
                    }, {
                        goodsId:9,
                        goodsName:'大块鸡米花',
                        price:15
                    }, {
                        goodsId:20,
                        goodsName:'香脆鸡柳',
                        price:17
                    }
                ]
            }
        }
    }
</script>

<style scoped>
  .nav-left {
    color: #fff;
    background-color: #1D8ce0;
    height: 100%;
  }

.nav-left li {
  border-bottom: 1px solid #ccc;
  text-align: center;
  margin: 15px 0;
  cursor: pointer;
}
.nav-left li:nth-child(1) {
  margin-top: 0;
}

.nav-left i {
  font-size: 24px;
}

.title {
  border-bottom: 1px solid #ccc;
  background-color: #f9fafc;
}

.often-goods-list ul li {
  float: left;
  border: 1px solid #e5e9f2;
  padding: 10px;
  margin: 5px;
  cursor: pointer;
}

.price {
  color: #58b7ff;
}
</style>
