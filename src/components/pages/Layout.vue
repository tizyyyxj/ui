<template>
  <div class="wapper">
    <el-container class="container">
      <el-container style="height: 500px; border: black">
        <el-aside class="aside" width="200px">
          <el-menu
            :default-openeds="['1', '3']"
            default-active="2"
            class="el-menu-vertical-demo"
            background-color="#545c64"
            text-color="#fff"
            active-text-color="#ffd04b"
          >
            <el-menu-item index="2">
              <i class="el-icon-menu"></i>
              <span slot="title">后台管理系统</span>
            </el-menu-item>
            <el-submenu index="2" class="aside">
              <template slot="title">
                <i class="el-icon-s-home"></i>首页
              </template>
            </el-submenu>
            <el-submenu index="3" class="aside">
              <template slot="title">
                <i class="el-icon-setting"></i>系统设置
              </template>
              <el-menu-item index="2">
                <span slot="title">菜单管理</span>
              </el-menu-item>
              <el-menu-item index="2">
                <span slot="title">角色管理</span>
              </el-menu-item>
              <el-menu-item index="2">
                <span slot="title">管理员管理</span>
              </el-menu-item>
            </el-submenu>

            <el-submenu index="4" class="aside">
              <template slot="title">
                <i class="el-icon-s-goods"></i>商品管理
              </template>
            </el-submenu>
            <el-submenu index="5" class="aside">
              <template slot="title">
                <i class="el-icon-user-solid"></i>商城管理
              </template>
            </el-submenu>
          </el-menu>
        </el-aside>

        <el-container>
          <el-header style="text-align: right; font-size: 12px">
            <span>admin</span>
            <el-dropdown>
              <i class="el-icon-setting" style="margin-right: 15px"></i>
              <el-dropdown-menu slot="dropdown">
                <el-dropdown-item>查看</el-dropdown-item>
                <el-dropdown-item>新增</el-dropdown-item>
                <el-dropdown-item>删除</el-dropdown-item>
              </el-dropdown-menu>
            </el-dropdown>
          </el-header>
          <el-button type="primary" style="width:70px ">添加</el-button>
          <el-main>
            <!-- <el-table :data="tableData" border style="width: 100%">
              <el-table-column fixed prop="name" label="名称" width="150"></el-table-column>
              <el-table-column prop="icon" label="图标" width="120"></el-table-column>
              <el-table-column prop="type" label="类型" width="120"></el-table-column>
              <el-table-column prop="sort" label="排序" width="60"></el-table-column>
            <el-table-column prop="menu" label="菜单URL" width="300"> </el-table-column>-->
            <el-table
              :data="tableData"
              style="width: 100%"
              row-key="id"
              border
              lazy
              :load="load"
              :tree-props="{children: 'children', hasChildren: 'hasChildren'}"
            >
              <el-table-column fixed prop="name" label="名称" width="150"></el-table-column>
              <el-table-column prop="icon" label="图标" width="120"></el-table-column>
              <el-table-column prop="type" label="类型" width="120"></el-table-column>
              <el-table-column prop="sort" label="排序" width="60"></el-table-column>
              <el-table-column prop="menu" label="菜单URL" width="300"></el-table-column>

              <el-table-column label="操作">
                <template slot-scope="scope">
                  <el-button size="mini" @click="handleEdit(scope.$index, scope.row)">编辑</el-button>
                  <el-button
                    size="mini"
                    type="danger"
                    @click="handleDelete(scope.$index, scope.row)"
                  >删除</el-button>
                </template>
              </el-table-column>
            </el-table>
          </el-main>
        </el-container>
      </el-container>
    </el-container>
  </div>
</template>
// <script>
// export default {
//   methods: {
//     handleClick(row) {
//       console.log(row);
//     },
//   },

//   data() {
//     return {
//       tableData: [
//         {
//           name: "系统设置",
//           icon: <i class="el-icon-setting"></i>,
//           type: <el-tag>目录</el-tag>,
//           sort: "0",
//           menu: "",
//           children: [
//             {
//               id: 31,
//               date: "2016-05-01",
//               name: "王小虎",
//               address: "上海市普陀区金沙江路 1519 弄",
//             },
//             {
//               id: 32,
//               date: "2016-05-01",
//               name: "王小虎",
//               address: "上海市普陀区金沙江路 1519 弄",
//             },
//           ],
//         },
//         {
//           name: "产品管理",
//           icon: <i class="el-icon-s-goods"></i>,
//           type: <el-tag>目录</el-tag>,
//           sort: "1",
//           menu: "",
//         },
//         {
//           name: "商城管理",
//           icon: <i class="el-icon-user-solid"></i>,
//           type: <el-tag>目录</el-tag>,
//           sort: "2",
//           menu: "",
//         },
//       ],
//     };
//   },
// };
//
</script>
<script>
export default {
  data() {
    return {
      tableData: [
        {
          id: 1,
          name: "系统设置",
          icon: <i class="el-icon-setting"></i>,
          type: <el-tag>目录</el-tag>,
          sort: "0",
          menu: "",
          children: [
            {
          id: 31,
          name: "菜单管理",
          icon: "",
          type: <el-tag type="success">菜单</el-tag>,
          sort: "",
          menu: "/munu",
            },
            {
              id: 32,
          name: "角色管理",
          icon: "",
          type: <el-tag type="success">菜单</el-tag>,
          sort: "",
          menu: "/munu",
            },
               {
              id: 33,
          name: "管理员管理",
          icon: "",
          type: <el-tag type="success">菜单</el-tag>,
          sort: "",
          menu: "/munu",
            },
          ],
        },
        {
          id: 2,
          name: "产品管理",
          icon: <i class="el-icon-s-goods"></i>,
          type: <el-tag>目录</el-tag>,
          sort: "1",
          menu: "",
          children: [
            {
              id: 31,
            name: "分类管理",
          icon: "",
          type: <el-tag type="success">菜单</el-tag>,
          sort: "",
          menu: "/munu",
            }
          ],
        },
        {
          id: 3,
          name: "商城管理",
          icon: <i class="el-icon-user-solid"></i>,
          type: <el-tag>目录</el-tag>,
          sort: "2",
          menu: "",
          children: [
             {
              id: 32,
          name: "角色管理",
          icon: "",
          type: <el-tag type="success">菜单</el-tag>,
          sort: "",
          menu: "/munu",
            },
               {
              id: 33,
          name: "管理员管理",
          icon: "",
          type: <el-tag type="success">菜单</el-tag>,
          sort: "",
          menu: "/munu",
            },
          ],
        },
      ],
    };
  },
  methods: {
    load(tree, treeNode, resolve) {
      setTimeout(() => {
        resolve([
          {
            id: 31,
            date: "2016-05-01",
            name: "王小虎",
            address: "上海市普陀区金沙江路 1519 弄",
          },
          {
            id: 32,
            date: "2016-05-01",
            name: "王小虎",
            address: "上海市普陀区金沙江路 1519 弄",
          },
        ]);
      }, 1000);
    },
  },
};
</script>
<style lang="" scoped>
.el-header {
  background-color: #709cc0cc;
  color: #333;
  line-height: 60px;
}

.el-aside {
  color: #333;
}
.aside {
  background-color: #545c64;
  color: white;
}
/* .el-header, .el-footer {
    background-color: #B3C0D1;
    color: #333;
    text-align: center;
    line-height: 60px;
  }
  
  .el-aside {
    background-color: #D3DCE6;
    color: #333;
    text-align: center;
    line-height: 200px;
  }
  
  .el-main {
    background-color: #E9EEF3;
    color: #333;
    text-align: center;
    line-height: 160px;
  }
  
  body > .el-container {
    margin-bottom: 40px;
  }
  
  .el-container:nth-child(5) .el-aside,
  .el-container:nth-child(6) .el-aside {
    line-height: 260px;
  }
  
  .el-container:nth-child(7) .el-aside {
    line-height: 320px;
  } */
</style>

