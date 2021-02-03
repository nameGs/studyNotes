# E-charts

```javascript
option = {
    legend: {},
    tooltip: {},
    title:{
        text: '审计日志统计'
    },
    dataset: {
        source: [
            ['product', '成功数', '失败数'],
            ['系统登录', 43.3, 85.8],
            ['菜单访问', 43.3, 85.8],
            ['权限保存', 83.1, 73.4],
            ['人员保存', 86.4, 65.2],
            ['越权访问', 72.4, 53.9],
            ['业务数据变更', 72.4, 53.9],
            ['系统退出', 72.4, 53.9]
        ]
    },
    xAxis: {type: 'category'},
    yAxis: {},
    series: [
        {type: 'bar'},
        {type: 'bar'}
    ]
};
```

