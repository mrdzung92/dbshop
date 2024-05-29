<template>
    <div class="chart-box">
        <ul class="select-list">
            <li class="select-item">1M</li>
            <li class="select-item">5M</li>
            <li class="select-item">15M</li>
            <li class="select-item">30M</li>
            <li class="select-item">1H</li>
            <li class="select-item">1D</li>
        </ul>
        <div class="chart-container">
            <highcharts :options="chartOptions"></highcharts>
        </div>
    </div>
</template>

<script>
import { Chart } from 'highcharts-vue'
const demoData = [


    [
        1317894120000,
        376.8336,
        377.88,
        376.8289,
        377.55
    ],
    [
        1317894180000,
        377.36,
        377.9,
        376.52,
        376.75
    ],
    [
        1317894240000,
        376.83,
        377.73,
        376.71,
        376.98
    ],
    [
        1317894300000,
        377,
        377.69,
        376.87,
        377.1212
    ],
    [
        1317894360000,
        377.225,
        377.33,
        376.01,
        376.26
    ],
    [
        1317894420000,
        376.42,
        376.64,
        375.55,
        375.5534
    ],
    [
        1317894480000,
        375.74,
        375.94,
        374.77,
        375.3
    ],
    [
        1317894540000,
        375.3313,
        376,
        374.92,
        375.06
    ],
    [
        1317894600000,
        375.11,
        375.46,
        374.82,
        374.92
    ],
    [
        1317894660000,
        374.82,
        375.68,
        374.64,
        375.668
    ],
    [
        1317894720000,
        375.62,
        376.13,
        375.46,
        376.13
    ],
    [
        1317894780000,
        376.14,
        376.6,
        375.89,
        376.34
    ],
    [
        1317894840000,
        376.39,
        376.39,
        375.55,
        375.99
    ],
    [
        1317894900000,
        376,
        376.28,
        375.42,
        376.21
    ],
    [
        1317894960000,
        376,
        377.38,
        375.7,
        376.591
    ],
    [
        1317895020000,
        376.59,
        377.46,
        376.57,
        376.9348
    ],
    [
        1317895080000,
        376.9481,
        377.749,
        376.84,
        377.563
    ],
    [
        1317895140000,
        377.452,
        377.65,
        376.43,
        376.78
    ],
    [
        1317895200000,
        376.94,
        377.01,
        375.75,
        375.98
    ],
    [
        1317895260000,
        376.27,
        377.29,
        375.95,
        376.98
    ],
    [
        1317895320000,
        376.9962,
        377.3,
        376.69,
        376.71
    ],
    [
        1317895380000,
        376.75,
        377.5,
        376.75,
        377.41
    ],
    [
        1317895440000,
        377.26,
        377.49,
        376.89,
        377.368
    ],
    [
        1317895500000,
        377.345,
        378,
        377.17,
        378
    ],
    [
        1317895560000,
        377.97,
        378.3199,
        377.68,
        377.97
    ],
    [
        1317895620000,
        378.01,
        378.07,
        377.25,
        377.37
    ],
    [
        1317895680000,
        377.37,
        377.75,
        377.05,
        377.12
    ],
    [
        1317895740000,
        377.16,
        377.79,
        377.01,
        377.4512
    ]
];
export default {
    data() {
        return {
            chartOptions: {
                rangeSelector: {
                    enabled: !1
                },
                credits: {
                    enabled: !1
                },
                scrollbar: {
                    enabled: !1
                },
                navigator: {
                    enabled: !1
                },
                // title: {
                //     text: '<div class="titleChartCandle d-flex align-items-center"><span class="iconBTC iconETH"></span><span class="textPrice">ETH/USDT</span></div>',
                //     align: "left",
                //     useHTML: !0
                // },
                chart: {
                    panning: !1,
                    followTouchMove: !1,
                    zoomType: "",
                    height: '400px',
                    backgroundColor: "#12013E",
                    plotBackgroundImage: "/images/world_map.svg",
                    // marginRight: "pc" !== deviceVersion ? 70 : 80,
                    // marginBottom: "pc" !== deviceVersion ? 25 : 30,
                    pinchType: '',
                    resetZoomButton: {
                        theme: {
                            display: "none"
                        }
                    },
                    animation: {
                        duration: 700
                    }
                },
                navigation: {
                    bindingsClassName: "tools-container"
                },
                stockTools: {
                    gui: {
                        enabled: !1
                    }
                },
                plotOptions: {
                    candlestick: {
                        lineColor: "#FC5F5F",
                        upLineColor: "#31BAA0",
                        // pointWidth: "pc" !== deviceVersion ? 9 : 10,
                        // maxPointWidth: "pc" !== deviceVersion ? 9 : 10
                    },
                    column: {
                        minPointLength: 2,
                        // pointWidth: "pc" !== deviceVersion ? 11.2 : 11,
                        // maxPointWidth: "pc" !== deviceVersion ? 11.2 : 11,
                        borderWidth: 0,
                        pointPadding: 0,
                        groupPadding: 0
                    },
                    series: {
                        zIndex: 2,
                        states: {
                            inactive: {
                                opacity: 1
                            }
                        },
                        allowPointSelect: !1,
                        point: {
                            events: {
                                click: function (t) { }
                            }
                        }
                    }
                },
                xAxis: [{
                    type: "datetime",
                    labels: {
                        enabled: !0,
                        // formatter: function () {
                        //     return moment(this.value).format("mm:ss")
                        // },
                        style: {
                            fontSize: 10,
                            color: "#707070"
                        }
                    },
                    plotLines: [{
                        value: 1580717085410,
                        color: "#ffffff",
                        width: .75,
                        id: "current-pricex",
                        zIndex: 1e3,
                        dashStyle: "LongDash"
                    }],
                    lineWidth: 0,
                    minorGridLineWidth: 0,
                    lineColor: "transparent",
                    minorTickLength: 0,
                    tickLength: 0
                }],
                yAxis: [
                    {
                        opposite: true,
                        gridLineColor: "#35275B",
                        labels: {
                            align: "right",
                            // x: "pc" !== deviceVersion ? 45 : 50,
                            style: {
                                color: "#fff",
                                fontSize: "11px"
                            },
                            formatter: function () {
                                return this.value / 1000 + 'k';
                            }
                        },
                        height: "85%",
                        // top: "pc" === deviceVersion ? 0 : null,
                        plotLines: [{
                            value: 0,
                            color: "#ffffff",
                            width: .75,
                            id: "current-price",
                            zIndex: 100,
                            label: {
                                useHTML: !0,
                                text: 0,
                                // x: "pc" !== deviceVersion ? 60 : 70,
                                align: "right",
                                style: {
                                    color: "#fff",
                                    fontSize: "11px",
                                    background: "transparent",
                                    borderRadius: "4px"
                                }
                            }
                        }],
                        lineWidth: 0,
                        resize: {
                            enabled: !0
                        }
                    },

                    {

                        gridLineColor: "",
                        visible: !1,
                        title: {
                            align: "high",
                            text: null,
                            rotation: 0,
                            y: 0,
                            useHTML: !0
                        },
                        // top: "pc" === deviceVersion ? "83.4%" : "85%",
                        height: "15%",
                        lineWidth: 0,
                        offset: 0
                    }
                ],
                // tooltip: {
                //     split: !1,
                //     enabled: !0,
                //     label: !1,
                //     animation: !1,
                //     backgroundColor: "transparent",
                //     borderColor: "transparent",
                //     borderWidth: 0,
                //     stroke: "transparent",
                //     useHTML: !0,
                //     style: {
                //         color: "#fff",
                //         fontSize: "12px",
                //         stroke: "transparent"
                //     },
                //     formatter: function () {
                //         return "ETH/USDT" === this.series.name ? '<span style="margin-right: 10px;"><b>O</b>: '
                //             + formatDecimalNotRound(this.point.open, "", 2) + '</span><span style="margin-right: 10px;"><b>C</b>: '
                //             + formatDecimalNotRound(this.point.close, "", 2) + '</span><span>&nbsp;</span><br/><span style="margin-right: 10px;"><b>H</b>: '
                //             + formatDecimalNotRound(this.point.high, "", 2) + '</span><span style="margin-right: 10px;"><b>L</b>: '
                //             + formatDecimalNotRound(this.point.low, "", 2) + "</span><span><b>Vol</b>: "
                //             + formatDecimalNotRound(this.point.vol, "", 2) + "</span>" : "Volume" === this.series.name ? "<b>Vol</b>: "
                //                 + formatDecimalNotRound(this.y, "", 2) : "";
                //     },
                //     positioner: function () {
                //         var t = 20
                //             , e = 60;
                //         return deviceHeight <= 667 && deviceWidth <= 414 ? (t = 50,
                //             e = this.chart.plotSizeY - 50) : deviceWidth >= 375 && deviceHeight >= 667 && deviceWidth <= 1024 && (t = 50,
                //                 e = this.chart.plotSizeY - 100),
                //         {
                //             x: t,
                //             y: e
                //         }
                //     }
                // },
                series: [
                    {
                        id: "aapl",
                        type: "candlestick",
                        name: "ETH/USDT",
                        color: "#FC5F5F",
                        upColor: "#31BAA0",
                        point: {},
                        lastPrice: {
                            enabled: true,
                            label: {
                                enabled: true,
                                backgroundColor: '#FF7F7F',

                            }
                        },
                        data: demoData,


                    },
                    {
                        type: "column",
                        name: "Volume",
                        point: {},
                        // data: demoData,
                        yAxis: 1
                    },
                ]
            },

        }
    },
    mehthod: {
        getNewPoint(i, data) {
            const lastPoint = data[data.length - 1];
        }
    }
}
</script>

<style lang="scss" scoped></style>