User
<template>
    <div class="my-page">
        <div class="box-head">
            <div class="user-info">
                <div class="user-avatar"><img src="@/assets/images/user.jpg" alt=""></div>
                <div class="info">
                    <div class="info-detail"> <span class="key">账号</span><span>:</span> <span
                            class="value">{{ userInfo.username }}</span></div>
                    <div class="info-detail"> <span class="key">等级</span><span>:</span> <span class="value">{{ userInfo.level }}</span>
                    </div>
                    <div class="info-detail"> <span class="key">USDT</span><span>:</span> <span
                            class="value">{{ userInfo.money }}</span><font-awesome-icon :class="{activeReload:activeIconReload}" @click="reloadUserMoney()" class="icon" :icon="['fas', 'rotate']" /></div>
                </div>
            </div>
            <div class="action">
                <router-link class="link" to="/"><font-awesome-icon class="icon" :icon="['fas', 'credit-card']" />
                    <p class="text">充值</p>
                </router-link>
                <span class="line"></span>
                <router-link class="link" to="/"><font-awesome-icon class="icon" :icon="['fas', 'wallet']" />
                    <p class="text">提现</p>
                </router-link>
            </div>
        </div>
        <div class="menu-bar">
            <ul class="menu-list" ref="menuBar">
                <li class="menu-item" :class="{ active: activeMenuBar == 0 }" @click="handleActiveMenuBar(0)">
                    <font-awesome-icon class="icon" :icon="['fas', 'id-card-clip']" /><span class="text">个人资料</span>
                </li>
                <li class="menu-item" :class="{ active: activeMenuBar == 1 }" @click="handleActiveMenuBar(1)">
                    <font-awesome-icon class="icon" :icon="['fas', 'calendar-days']" /><span class="text">账单明细</span>
                </li>
                <li class="menu-item"><font-awesome-icon class="icon" :icon="['fas', 'envelope']" /><span
                        class="text">站内信</span><router-link class="link" to="#"></router-link></li>
                <li class="menu-item"><font-awesome-icon class="icon" :icon="['fas', 'users']" /><span
                        class="text">代理中心</span> <router-link class="link" to="#"></router-link></li>
                <li class="line"></li>
            </ul>
           
            <ul class="menu-detail-list" >
                <!-- 个人资料 -->
                <li class="menu-detail-item" :class="{ active: activeMenuBar == 0 }">
                    <ul class="sub-menu-list">
                        <li class="sub-menu-item" v-for="item,index in personInfo" :key="index">
                            <div class="left">
                                <font-awesome-icon class="icon" :icon="[...item.icon]" />
                                <p class="text">{{ item.text }}</p>
                            </div>
                            <font-awesome-icon :icon="['fas', 'chevron-right']" />
                            <router-link class="link" :to="item.link"></router-link>
                        </li>
                        <li class="sub-menu-item">
                            <div class="left">
                                <font-awesome-icon class="icon" :icon="['fas', 'arrow-right-from-bracket']" />
                                <p class="text">退出账号</p>
                            </div>
                            <font-awesome-icon :icon="['fas', 'chevron-right']" />
                        </li>
                    </ul>
                </li>

                <!-- 账单明细 -->
                <li class="menu-detail-item" :class="{ active: activeMenuBar == 1 }">
                    <ul class="sub-menu-list">
                        <li class="sub-menu-item" v-for="item,index in billingDetails" :key="index">
                            <div class="left">
                                <font-awesome-icon class="icon" :icon="[...item.icon]" />
                                <p class="text">{{ item.text }}</p>
                            </div>
                            <font-awesome-icon :icon="['fas', 'chevron-right']" />
                            <router-link class="link" :to="item.link"></router-link>
                        </li>

                    </ul>
                </li>
            </ul>
           
        </div>
        <navBar />
    </div>
</template>

User
<script>
import navBar from '@/components/navBar.vue';
export default {
    components: {
        navBar
    },
    data() {
        return {
            activeMenuBar: 0,
            personInfo: [
                {
                    icon: ['far', 'address-book'],
                    text: '个人信息',
                    link: '/#',
                },
                {
                    icon: ['far', 'credit-card'],
                    text: '提款账号管理',
                    link: '/#'
                },
                {
                    icon: ['fas', 'lock'],
                    text: '密码设置',
                    link: '/#'
                },
                {
                    icon: ['far', 'circle-question'],
                    text: '帮助中心',
                    link: '/#'
                }   
            ],
            billingDetails: [
                {
                    icon: ['far', 'calendar-days'],
                    text: '投注记录',
                    link: '/#',
                },
                {
                    icon: ['fas', 'arrow-right-arrow-left'],
                    text: '账变记录',
                    link: '/#'
                },
                {
                    icon: ['fas', 'file-invoice'],
                    text: '充值记录',
                    link: '/#'
                },
                {
                    icon: ['fas', 'file-invoice-dollar'],
                    text: '提现记录',
                    link: '/#'
                }  ,
                {
                    icon: ['fas', 'square-poll-vertical'],
                    text: '个人盈亏',
                    link: '/#'
                }   
            ],
            userInfo:{
                username:'ceshi2233',
                level:'vip1',
                money:'19007'
            },
            activeIconReload:false
        }
    },
    methods: {
        handleActiveMenuBar(menuIndex) {
            this.activeMenuBar = menuIndex
            const menuBar = this.$refs.menuBar;
            const elementOfsetLeft = menuBar.querySelectorAll('.menu-item')[menuIndex].offsetLeft
            menuBar.lastChild.style.left = elementOfsetLeft + 'px'
            
        },
        reloadUserMoney(){
            this.activeIconReload = true;
            console.log('reload user money')
        }
    }
}
</script>