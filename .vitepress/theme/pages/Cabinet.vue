<template>
  <div class="cabinet-open-screen">
    <div class="os-bg-base"></div>
    <div class="os-bg-base os-bg1"></div>
    <div class="os-bg-base os-bg2"></div>

    <h1 class="brand-slogan-cabinet">PAWAO 真机集群全套硬件方案</h1>
    <h4 class="brand-desc-cabinet">
      全套完整一体化硬件方案，为您提供企业级使用体验
    </h4>
  </div>

  <section-box title="PAWAO 1.0 散热式机柜" isCenter>
    <div class="capacity-wrapper-cabinet">
      <video class="capacity-video" controls :src="cabinetVideo"/>
      <el-timeline class="capacity-list" style="text-align: left">
        <el-timeline-item v-for="i in cabinetDes" type="primary" :hollow="true">
          {{ i }}
        </el-timeline-item>
      </el-timeline>
    </div>
    <pur
      url="https://item.taobao.com/item.htm?ft=t&id=696443990660"
      :code="code1"
    />
  </section-box>

  <section-box title="PAWAO 1.0 智能集线器" isCenter>
    <div class="capacity-wrapper-cabinet">
      <el-timeline class="capacity-list-2" style="text-align: left">
        <el-timeline-item v-for="i in hubDes" type="primary" :hollow="true">
          {{ i }}
        </el-timeline-item>
      </el-timeline>
      <video class="capacity-video-2" controls :src="hubVideo"/>
    </div>
    <pur
      url="https://item.taobao.com/item.htm?ft=t&id=697697950839"
      :code="code2"
    />
  </section-box>

  <section-box title="所有硬件产品">
    <div class="use-case-cabinet">
      <el-card v-for="d in product" class="case-card-wrapper" shadow="hover">
        <div class="case-card-content">
          <img class="product-img" :src="d.pic"/>
          <h3 class="product-name">{{ d.title }}</h3>
          <p>{{ d.des }}</p>
          <p>{{ d.des2 }}</p>
          <pur :url="d.url" :code="d.code"/>
        </div>
      </el-card>
    </div>
  </section-box>

  <section-box title="他们都在用" isCenter>
    <div class="icon-container">
      <el-space
        v-for="t in ths"
        :size="25"
        alignment="stretch"
        style="margin: 20px 15px 0px 15px"
      >
        <a :href="t.url" target="_blank" class="cabinet-avatar">
          <el-avatar
            shape="square"
            style="margin-top: 20px;border-radius: 24px; box-shadow: 4px 4px 10px #606266"
            :src="t.src"
            :size="100"
            fit="contain"
          />
        </a>
      </el-space>
    </div>

    <div class="using-container">
      <el-carousel type="card" height="250px" :interval="5000">
        <el-carousel-item v-for="t in talk" :key="t">
          <el-card style="text-align: left">
            <div class="cabinet-avatar" style="display: flex">
              <el-avatar :src="t.ava" fit="contain" :size="60"/>
              <div style="flex: 1; margin-left: 20px">
                <div style="display: flex">
                  <h4 style="margin: 0px">{{ t.name }}</h4>
                  <el-rate
                    disabled
                    v-model="rate"
                    style="width: 160px; margin-left: 10px; height: 25px"
                  />
                </div>
                <el-card style="margin-top: 10px">
                  {{ t.msg }}
                </el-card>
              </div>
            </div>
          </el-card>
        </el-carousel-item>
      </el-carousel>
    </div>
  </section-box>

  <section-box
    title="设备充电保护落地效益"
    divider-content="Sonic实验室结合内测用户三个月实验数据"
  >
    <div class="profit-container">
      <el-descriptions direction="vertical" :column="1" size="large" border>
        <el-descriptions-item label="充电时长">
          工作日24h/天
        </el-descriptions-item>
        <el-descriptions-item label="电池温度">
          设备平均温度下降8-11°C
        </el-descriptions-item>
        <el-descriptions-item label="设备鼓包率">
          7% -> 1.8%
        </el-descriptions-item>
        <el-descriptions-item label="设备充电电流">
          接近额定电流，未出现过冲
        </el-descriptions-item>
        <el-descriptions-item label="设备充电电压">
          约4V - 4.5V不等
        </el-descriptions-item>
      </el-descriptions>
    </div>
  </section-box>

  <div class="footer-container">
    <div style="margin-bottom: 100px"></div>
    <el-footer style="margin-top: 75px">
      <el-divider></el-divider>
      <div style="font-size: 10px; color: #909399">
        上述硬件产品不影响Sonic平台正常使用，仅为搭建硬件环境提供采购选择，Sonic平台仍然保持永久开源、免费。
      </div>
      <div style="margin-top: 5px">
        <el-link
          href="mailto:soniccloudorg@163.com"
          target="_blank"
          type="primary"
        >
          官方邮箱
        </el-link>
        <el-link
          href="https://sonic-cloud.cn/wechat.jpg"
          target="_blank"
          type="primary"
          style="margin-left: 20px"
        >
          企微咨询
        </el-link>
      </div>
      <div style="margin-top: 10px">&nbsp;</div>
    </el-footer>
  </div>

  <!-- 咨询浮窗 -->
  <ConsultantFloat/>
</template>

<script setup lang="ts">
import {ref} from 'vue'
import Pur from '../components/Pur.vue'
import SectionBox from '../components/SectionBox.vue'
import ConsultantFloat from '@theme/components/ConsultantFloat.vue'
import th1 from '../assets/cabinet/th1.png'
import th2 from '../assets/cabinet/th2.png'
import th3 from '../assets/cabinet/th3.png'
import th4 from '../assets/cabinet/th4.png'
import th5 from '../assets/cabinet/th5.png'
import th6 from '../assets/cabinet/th6.jpg'
import th7 from '../assets/cabinet/th7.png'
import th8 from '../assets/cabinet/th8.png'
import user from '../assets/cabinet/user.png'
import you from '../assets/cabinet/you.png'
import xinyang from '../assets/cabinet/xinyang.jpg'
import taole from '../assets/cabinet/taole.png'
import eco from '../assets/cabinet/eco.jpeg'
import p1 from '../assets/cabinet/p1.jpg'
import p2 from '../assets/cabinet/p2.jpg'
import p3 from '../assets/cabinet/p3.jpg'
import p4 from '../assets/cabinet/p4.jpg'
import p5 from '../assets/cabinet/p5.jpg'
import p6 from '../assets/cabinet/p6.jpg'
import p7 from '../assets/cabinet/p7.jpg'
import code1 from '../assets/cabinet/code1.png'
import code2 from '../assets/cabinet/code2.png'
import code3 from '../assets/cabinet/code3.png'
import code4 from '../assets/cabinet/code4.png'
import code5 from '../assets/cabinet/code5.png'
import code6 from '../assets/cabinet/code6.png'
import code7 from '../assets/cabinet/code7.png'
import cabinetVideo from '../assets/video/cabinet.mp4'
import hubVideo from '../assets/video/hub.mp4'

const rate = ref(5)
const videoOptions = ref({
  width: '780px',
  height: '440px',
  controlBtns: ['audioTrack', 'quality', 'volume', 'fullScreen', 'speedRate']
})
const cabinetDes = ref([
  '采用工业级静电喷塑铝板',
  '3C级防爆钢化玻璃，安全美观',
  '特殊定制铝合金门锁，开关存放方便',
  '空间设计合理，摆放井井有续',
  '内置8块抽拉托盘，可存放80部手机',
  '便捷手机支架，适合多种款式机型',
  '满足不同充电口充电需求',
  '安全充电，管理方便，配备3c标准插排和品牌千兆交换机',
  '内置高速静音散热风扇，静音降温，保证柜内温度',
  '底部配有带刹车万向轮，方便移动柜体'
])
const hubDes = ref([
  '采用工业级铁质外壳',
  '3C级配置电源，保证电源供给防异常断电',
  '程控USB集线器，单独控制USB口通断电',
  '附赠二进制控制程序，搭配Sonic可视化界面',
  '搭载智能芯片，防电流过冲过压',
  '附带蓝色指示灯，通断情况一目了然',
  '10个USB3.0口，传输速度快人一步',
  '内置高速散热风扇，内部降温，控制集线器温度',
  'USB连接，一插即用，无需额外硬件接口与驱动'
])
const product = ref([
  {
    pic: p1,
    title: 'PAWAO 1.0 散热式机柜',
    des: '含小、中、大规格',
    des2: '可选择散热版、屏蔽版、温控版',
    url: 'https://item.taobao.com/item.htm?ft=t&id=696443990660',
    code: code1
  },
  {
    pic: p2,
    title: 'PAWAO 1.0 智能集线器',
    des: '提供二进制文件，可HTTP调用',
    des2: '轻松控制集线器USB口通断电',
    url: 'https://item.taobao.com/item.htm?ft=t&id=697697950839',
    code: code2
  },
  {
    pic: p3,
    title: 'PAWAO 1.0 智能数据线',
    des: '智能芯片助力充电口降温',
    des2: '支持Type-c、苹果数据线',
    url: 'https://item.taobao.com/item.htm?ft=t&id=693483194887',
    code: code3
  },
  {
    pic: p4,
    title: 'PAWAO 迷你工控机',
    des: '小巧工控机，可自定义配置',
    des2: '搭载Ubuntu系统，稳定运行',
    url: 'https://item.taobao.com/item.htm?ft=t&id=690165961688',
    code: code4
  },
  {
    pic: p5,
    title: 'PAWAO 六类网线',
    des: 'CAT6A成品网线、路由器网线',
    des2: '可自由选择长度',
    url: 'https://item.taobao.com/item.htm?ft=t&id=691859752465',
    code: code5
  },
  {
    pic: p6,
    title: 'PAWAO UPS电源',
    des: '外置电池主机',
    des2: '智能稳压，无惧异常断电',
    url: 'https://item.taobao.com/item.htm?ft=t&id=696193021266',
    code: code6
  },
  {
    pic: p7,
    title: 'PAWAO 无线路由器',
    des: '超强覆盖，信号稳定',
    des2: '高速率、超频宽、更疾速',
    url: 'https://item.taobao.com/item.htm?ft=t&id=696702703783',
    code: code7
  }
])
const ths = ref([
  {
    url: 'https://z.yonyoucloud.com/',
    src: th3
  },
  {
    url: 'https://www.yonyou.com/',
    src: th2
  },
  {
    url: 'https://pmcloud.yonyoucloud.com/official-index.html',
    src: th1
  },
  {
    url: 'http://thsy.yx20.com/main.html',
    src: th4
  },
  {
    url: 'http://yj.20planet.com/main.html',
    src: th5
  },
  {
    url: 'https://www.soyoung.com/',
    src: th6
  },
  {
    url: 'https://www.eeo.cn/cn/',
    src: th7
  },
  {
    url: 'http://www.galasports.net/home.html',
    src: th8
  }
])
const talk = ref([
  {
    ava: you,
    name: '友空间团队测试专家',
    msg: 'PAWAO全套硬件方案考虑非常全面，整体体验很不错，与Sonic平台契合度也很高。使用下来设备鼓包率大大下降，长时间测试与使用能保持电池健康的温度。手机管理，监控，使用变得更快捷，更有效！'
  },
  {
    ava: xinyang,
    name: '新氧技术中心-平台研发部',
    msg: '非常专业的硬件设备，是搭建云测机房的不二选择。不仅能很完美地与Sonic云测平台结合，而且技术售后也非常到位，考虑到的实际情况非常细心，期待更深入的合作'
  },
  {
    ava: taole,
    name: '深圳淘乐网络-手游研发团队',
    msg: 'HUB支持十台手机设备，并且HUB本身自带风扇散热，集中使用散热也很好，提高跑脚本时的稳定性，每个设备还可以通过HUB控制手机断电，提高电池使用寿命，集中管理的情况下常非方便远程管理设备。期待平台继续成长强大。'
  },
  {
    ava: eco,
    name: '翼鸥产品研发中心-测试团队',
    msg: '考虑非常周到的硬件套装，让中小企业打造自己专属的云测设施变为可能！搭配Sonic云测平台对设备进行软硬件的监控与控制非常便利，祝越来越好。'
  },
  {
    ava: user,
    name: '东田测试团队',
    msg: '为测试设备的运行提供了一个稳定的环境，可以更加高效的对测试设备进行管理，可以实时查看设备的状态以及各种信息，对温度指标设置监控警报，提升了测试设备的使用寿命。'
  },
  {
    ava: th8,
    name: '望尘科技测试部负责人',
    msg: 'PAWAO提供的一站式硬件套餐与Sonic开源平台配合，让中小企业能快速搭建属于自己的云真机基础平台，解决了公司测试机多管理难/使用效率低等痛点。其中散热/控温/断电功能也解决了设备长期使用电池鼓包甚至起火的后顾之忧。'
  },
])
</script>

<style lang="scss" scoped>
.cabinet-avatar .el-avatar {
  background: #ffffff;
}

@keyframes slide {
  0% {
    transform: translateX(-25%);
  }
  100% {
    transform: translateX(25%);
  }
}

.os-bg-base {
  animation: slide 3s ease-in-out infinite alternate;
  background-image: linear-gradient(-60deg, #000000 50%, #606266 50%);
  bottom: 0;
  left: -50%;
  opacity: 0.5;
  position: absolute;
  right: -50%;
  top: 0;
  z-index: -1;
}

.os-bg1 {
  animation-direction: alternate-reverse;
  animation-duration: 4s;
}

.os-bg2 {
  animation-duration: 5s;
}

.cabinet-open-screen {
  position: relative;
  padding: 200px 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  overflow-x: hidden;
}

.brand-slogan-cabinet {
  margin-top: 0;
  margin-bottom: 24px;
  color: #ffffff;
  font-size: 2.2rem;
  line-height: 2.2rem;
  font-weight: bold;
}

.brand-desc-cabinet {
  margin: 12px 0;
  color: #fafcff;
  font-weight: bold;
}

.capacity-wrapper-cabinet {
  display: flex;
  justify-content: center;
  margin-top: 50px;
}

.capacity-video {
  width: 780px;
  height: 440px;
}

.capacity-video-2 {
  width: 254px;
  height: 450px;
}

.capacity-list {
  margin-left: 40px;
}

.capacity-list-2 {
  margin-right: 60px;
}

.card-content {
  width: 180px;
}

.use-case-cabinet {
  display: flex;
  justify-content: flex-start;
  flex-wrap: wrap;
  width: 1200px;
  margin: 0 auto;
}

.product-name {
  font-size: 18px;
  font-weight: bold;
  margin: 18px 0;
}

.product-img {
  height: 240px;
  object-fit: contain;
}

.case-card-wrapper {
  width: 270px;
  margin-bottom: 20px;
  margin-right: 20px;
}

.case-card-content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  p {
    margin-bottom: 16px;
  }
}

.using-container {
  width: 1200px;
  margin: 0 auto;
  padding: 3% 5% 0 5%;
}

.icon-container {
  width: 900px;
  margin: 0 auto;
  padding: 0 5% 0 5%;
}

.profit-container {
  width: 1200px;
  margin: 0 auto;
}

.footer-container {
  width: 1200px;
  margin: 0 auto;
}

@media screen and (max-width: 820px) {
  .container {
    width: 100%;
    margin: 0 auto;
  }

  .card-content {
    width: 165px;
    margin-bottom: 14px;
  }

  .case-content {
    width: 170px;
    margin-bottom: 10px;
  }

  .capacity-wrapper-cabinet {
    position: relative;
    display: inline-block;
    margin-top: 10px;
  }
}
</style>
