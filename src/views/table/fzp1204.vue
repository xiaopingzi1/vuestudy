<template>
  <el-table :data="tableData" style="width: 100%" row-class-name="add" @expand-change="zydescription" border >
    <el-table-column type="expand" label="序号"  width="120">
      <template slot-scope="props">
        <el-table border style="width: 100%" :data="props.row.test">
          <el-table-column label="序号" width="80" type="index"></el-table-column>
          <el-table-column prop="name" label="商品名称" width="180"></el-table-column>
          <el-table-column prop="shop" label="所属店铺" width="180"></el-table-column>
          <el-table-column prop="id" label="商品 ID"></el-table-column>
          <el-table-column prop="complate" label="是否完成">
            <template slot-scope="props">
              <span v-if="props.row.complate">
                <span style="color:#00B46D" @click="a">已完成</span>
              </span>
              <span v-else>
                <span style="color:#D75C89">未完成</span>
              </span>
            </template>
          </el-table-column>
          <el-table-column prop="category" label="商品分类"></el-table-column>
          <el-table-column label="选择日期" prop="date">
            <template slot-scope="props">
              <span v-if="props.row.complate">
               <el-date-picker
                  v-model="props.row.date"
                  type="date"
                  placeholder="选择日期"
                >
                </el-date-picker>
              </span>
              <span v-else>
                <el-date-picker
                  v-model="props.row.date"
                  type="date"
                  placeholder="选择日期a "
                >
                </el-date-picker>
              </span>
            </template>
          </el-table-column>
        </el-table>
      </template>
    </el-table-column>
    <!-- <el-table-column label="序号" prop="id" type="index" width="120">
    </el-table-column> -->
    <el-table-column label="商品 ID" prop="id"></el-table-column>
    <el-table-column label="商品名称" prop="name"></el-table-column>
    <el-table-column label="描述" prop="desc"></el-table-column>
  </el-table>
</template>

<script>
export default {
  data() {
    return {
      tableData: [
        {
          id: "12987122",
          name: "好滋好味鸡蛋仔1",
          category: "江浙小吃、小吃零食",
          desc: "荷兰优质淡奶，奶香浓而不腻",
          address: "上海市普陀区真北路",
          shop: "王小虎夫妻店",
          shopId: "10333",
          date: "2019-12-12",
          test: [
            {
              id: "12987122",
              name: "好滋好味鸡蛋仔1",
              category: "江浙小吃、小吃零食",
              desc: "荷兰优质淡奶，奶香浓而不腻",
              address: "上海市普陀区真北路",
              shop: "王小虎夫妻店",
              shopId: "10333",
              date: "2019-12-12",
              complate: false
            }
          ]
        },
        {
          id: "12987123",
          name: "好滋好味鸡蛋仔2",
          category: "江浙小吃、小吃零食",
          desc: "荷兰优质淡奶，奶香浓而不腻",
          address: "上海市普陀区真北路",
          shop: "王小虎夫妻店",
          shopId: "10333",
          date: "2019-12-13",
          test: [
            {
              id: "12987122",
              name: "好滋好味鸡蛋仔1",
              category: "江浙小吃、小吃零食",
              desc: "荷兰优质淡奶，奶香浓而不腻",
              address: "上海市普陀区真北路",
              shop: "王小虎夫妻店",
              shopId: "10333",
              date: "2019-12-12",
              complate: true
            }
          ]
        },
        {
          id: "12987125",
          name: "好滋好味鸡蛋仔3",
          category: "江浙小吃、小吃零食",
          desc: "荷兰优质淡奶，奶香浓而不腻",
          address: "上海市普陀区真北路",
          shop: "王小虎夫妻店",
          shopId: "10333",
          date: "2019-12-12",
          test: [
            {
              id: "12987122",
              name: "好滋好味鸡蛋仔1",
              category: "江浙小吃、小吃零食",
              desc: "荷兰优质淡奶，奶香浓而不腻",
              address: "上海市普陀区真北路",
              shop: "王小虎夫妻店",
              shopId: "10333",
              date: "2019-12-12",
              complate: true
            }
          ]
        },
        {
          id: "12987126",
          name: "好滋好味鸡蛋仔4",
          category: "江浙小吃、小吃零食",
          desc: "荷兰优质淡奶，奶香浓而不腻",
          address: "上海市普陀区真北路",
          shop: "王小虎夫妻店",
          shopId: "10333",
          date: "2019-12-12",
          test: [
            {
              id: "12987122",
              name: "好滋好味鸡蛋仔1",
              category: "江浙小吃、小吃零食",
              desc: "荷兰优质淡奶，奶香浓而不腻",
              address: "上海市普陀区真北路",
              shop: "王小虎夫妻店",
              shopId: "10333",
              date: "2019-12-12",
              complate: true
            }
          ]
        }
      ],
      imgType: false,
      
    };
  },

  components: {},

  computed: {},

  mounted() {
    // this.setPorety();
  },
  created() {
    this.setPorety();
  },
  methods: {
    zydescription(row, expandedRows) {
      // 根据点击行id判断所在索引
      var list = this.tableData;
      for (var i = 0; i < list.length;i++) {
        if (list[i].id == row.id) {
          var imgType = row.imgType;
          this.$set(this.tableData[i], "imgType", !imgType);
          var imgs = document.querySelectorAll(".add .el-table__expand-icon");
            if (this.tableData[i].imgType) {
              imgs[i].style.backgroundImage =
                "url(https://zux2.oss-cn-beijing.aliyuncs.com/2019/12/04/fe099a9da5b043a5851dd3a2430c441c.png)";
            } else {
              imgs[i].style.backgroundImage =
                "url(https://zux2.oss-cn-beijing.aliyuncs.com/2019/12/04/facb2ad1697c429a9382eb2f0aa1c0ed.png)";
            }
        }
      }
      
    },
    setPorety() {
      var data = this.tableData;
      for (var i = 0; i < data.length; i++) {
        this.$set(data[i], "imgType", false);
      }
      // 图标后添加索引
      this.$nextTick( ()=> {
        var imgs = document.querySelectorAll(".el-table__body-wrapper .el-table__row .el-table__expand-column");
        console.log(imgs)
        for (let i = 0;i < imgs.length;i++) {
          var div = document.createElement('div');
          div.className = 'newIndex'
          imgs[i].appendChild(div);
          var cout = document.createTextNode(i+1)
          div.appendChild(cout)
        }
      })

    },
  }
};
</script>

<style>
.newIndex{display:inline-block;width:32px;height:32px;line-height:32px;text-align:center;float:right;margin-right:20px;}
.demo-table-expand {
  font-size: 0;
}
.demo-table-expand label {
  width: 90px;
  color: #99a9bf;
}
.demo-table-expand .el-form-item {
  margin-right: 0;
  margin-bottom: 0;
  width: 50%;
}
.el-table--border th:first-child .cell, .el-table--border td:first-child .cell{display:inline-block;}
.add .el-table__expand-icon {
  width: 32px;
  height: 32px;
  background: url("../../icons/img/jiahao.png");
  -webkit-transform: rotate(0deg);
  transform: rotate(0deg);
  display:inline-block;
}
.add .el-table__expand-icon > .el-icon {
  display: none;
}
.jian {width: 32px;
  height: 32px;
  background: url("../../icons/img/jianhao.png");
  -webkit-transform: rotate(0deg);
  transform: rotate(0deg);}
.el-date-editor.el-input,
.el-date-editor.el-input__inner {
  width: 100%;
}
.red input {
  background-color: red;
}
.pink input {
  background-color: pink;
}

.tableClass {
  color: #666;
  border-color: #666;
}
</style>
