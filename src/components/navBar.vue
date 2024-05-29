<template>
    <div class="nav-com">
        <ul class="nav-list" ref="navRef">
            <li class="nav-item" :class="{ active: activeIndex == 0 }" @click="changeNav(0, $event)">
                <router-link class="link" to="/">
                    <span class="icon"><font-awesome-icon :icon="['fas', 'house']" /></span>
                    <span class="text">首页</span>
                </router-link>
            </li>
            <li class="nav-item" :class="{ active: activeIndex == 1 }" @click="changeNav(1, $event)">
                <router-link class="link" to="#">
                    <span class="icon"><font-awesome-icon :icon="['fas', 'chart-line']" /></span>
                    <span class="text">引用</span>
                </router-link>
            </li>
            <li class="nav-item" :class="{ active: activeIndex == 2 }" @click="changeNav(2, $event)">
                <router-link class="link" to="#">
                    <span class="icon"><font-awesome-icon :icon="['fas', 'money-bill-trend-up']" /></span>
                    <span class="text">交易</span>
                </router-link>
            </li>
            <li class="nav-item" :class="{ active: activeIndex == 3 }" @click="changeNav(3, $event)">
                <router-link class="link" to="#">
                    <span class="icon"><font-awesome-icon :icon="['fas', 'headset']" /></span>
                    <span class="text">客服</span>
                </router-link>
            </li>
            <li class="nav-item" :class="{ active: activeIndex == 4 }" @click="changeNav(4)">
                <router-link class="link" :class="{ active: $route.path == '/my' }" to="/my">
                    <span class="icon"> <font-awesome-icon :icon="['fas', 'user']" /></span>
                    <span class="text">我</span>
                </router-link>
            </li>
            <div class="indicator" ref="indicator"></div>
        </ul>
    </div>
</template>

<script>

export default {
    data() {
        return {
            activeIndex: 0

        }
    },
    mounted() {

        this.getLiPosition(0)
    },
    methods: {
        changeNav(index, e) {
            this.activeIndex = index;
            this.getLiPosition(index)
        },
        getLiPosition(index) {

            let navRef = this.$refs.navRef;
            let indicator = this.$refs.indicator;
            const firstLi = navRef.children[index].querySelector('.link .icon');
            console.log(firstLi);

            if (firstLi) {
                const position = firstLi.getBoundingClientRect();
                console.log(position);
                indicator.style.left = `${position.left - 14}px`;
            }
        }
    },

}
</script>

<style lang="scss" scoped>
.nav-com {
    width: 100%;
    position: fixed;
    bottom: 0;
    height: 52px;
    max-width: 1280px;
    box-shadow: 0px 0px 4px 0px #ccc;
    padding-top: 2px;
    background-color: #ddd;

    .nav-list {
        display: flex;
        align-items: center;
        justify-content: space-between;
        height: 100%;

        .nav-item {
            flex: 1;
            height: 100%;
            position: relative;

            .link {
                display: flex;
                flex-direction: column;
                justify-content: center;
                align-items: center;
                font-size: 14px;
                position: relative;
                width: 100%;
                color: var(--color-depthSellBg);
                text-align: center;


                .icon {
                    position: relative;
                    display: block;
                    font-size: 1.5rem;
                    line-height: 52px;
                    font-weight: 500;
                    transition: 0.5s;
                    z-index: 1;
                }

                .text {
                    position: absolute;
                    opacity: 0;
                    font-size: 16px;
                    font-weight: 400;
                    transition: 0.5s;
                    transform: translateY(10px);
                }

            }

            &.active {
                .link {
                    .icon {
                        transform: translateY(-30px);
                    }

                    .text {
                        opacity: 1;
                        transform: translateY(5px);
                    }
                }

            }

        }

        .indicator {
            position: absolute;
            background-color: var(--color-primary);
            width: 52px;
            height: 52px;
            top: -50%;
            border-radius: 50%;
            border: 4px solid white;

            transition: 0.5s;

            &::before {
                content: '';
                position: absolute;
                top: 21px;
                left: -20px;
                width: 20px;
                height: 20px;
                background-color: transparent;
                border-top-right-radius: 20px;
                box-shadow: 0px -10px 0px 0px #fff;
            }

            &::after {
                content: "";
                position: absolute;
                top: 21px;
                right: -20px;
                width: 20px;
                height: 20px;
                background-color: transparent;
                border-top-left-radius: 20px;
                box-shadow: 0px -10px 0px 0px #fff;
            }
        }
    }
}
</style>