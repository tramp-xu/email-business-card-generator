<script>
import domtoimage from 'dom-to-image'

const form = {
  logo: 'qipeng',
  name: '隔壁老王',
  esName: 'W.lao',
  career: '前端',
  department: '产品研发部',
  email: 'laowang@qq.com',
  phone: '188 8888 8888',
  weChat: 'laowang',
  address: '杭州西湖区紫霞街176号互联网创新创业园1幢10F'
}
const urls = {
  qipeng: 'https://www.yunpian.com/console/static/img/email/qipeng.png',
  yunpian: 'https://www.yunpian.com/console/static/img/email/yunpian.png',
  simboss: 'https://www.yunpian.com/console/static/img/email/simboss.png',
  weike: 'https://www.yunpian.com/console/static/img/email/weike.png'
}

export default {
  name: 'Index',
  data () {
    return {
      value1: '',
      form: {...form},
      urls: {...urls},
      code: '',
      dataURL: ''
    }
  },
  methods: {
    build () {
      let dom = document.querySelector('.card__body--right')
      this.code = String(dom.innerHTML)
      setTimeout(() => {
        this.copy()
      }, 500)
    },
    copy () {
      let target = document.getElementById('code')
      target.select()
      let done = document.execCommand('Copy')
      if (done) {
        this.$message({
          message: '已复制到剪贴板',
          type: 'success'
        })
      } else {
        this.$message({
          message: '复制失败, 请联系许俊雄',
          type: 'warning'
        })
      }
    },
    draw () {
      let id = this.form.logo
      let node = document.getElementById(id)

      let filter = node => {
        return (node.tagName !== 'i')
      }
      domtoimage.toSvg(node, {filter: filter})
        .then(function (dataUrl) {
          var link = document.createElement('a')
          link.download = 'my-image-name1.svg'
          link.href = dataUrl
          link.click()
        })
    }
  }
}
</script>

<template>
  <div class="index">
    <input type="text" v-model="code" id="code" class="code">
    <el-card class="box-card">
      <div slot="header" class="clearfix">
        <span>测试生成图片中... 若急需要使用请联系许俊雄</span>
      </div>
      <div class="card__body">
        <div class="card__body--left">
          <el-form ref="form" :model="form" label-width="80px">
            <el-form-item label="">
              <el-radio-group v-model="form.logo">
                <el-radio label="qipeng">企朋</el-radio>
                <el-radio label="yunpian">云片</el-radio>
                <el-radio label="simboss">SIMBOSS</el-radio>
                <el-radio label="weike">维客</el-radio>
              </el-radio-group>
            </el-form-item>
            <el-form-item label="中文名">
              <el-input v-model="form.name"></el-input>
            </el-form-item>
            <el-form-item label="英文名">
              <el-input v-model="form.esName"></el-input>
            </el-form-item>
            <el-form-item label="职业">
              <el-input v-model="form.career"></el-input>
            </el-form-item>
            <el-form-item label="部门">
              <el-input v-model="form.department"></el-input>
            </el-form-item>
            <el-form-item label="邮箱">
              <el-input v-model="form.email"></el-input>
            </el-form-item>
            <el-form-item label="手机">
              <el-input v-model="form.phone"></el-input>
            </el-form-item>
            <el-form-item label="微信">
              <el-input v-model="form.weChat"></el-input>
            </el-form-item>
            <el-form-item label="地址">
              <el-input v-model="form.address"></el-input>
            </el-form-item>
            <el-form-item label="">
              <el-button @click="build" type="primary">确认信息并复制代码</el-button>
              <el-button @click="draw" type="primary">确认信息并生成图片</el-button>
            </el-form-item>
          </el-form>
        </div>
        <div class="card__body--right">
          <!--企朋-->
          <div id="qipeng" v-if="form.logo === 'qipeng'" style="height: 79px; padding: 0 10px;">
            <div style="float: left; width: 73px; height: 47px;
            overflow: hidden; margin: 16px 0;
            background-image: url('/static/img/qipeng.png');
            -webkit-background-image: url('/static/img/qipeng.png');
            background-size: cover;
            -webkit-background-size: cover">
            </div>
            <div style="float: left; width: 2px; height: 79px; margin: 0 15px; background: linear-gradient(#fff 0%, #fff 5%, #4a67d3 30%, #4a67d3 70%, #fff 95%, #fff 100%)"></div>
            <div style="float: left; height: 79px;">
              <div style="font-size: 14px;color: #4a4a4a; margin: 0px 20px 2px 0;">
                <span style="font-weight: 600;">{{ form.name }}</span>
                <span style="font-size: 12px;">{{ form.esName }}</span>
                <span style="font-size: 12px;margin-left: 15px;">{{ form.career }} — {{ form.department }}</span>
              </div>
              <div style="font-size: 12px;color: #666;">
                <span style="color: #555;">邮箱：</span>
                <span style="color: #9b9b9b;">{{ form.email }}</span>
              </div>
              <div style="font-size: 12px;color: #666;">
                <span style="color: #555;">手机：</span>
                <span style="color: #9b9b9b;">{{ form.phone }}</span>
                <span style="color: #4a4a4a;margin: 0 8px;">|</span>
                <span style="color: #555;">微信：</span>
                <span style="color: #9b9b9b;">{{ form.weChat }}</span>
              </div>
              <div style="font-size: 12px;color: #666;">
                <span style="color: #555;">地址：</span>
                <span style="color: #9b9b9b;">{{ form.address }}</span>
              </div>
            </div>
            <div style="clear: both;"></div>
          </div>
          <!--云片-->
          <div id="yunpian" v-if="form.logo === 'yunpian'" style="height: 79px; padding: 0 10px;">
            <div style="float: left; width: 125px; height: 47px;
            overflow: hidden; margin: 16px 0;
            background-image: url('/static/img/yunpian.png');
            -webkit-background-image: url('/static/img/yunpian.png');
            background-size: cover;
            -webkit-background-size: cover;
            ">
            </div>
            <div style="float: left; width: 2px; height: 79px; margin: 0 15px; background: linear-gradient(#fff 0%, #fff 5%, #00a1ff 30%, #00a1ff 70%, #fff 95%, #fff 100%)"></div>
            <div style="float: left; height: 79px;">
              <div style="font-size: 14px;color: #4a4a4a; margin: 0px 20px 2px 0;">
                <span style="font-weight: 600;">{{ form.name }}</span>
                <span style="font-size: 12px;">{{ form.esName }}</span>
                <span style="font-size: 12px;margin-left: 15px;">{{ form.career }} — {{ form.department }}</span>
              </div>
              <div style="font-size: 12px;color: #666;">
                <span style="color: #555;">邮箱：</span>
                <span style="color: #9b9b9b;">{{ form.email }}</span>
              </div>
              <div style="font-size: 12px;color: #666;">
                <span style="color: #555;">手机：</span>
                <span style="color: #9b9b9b;">{{ form.phone }}</span>
                <span style="color: #4a4a4a;margin: 0 8px;">|</span>
                <span style="color: #555;">微信：</span>
                <span style="color: #9b9b9b;">{{ form.weChat }}</span>
              </div>
              <div style="font-size: 12px;color: #666;">
                <span style="color: #555;">地址：</span>
                <span style="color: #9b9b9b;">{{ form.address }}</span>
              </div>
            </div>
            <div style="clear: both;"></div>
          </div>
          <!--SIMBOSS-->
          <div id="simboss" v-if="form.logo === 'simboss'" style="height: 79px; padding: 0 10px;">
            <div style="float: left; width: 128px; height: 29px;
            overflow: hidden; margin: 25px 0;
            background-image: url('/static/img/simboss.png');
            -webkit-background-image: url('/static/img/simboss.png');
            background-size: cover;
            -webkit-background-size: cover;
            ">
            </div>
            <div style="float: left; width: 2px; height: 79px; margin: 0 15px; background: linear-gradient(#fff 0%, #fff 5%, #0095e2 30%, #0095e2 70%, #fff 95%, #fff 100%)"></div>
            <div style="float: left; height: 79px;">
              <div style="font-size: 14px;color: #4a4a4a; margin: 0px 20px 2px 0;">
                <span style="font-weight: 600;">{{ form.name }}</span>
                <span style="font-size: 12px;">{{ form.esName }}</span>
                <span style="font-size: 12px;margin-left: 15px;">{{ form.career }} — {{ form.department }}</span>
              </div>
              <div style="font-size: 12px;color: #666;">
                <span style="color: #555;">邮箱：</span>
                <span style="color: #9b9b9b;">{{ form.email }}</span>
              </div>
              <div style="font-size: 12px;color: #666;">
                <span style="color: #555;">手机：</span>
                <span style="color: #9b9b9b;">{{ form.phone }}</span>
                <span style="color: #4a4a4a;margin: 0 8px;">|</span>
                <span style="color: #555;">微信：</span>
                <span style="color: #9b9b9b;">{{ form.weChat }}</span>
              </div>
              <div style="font-size: 12px;color: #666;">
                <span style="color: #555;">地址：</span>
                <span style="color: #9b9b9b;">{{ form.address }}</span>
              </div>
            </div>
            <div style="clear: both;"></div>
          </div>
          <!--维客-->
          <div id="weike" v-if="form.logo === 'weike'" style="height: 79px; padding: 0 10px;">
            <div style="float: left; width: 82px; height: 39px;
            overflow: hidden; margin: 20px 0;
            background-image: url('/static/img/weike.png');
            -webkit-background-image: url('/static/img/weike.png');
            background-size: cover;
            -webkit-background-size: cover;
            ">
            </div>
            <div style="float: left; width: 2px; height: 79px; margin: 0 15px; background: linear-gradient(#fff 0%, #fff 5%, #0097e8 30%, #0097e8 70%, #fff 95%, #fff 100%)"></div>
            <div style="float: left; height: 79px;">
              <div style="font-size: 14px;color: #4a4a4a; margin: 0px 20px 2px 0;">
                <span style="font-weight: 600;">{{ form.name }}</span>
                <span style="font-size: 12px;">{{ form.esName }}</span>
                <span style="font-size: 12px;margin-left: 15px;">{{ form.career }} — {{ form.department }}</span>
              </div>
              <div style="font-size: 12px;color: #666;">
                <span style="color: #555;">邮箱：</span>
                <span style="color: #9b9b9b;">{{ form.email }}</span>
              </div>
              <div style="font-size: 12px;color: #666;">
                <span style="color: #555;">手机：</span>
                <span style="color: #9b9b9b;">{{ form.phone }}</span>
                <span style="color: #4a4a4a;margin: 0 8px;">|</span>
                <span style="color: #555;">微信：</span>
                <span style="color: #9b9b9b;">{{ form.weChat }}</span>
              </div>
              <div style="font-size: 12px;color: #666;">
                <span style="color: #555;">地址：</span>
                <span style="color: #9b9b9b;">{{ form.address }}</span>
              </div>
            </div>
            <div style="clear: both;"></div>
          </div>
        </div>
      </div>
    </el-card>
  </div>
</template>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style type="text/less">
  .code {
    z-index: -9999;
    position: absolute;
    left: -999px;
    top: -999px;
  }
  .box-card {
    width: 1010px;
    margin: 0 auto;
  }
  .card__body {
    display: flex;
    align-items: center;
  }
  .card__body--left {
    flex: 1;
  }
  .card__body--right {
    width: 500px;
    margin-left: 40px;
  }
</style>
