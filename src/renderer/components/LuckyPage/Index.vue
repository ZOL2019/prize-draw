<template>
  <div>
    <div class="main-style">
      <div class="text-center title-main-top">【咸鱼帮会】-【钱多多】-【蓬莱门】</div>
      <div class="text-center title-main-tip">[剑侠情缘网络版3]-[95赛季]-[抽奖盛典]</div>
      <div class="content-main">
        <div class="text-center lucky-input">
          <label>抽奖幸运儿：</label>
          <input type="text" v-model="LuckyName" placeholder="请输入幸运儿名称" />
          <button @click="LuckyClick()">开始</button>
        </div>
        <div class="text-center lucky-random">
          <div style="float: left; width: 50%">
            <div style="color: #dd3384; font-weight: bold; text-align: left">奖品一览</div>
            <div style="font-size: 12px;">
              <ol>
                <li><span style="color: #ff1642">锦鲤:大礼包一份</span>
                  <ul>
                    <li>@十七（15元点卡）</li>
                    <li>@二宝（一个月大战代练）</li>
                    <li>@伍芽芽（摸宠奇遇一圈包撩物品）</li>
                    <li><span style="color: #1f8ddd">@师父父（大礼包一份）</span>
                      <ul>
                        <li># 10000枚金币-新赛季助力装备买买买！</li>
                        <li># 1000个青铜宝箱-新赛季助力材料、五行石等快速获取！</li>
                        <li># 1000颗1级五彩石-新赛季助力五彩石属性加成！</li>
                        <li># 100颗马草-新赛季撩汉必备！</li>
                        <li># 10个24格背包-新赛季扩容必备！</li>
                        <li># 1个百级藏宝洞-新赛季第一件藏宝洞装备！</li>
                        <li># 10匹马驹-新赛季爱徒养成必备！</li>
                        <li># 3匹小绿-新赛季小号跑商必备！</li>
                        <li># 3个官方通达卷礼包 12月31日前 领取</li>
                        <li># 1个官方重置版新手礼包 12月31日前 领取</li>
                        <li> # 1个五级五彩石-新赛季助力装备伤害加成！</li>
                        <li># 1个百级藏宝洞-新赛季第一件藏宝洞装备！</li>
                      </ul>
                    </li>
                  </ul>
                </li>
                <li><span style="color: #e252da">师门:随机礼包</span>
                  <ul>
                    <li># 若干 四、三、二、一级 五彩石-新赛季高级 五彩石 原石必备！</li>
                    <li># 若干 四、三、二、一级 五行石-新赛季高级 五行石 原石必备！</li>
                    <li># 若干 福禄、精铁、锡制、青铜 宝箱-新赛季随缘抽奖必备！</li>
                    <li># 若干 肉食类、草药类、锦缎类、矿石类 茶馆材料-新赛季日常必备！</li>
                    <li># 若干图谱-新赛季拓印必备！</li>
                    <li># 若干飞沙令-新赛季吃鸡必备！</li>
                    <li># 若干名剑币-新赛季竞技场必备！</li>
                    <li># 若干威望值-新赛季阵营必备！</li>
                    <li># 其他奖励-新赛季吃鸡小伙伴一枚！</li>
                    <li># 其他奖励-新赛季竞技场小伙伴一枚！</li>
                    <li># 其他奖励-新赛季阵营小伙伴一枚！</li>
                    <li># 其他奖励-新赛季咸鱼小伙伴一枚！</li>
                    <li># # 补充奖励-???</li>
                  </ul>
                </li>
                <li><span style="color: #37a8ff">师门:基础小礼包</span>
                  <ul>
                    <li># 1颗四级五彩石-新赛季六级五彩石原石必备！</li>
                    <li># 若干生活材料-随缘材料！</li>
                    <li># 一份 2018.12.20 师门截图</li>
                  </ul>
                </li>
              </ol>
            </div>
          </div>
          <div style="float: left; width: 50%">
            <div style="text-align: left">
              <ul v-for="(lucky,index) in LuckyList">
                <li>{{lucky.name}}:{{lucky.detail}}</li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import IndexPage from '../IndexPage'
export default {
    components: {IndexPage},
    data () {
      return {
        LuckyName: '',
        LuckyList: []
      }
    },
    methods: {
      LuckyClick () {
        if (this.LuckyName) {
          const detail = this.getLucky()
          this.LuckyList.push({
            name: this.LuckyName,
            detail: detail
          })
        }
      },
      getLucky () {
        const random = []
        for (let i = 0, len = 4; i < len; i++) {
          const randomNumber = ((Math.random() * 1000 % 1000 + 1)).toString().substr(0, 3)
          random.push(randomNumber)
        }
        return random
      },
      getLuckyGift () {
        const gift = []
        for (let i = 0, len = 1; i < len; i++) {
          gift.push('锦鲤:大礼包一份')
        }
        for (let i = 0, len = 30; i < len; i++) {
          gift.push('师门:随机礼包')
        }
        for (let i = 0, len = 100; i < len; i++) {
          gift.push('师门:基础小礼包')
        }
        return gift
      }
    }
  }
</script>

<style scoped lang="scss">
  $margin_main: 0 auto;
  $width_main: 100%;
  $width_height: 720px;
  $title_size: 16px;
  $title_color_top: #ff310d;
  $title_color_tip: #ff1ef9;
  $content_size: 14px;
  $content_color: #000;
  $content_main: 960px;
  $lucky_width_input: 600px;
  $lucky_width_button: 100px;
  $lucky_input: 24px;
  $border_style: 1px solide #eee;
  .main-style{
    margin: $margin_main;
    width: $width_main;
    min-height: $width_height;
    background-color: #eee;
  }
  .text-center{
    text-align: center;
  }
  .text-left{
    text-align: left;
  }
  .title-main-top{
    padding: 20px;
    font-size: $title_size;
    color: $title_color_top;
  }
  .title-main-tip{
    font-size: $title_size;
    color: $title_color_tip;
  }
  .content-main{
    margin: 20px;
    width: 100%;
    font-size: $content_size;
    color: $content_color;
  }
  .lucky-input input{
    width: $lucky_width_input;
    height: $lucky_input;
  }
  .lucky-input button{
    width: $lucky_width_button;
    height: $lucky_input + 5px;
    background-color: orange;
  }
  .lucky-random{
    margin: 20px;
  }
  ol li {
    text-align: left;
    font-size: 12px;
  }
</style>
