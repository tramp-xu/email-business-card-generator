<script>
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
      copyState: '',
      isLoading: false
    }
  },
  methods: {
    build () {
      let dom = document.querySelector('.right__sign')
      this.code = String(dom.innerHTML)
      this.isLoading = true
      setTimeout(() => {
        this.isLoading = false
        this.copy()
      }, 1000)
    },
    copy () {
      let target = document.getElementById('code')
      target.select()
      let done = document.execCommand('Copy')
      if (done) {
        this.copyState = 'success'
        this.$message({
          message: '已复制到剪贴板',
          type: 'success'
        })
      } else {
        this.copyState = 'fail'
        this.$message({
          message: '复制失败, 请手动复制代码',
          type: 'warning'
        })
      }
    }
  }
}
</script>

<template>
  <div class="index">
    <input type="text" v-model="code" id="code" class="code">
    <el-card class="box-card">
      <div slot="header" class="clearfix">
        <span>企业微信签名生成器</span>
      </div>
      <div class="card__body">
        <div class="card__body--left" v-loading="isLoading">
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
            </el-form-item>
          </el-form>
        </div>
        <div class="card__body--right">
          <div class="right__sign">
            <!--企朋-->
            <div v-if="form.logo === 'qipeng'" style="width: 100%;">
              <div style="float: left; height: 47px; overflow: hidden; margin: 16px 0;">
                <img :src="urls[form.logo]" style="width: 73px;height: 47px;">
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
            <div v-if="form.logo === 'yunpian'">
              <div style="float: left; height: 47px; overflow: hidden; margin: 16px 0;">
                <img :src="urls['yunpian']" style="width: 125px;height: 47px;">
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
            <div v-if="form.logo === 'simboss'">
              <div style="float: left; height: 29px; overflow: hidden; margin: 25px 0;">
                <img :src="urls['simboss']" style="width: 128px;height: 29px;">
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
            <div v-if="form.logo === 'weike'">
              <div style="float: left; height: 39px; overflow: hidden; margin: 20px 0;">
                <img :src="urls['weike']" style="width: 82px;height: 39px;">
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
          <!--代码展示-->
          <template v-if="copyState === 'fail'">
            <div class="copy-by-self">自动复制失败请手动复制下面的代码</div>
            <el-input type="textarea" v-model="code" :rows="6"></el-input>
          </template>
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
  .copy-by-self {
    color: #ff9f1a;
    margin: 30px 0 10px;
  }
</style>
