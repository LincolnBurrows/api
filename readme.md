#### 1 添加教练信息

post  https://yunying.digitgolf.com/coach/add    

```
request form-data:
{
  coachName : '滴滴', // 姓名 
  gender:'男', //性别
  avatarUrl: 'https://thirdwx.qlogo.cn/mmopen/vi_32/fndXt7CVrdEll4znPM5MAD0nfJCDuqCYS1xvkmqArmj9rEym8Za7aofBrjndvLNIIkPcphibfeaZibhPIfdMGGTA/132'， //头像
   level:0, // 教练等级 0:初级教练  1:中级教练 2:高级教练 3:国家级教练  4:国际级教练
    introduction: '好教练'，// 介绍
    clubId：'101', //教练所属的高尔夫门店id
    phone: '15111111111', //手机号
    timesLimit：5, // 每日可预约次数
    orderBeginTime:'00:00:00', // 可预约开始时间
    orderEndTime：'24:00:00', //可预约结束时间
    expense：200，// 每节费用
    expensePercent: '10%' // 每节费用百分比
    isInner: true // 内部还是外聘
}
```

```
response:
{
    "code": 0,
    "msg": "coach add success"
}
{
  	code:2,
  	msg:'ShareGolf DB error'
}
```

#### 2 添加高尔夫卡（课程卡、E卡、特惠卡）

post	 http://yunying.digitgolf.com/golfcard/add 

```
request form-data:
{
  cardName: '成人私教卡现场1V1教学23节课', //卡名称
  coachLevel：'中级教练', //教练等级
    golfClub：'北京city高尔夫会所' , //门店名称
    timeValid：'30', //有效期30天
    cardStart：'2022-07-13 12:00', // 卡上架开始时间
    cardEnd：'2022-08-13 12:00', //卡上架结束时间
    cardStatus: '上架中'， // 卡状态
    cardPrice：'4000' //卡价格
    cardType：'成人私教课' // 卡类型
    cardTimes：'23', //卡次数  若为 9999表示无限畅达卡
	giveTimes:'5' , //赠送次数
    discountMoney：'0' //优惠金额
    discountPercent：'0' // 优惠百分比
    useRule：'1天10次4小时', //使用规则
    cardIntro：'非常好的课程卡', //卡介绍
    remarks：'0', //购买限制：0 无限制 ，1 限首次购卡用户，2：限每人限购2次 以此类推
    cardKind:'0', //卡的种类：0：课程卡，1：E卡，
    cardimg:'https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/adult.jpg', //封面图
    clubId:'101',// 门店id
    cardGrant：'0' //0：普通卡 1 特惠卡
    dayLimit:'1',  // 参看userRule
    timesLimit:'10', // 参看userRule
    hoursLimit:'4' // 参看userRule
}
```

```
response:
{
    "code": 0,
    "msg": "coach add success"
}
```

#### 3 添加高尔夫门店

post	 https://yunying.digitgolf.com/golfclub/add 

```
{
    clubId: '102', //门店id
    clubType：'0', //0：非无人值守  1：无人值守
    clubName：'中通数字高尔夫旗舰店'， //门店名称
    address：'xxx'， //门店地址
    latitude：'20', //纬度
    longitude：'30', //经度
    intro:'旗舰店', // 门店介绍
    hotline:'10086', //热线
    payType：'0', //支付类型 0不支持线上支付  1 支持线上支付 
    openTime:'00:00:00',// 营业开门时间
    closeTime:'24:00:00'//营业关门时间
    imglogo:'https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/golfclubdefault/golfclublogo.jpg' //
}
```

```
{
  	code:0,
  	msg:'club add success'
 }

{
  	code:2,
  	msg:'ShareGolf DB error'
 }
```

#### 4 高尔夫门店添加打位

post	 https://yunying.digitgolf.com/golfclub/addhitpos 

```
{
    clubId:'100', //门店id
    posname: '包间2', //打位名称
    type:'0', //0 普通打位 1 无人值守
    posimg: "https://yunying.digitgolf.com/images/8c6xabkfnin.jpg", // 打位照片
    priceList:[
      {
        week: 1,  #星期一
        status:1,  #1开启 0 关闭	
        time: [
          {
            time_id:'xxxxxxxx', #时间段id, 随机生成多位字符串id， 比如 Math.random().toString(36).substr(2, 15)
            startTime: 08:00, #开始时间
            endTime: 16:00, #结束时间
            price: 40  #价格
          },
          {
            time_id:'xxxxxxxx',
            startTime: 16:00,
            endTime: 24:00,
            price: 60
          }
        ]
      },
      {
        week: 2,
        status:1,
        time: [
          {
            time_id:'xxxxxxxx', #时间段id, 随机生成多位字符串id， 比如 Math.random().toString(36).substr(2, 15)
            startTime: 08:00, #开始时间
            endTime: 16:00, #结束时间
            price: 40  #价格
          },
          {
            time_id:'xxxxxxxx',
            startTime: 16:00,
            endTime: 24:00,
            price: 60
          }
        ]
      },
      {
        week: 3,
        status:1,
        time: [
          {
            time_id:'xxxxxxxx', #时间段id, 随机生成多位字符串id， 比如 Math.random().toString(36).substr(2, 15)
            startTime: 08:00, #开始时间
            endTime: 16:00, #结束时间
            price: 40  #价格
          },
          {
            time_id:'xxxxxxxx',
            startTime: 16:00,
            endTime: 24:00,
            price: 60
          }
        ]
      },
      {
        week: 4,
        status:1,
        time: [
           {
            time_id:'xxxxxxxx', #时间段id, 随机生成多位字符串id， 比如 Math.random().toString(36).substr(2, 15)
            startTime: 08:00, #开始时间
            endTime: 16:00, #结束时间
            price: 40  #价格
          },
          {
            time_id:'xxxxxxxx',
            startTime: 16:00,
            endTime: 24:00,
            price: 60
          }
        ]
      },
      {
        week: 5,
        status:1,
        time: [
          {
            time_id:'xxxxxxxx', #时间段id, 随机生成多位字符串id， 比如 Math.random().toString(36).substr(2, 15)
            startTime: 08:00, #开始时间
            endTime: 16:00, #结束时间
            price: 40  #价格
          },
          {
            time_id:'xxxxxxxx',
            startTime: 16:00,
            endTime: 24:00,
            price: 60
          }
        ]
      },
      {
        week: 6,
        status:1,
        time: [
          {
            time_id:'xxxxxxxx', #时间段id, 随机生成多位字符串id， 比如 Math.random().toString(36).substr(2, 15)
            startTime: 08:00, #开始时间
            endTime: 16:00, #结束时间
            price: 40  #价格
          },
          {
            time_id:'xxxxxxxx',
            startTime: 16:00,
            endTime: 24:00,
            price: 60
          }
        ]
      },
      {
        week: 7,
        status:1,
        time: [
          {
            time_id:'xxxxxxxx', #时间段id, 随机生成多位字符串id， 比如 Math.random().toString(36).substr(2, 15)
            startTime: 08:00, #开始时间
            endTime: 16:00, #结束时间
            price: 40  #价格
          },
          {
            time_id:'xxxxxxxx',
            startTime: 16:00,
            endTime: 24:00,
            price: 60
          }
        ]
      }
    ]
}
```

```
{
    code:0,
    msg:'position add success'
}
{
    code:1,
    msg:'club not exist'
}
{
  code:2,
  msg:'ShareGolf DB error'
}
{
    code:3,
    msg:'clubId err'
}
```

#### 5 获取昨日和今日数据

get	 https://yunying.digitgolf.com/w/datanum?clubId=101   

```
{
    clubId:'101' // 门店id
}
```

```

    {
    "code": 0,
    "todayOrderNum": 0, //今日预约量
    "lastdayOrderNum": 0, //昨日预约数量
    "todaycourseCardNum": 0, //今日课程卡数量
    "lastdaycourseCardNum": 0,//昨日课程卡数量
    "todayECardNum": 1, //今日e卡数量
    "lastdayECardNum": 0,//昨日e卡数量
    "todaytehuiCardNum": 0,//今日特惠卡数量
    "lastdaytehuiCardNum": 0, //昨日特惠卡数量
    "todayUserNum": 0, //今日用户数量
    "lastdayUserNum": 0, //昨日用户数量
    "msg": "SUCCESS"
}

```

#### 6 获取最新的预约数据(最近的4个)

get	 https://yunying.digitgolf.com/w/getLatestOrder?clubId=101 

```
{
    clubId:'101' //门店id
}
```

```
{
    "code": 0,
    "data": [
        {
            "xtype": 1, // 订单类型 0：充值 1：预约订单  2：卡订单
            "orderId": "202209141035006727447588", // 预约订单id
            "transaction_id": "", //微信支付交易id
            "openid": "o99bm4uBHHMRhUMleN0SHmSjDeig", //用户id
            "nickName": "🌞", //昵称
            "phone": "15662170259", //手机号
            "clubId": "101", // 门店id
            "clubName": "北京中通数字高尔夫体验店", //门店名称
            "payType": "0", // 门店支付类型 0不支持线上支付  1 支持线上支付
            "coachId": "", // 教练id
            "coachName": "", //教练姓名
            "coachLevel": "",//教练等级 0:初级教练  1:中级教练 2:高级教练 3:国家级教练  4:国际级教练
            "coachGender": "",//教练性别
            "serviceType": "打球", // 预约订单类型
            "posid": "u15po15atgi",//打位id
            "hitposition": "包间1",//打位名称
            "totalFee": 0.02, //总额
            "orderDate": "2022-09-14", //预约日期
            "orderTime": "2022-09-14 10:34:45", //预约时间
            "startTime": "2022-09-14 10:40:00",// 预约开始时间
            "endTime": "2022-09-14 12:40:00", //预约结束时间
            "duration": "2", //预约时长
            "payManner": 2, //支付方式 0 微信支付 1 余额支付 2 还没有支付 3 后台支付 4 卡支付
            "golfcardOrderId": "", // 如果是卡支付,则设置卡的golfcardOrderId
            "status": 2, //预约订单状态 0：待付款 1：待使用 2：已取消 3：已使用 4：进行中 注：过期未使用也算已使用 status=5是已退款
            "remarks": "",  //订单备注信息
            "TimeStamp": 1663121913225, //时间戳
            "_id": "63213dd4830084076342f078"
        },
        {
            "xtype": 1,
            "orderId": "202209051727595845472226",
            "transaction_id": "",
            "openid": "o99bm4uBHHMRhUMleN0SHmSjDeig",
            "nickName": "🌞",
            "phone": "15662170259",
            "clubId": "101",
            "clubName": "北京中通数字高尔夫体验店",
            "payType": "0",
            "coachId": "",
            "coachName": "",
            "coachLevel": "",
            "coachGender": "",
            "serviceType": "打球",
            "posid": "1",
            "hitposition": "打位1",
            "totalFee": 0.01,
            "orderDate": "2022-09-08",
            "orderTime": "2022-09-05 17:27:58",
            "startTime": "2022-09-08 00:00:00",
            "endTime": "2022-09-08 01:00:00",
            "duration": "1",
            "payManner": 2,
            "golfcardOrderId": "",
            "status": 2,
            "remarks": "",
            "TimeStamp": 1662365452201,
            "_id": "6315c11fec96e4755632f1ed"
        },
        {
            "xtype": 1,
            "orderId": "202209051724564810282723",
            "transaction_id": "",
            "openid": "o99bm4uBHHMRhUMleN0SHmSjDeig",
            "nickName": "🌞",
            "phone": "15662170259",
            "clubId": "101",
            "clubName": "北京中通数字高尔夫体验店",
            "payType": "0",
            "coachId": "",
            "coachName": "",
            "coachLevel": "",
            "coachGender": "",
            "serviceType": "打球",
            "posid": "1",
            "hitposition": "打位1",
            "totalFee": 0.01,
            "orderDate": "2022-09-07",
            "orderTime": "2022-09-05 17:24:55",
            "startTime": "2022-09-07 00:00:00",
            "endTime": "2022-09-07 01:00:00",
            "duration": "1",
            "payManner": 2,
            "golfcardOrderId": "",
            "status": 2,
            "remarks": "",
            "TimeStamp": 1662365452201,
            "_id": "6315c068ec96e4755632f1ec"
        },
        {
            "xtype": 1,
            "orderId": "202209051722344245176361",
            "transaction_id": "",
            "openid": "o99bm4uBHHMRhUMleN0SHmSjDeig",
            "nickName": "🌞",
            "phone": "15662170259",
            "clubId": "101",
            "clubName": "北京中通数字高尔夫体验店",
            "payType": "0",
            "coachId": "",
            "coachName": "",
            "coachLevel": "",
            "coachGender": "",
            "serviceType": "打球",
            "posid": "1",
            "hitposition": "打位1",
            "totalFee": 0.01,
            "orderDate": "2022-09-07",
            "orderTime": "2022-09-05 17:22:33",
            "startTime": "2022-09-07 03:00:00",
            "endTime": "2022-09-07 04:00:00",
            "duration": "1",
            "payManner": 2,
            "golfcardOrderId": "",
            "status": 2,
            "remarks": "",
            "TimeStamp": 1662365452201,
            "_id": "6315bfdaec96e4755632f1eb"
        }
    ],
    "msg": "SUCCESS"
}
```

#### 7 获取打位信息

get	https://yunying.digitgolf.com/w/getHitposInfo?clubId=101 

```
{
    clubId:'101' //门店id
}
```

```
{
    "code": 0,
    "data": [
        {
            "posid": "1", //打位id 
            "startTime": "00:00:00", // 打位开始时间
            "endTime": "24:00:00", // 打位结束时间
            "posname": "打位1", //打位名称
	    	"posimg":"https://yunying.digitgolf.com/images/8c6xabkfnin.jpg", //打位照片
            "price": "0.01", //打位价格
            "type": "0", //打位类型 0 普通打位 1 无人值守
            "status": "0" // 打位状态 0开启 1关闭
        },
        {
            "posid": "2",
            "startTime": "00:00:00",
            "endTime": "24:00:00",
            "posname": "打位2",
	    	"posimg":"https://yunying.digitgolf.com/images/8c6xabkfnin.jpg", //打位照片
            "price": "0.01",
            "type": "0",
            "status": "0"
        },
        {
            "posid": "u15po15atgi",
            "posname": "包间1",
	        "posimg":"https://yunying.digitgolf.com/images/8c6xabkfnin.jpg", //打位照片
            "price": "0.01",				
            "startTime": "00:00:00",
            "endTime": "24:00:00",
            "type": "0",
            "status": "0"
        },
        {
            "posid": "1nwbs0xjhm3",
            "posname": "包间2",
	        "posimg":"https://yunying.digitgolf.com/images/8c6xabkfnin.jpg", //打位照片
            "price": "0.01",
            "startTime": "00:00:00",
            "endTime": "24:00:00",
            "type": "0",
            "status": "0"
        }
    ],
    "msg": "SUCCESS"
}
```

#### 8 获取门店所有教练信息

get  https://yunying.digitgolf.com/w/getCoachInfo?clubId=101 

```
{
    clubId:'101' //门店id
}
```

```
{
    "code": 0,
    "data": [
        {
            "clubId": "101",// 门店id
            "coachName": "马云", //教练姓名
            "gender": "男", //教练性别
            "phone": "15111111111", //手机号
            "isInner": true, //是否内部
            "expense": 200, //每节课费用
            "expensePercent": "10%", //每节费用 默认10%
            "avatarUrl": "https://thirdwx.qlogo.cn/mmopen/vi_32/fndXt7CVrdEll4znPM5MAD0nfJCDuqCYS1xvkmqArmj9rEym8Za7aofBrjndvLNIIkPcphibfeaZibhPIfdMGGTA/132", //头像
            "level": "0", //教练等级 0:初级教练  1:中级教练 2:高级教练 3:国家级教练  4:国际级教练
            "timesLimit": 5, // 每天可预约的次数
            "timesUsed": 0, // 每天已经预约的次数
            "hoursLimit": 4, // 每次预约的最大时长
            "isOrderable": true, // 是否可预约
            "orderBeginTime": "00:00:00", // 可预约的开始时间
            "orderEndTime": "24:00:00", // 可预约的结束时间
            "alreadOrderDuration": [], //已经预约的时间段
                /* [{
																				"orderId" : '202208241433271994203913', //预约订单号         		  "orderDate" : "2022-09-01",  //预约日期         						"startTime" : "2022-09-01 15:00:00", //预约开始时间
			 "endTime" : "2022-09-01 16:00:00" // 预约结束时间
       		 	}] */
            "introduction": "好教练",
            "_id": "6319b9118adecb5540371c9f"
        },
        {
            "clubId": "101",
            "coachName": "马化腾",
            "gender": "男",
            "phone": "15111111111",
            "isInner": true,
            "expense": 200,
            "expensePercent": "10%",
            "avatarUrl": "https://thirdwx.qlogo.cn/mmopen/vi_32/fndXt7CVrdEll4znPM5MAD0nfJCDuqCYS1xvkmqArmj9rEym8Za7aofBrjndvLNIIkPcphibfeaZibhPIfdMGGTA/132",
            "level": "0",
            "timesLimit": 5,
            "timesUsed": 0,
            "hoursLimit": 4,
            "isOrderable": true,
            "orderBeginTime": "00:00:00",
            "orderEndTime": "24:00:00",
            "alreadOrderDuration": [],
            "introduction": "好教练",
            "_id": "6319b91f8adecb5540371ca0"
        },
        {
            "clubId": "101",
            "coachName": "李彦宏",
            "gender": "男",
            "phone": "15111111111",
            "isInner": true,
            "expense": 200,
            "expensePercent": "10%",
            "avatarUrl": "https://thirdwx.qlogo.cn/mmopen/vi_32/fndXt7CVrdEll4znPM5MAD0nfJCDuqCYS1xvkmqArmj9rEym8Za7aofBrjndvLNIIkPcphibfeaZibhPIfdMGGTA/132",
            "level": "0",
            "timesLimit": 5,
            "timesUsed": 0,
            "hoursLimit": 4,
            "isOrderable": true,
            "orderBeginTime": "00:00:00",
            "orderEndTime": "24:00:00",
            "alreadOrderDuration": [],
            "introduction": "好教练",
            "_id": "6319b9258adecb5540371ca1"
        },
        {
            "clubId": "101",
            "coachName": "雷军",
            "gender": "男",
            "phone": "15111111111",
            "isInner": true,
            "expense": 200,
            "expensePercent": "10%",
            "avatarUrl": "https://thirdwx.qlogo.cn/mmopen/vi_32/fndXt7CVrdEll4znPM5MAD0nfJCDuqCYS1xvkmqArmj9rEym8Za7aofBrjndvLNIIkPcphibfeaZibhPIfdMGGTA/132",
            "level": "0",
            "timesLimit": 5,
            "timesUsed": 0,
            "hoursLimit": 4,
            "isOrderable": true,
            "orderBeginTime": "00:00:00",
            "orderEndTime": "24:00:00",
            "alreadOrderDuration": [],
            "introduction": "好教练",
            "_id": "6319b92b8adecb5540371ca2"
        },
        {
            "clubId": "101",
            "coachName": "刘强东",
            "gender": "男",
            "phone": "15111111111",
            "isInner": true,
            "expense": 200,
            "expensePercent": "10%",
            "avatarUrl": "https://thirdwx.qlogo.cn/mmopen/vi_32/fndXt7CVrdEll4znPM5MAD0nfJCDuqCYS1xvkmqArmj9rEym8Za7aofBrjndvLNIIkPcphibfeaZibhPIfdMGGTA/132",
            "level": "0",
            "timesLimit": 5,
            "timesUsed": 0,
            "hoursLimit": 4,
            "isOrderable": true,
            "orderBeginTime": "00:00:00",
            "orderEndTime": "24:00:00",
            "alreadOrderDuration": [],
            "introduction": "好教练",
            "_id": "6319b9368adecb5540371ca3"
        },
        {
            "clubId": "101",
            "coachName": "滴滴",
            "gender": "男",
            "phone": "15111111111",
            "isInner": true,
            "expense": 200,
            "expensePercent": "10%",
            "avatarUrl": "https://thirdwx.qlogo.cn/mmopen/vi_32/fndXt7CVrdEll4znPM5MAD0nfJCDuqCYS1xvkmqArmj9rEym8Za7aofBrjndvLNIIkPcphibfeaZibhPIfdMGGTA/132",
            "level": "0",
            "timesLimit": 5,
            "timesUsed": 0,
            "hoursLimit": 4,
            "isOrderable": true,
            "orderBeginTime": "00:00:00",
            "orderEndTime": "24:00:00",
            "alreadOrderDuration": [],
            "introduction": "好教练",
            "_id": "6319b96b8adecb5540371ca4"
        },
        {
            "clubId": "101",
            "coachName": "滴滴",
            "gender": "男",
            "phone": "15111111111",
            "isInner": true,
            "expense": 200,
            "expensePercent": "10%",
            "avatarUrl": "https://thirdwx.qlogo.cn/mmopen/vi_32/fndXt7CVrdEll4znPM5MAD0nfJCDuqCYS1xvkmqArmj9rEym8Za7aofBrjndvLNIIkPcphibfeaZibhPIfdMGGTA/132",
            "level": "0",
            "timesLimit": 5,
            "timesUsed": 0,
            "hoursLimit": 4,
            "isOrderable": true,
            "orderBeginTime": "00:00:00",
            "orderEndTime": "24:00:00",
            "alreadOrderDuration": [],
            "introduction": "好教练",
            "_id": "631b63342444ba78066a177f"
        },
        {
            "clubId": "101",
            "coachName": "滴滴",
            "gender": "男",
            "phone": "15111111111",
            "isInner": true,
            "expense": 200,
            "expensePercent": "10%",
            "avatarUrl": "https://thirdwx.qlogo.cn/mmopen/vi_32/fndXt7CVrdEll4znPM5MAD0nfJCDuqCYS1xvkmqArmj9rEym8Za7aofBrjndvLNIIkPcphibfeaZibhPIfdMGGTA/132",
            "level": "0",
            "timesLimit": 5,
            "timesUsed": 0,
            "hoursLimit": 4,
            "isOrderable": true,
            "orderBeginTime": "00:00:00",
            "orderEndTime": "24:00:00",
            "alreadOrderDuration": [],
            "introduction": "好教练",
            "_id": "6320a90aeede2866f1323f8b"
        },
        {
            "clubId": "101",
            "coachName": "滴滴",
            "gender": "男",
            "phone": "15111111111",
            "isInner": true,
            "expense": 200,
            "expensePercent": "10%",
            "avatarUrl": "https://thirdwx.qlogo.cn/mmopen/vi_32/fndXt7CVrdEll4znPM5MAD0nfJCDuqCYS1xvkmqArmj9rEym8Za7aofBrjndvLNIIkPcphibfeaZibhPIfdMGGTA/132",
            "level": "0",
            "timesLimit": 5,
            "timesUsed": 0,
            "hoursLimit": 4,
            "isOrderable": true,
            "orderBeginTime": "00:00:00",
            "orderEndTime": "24:00:00",
            "alreadOrderDuration": [],
            "introduction": "好教练",
            "_id": "6329e39dbbc3ca5905f5a240"
        },
        {
            "clubId": "101",
            "coachName": "滴滴",
            "gender": "男",
            "phone": "15111111111",
            "isInner": true,
            "expense": 200,
            "expensePercent": "10%",
            "avatarUrl": "https://thirdwx.qlogo.cn/mmopen/vi_32/fndXt7CVrdEll4znPM5MAD0nfJCDuqCYS1xvkmqArmj9rEym8Za7aofBrjndvLNIIkPcphibfeaZibhPIfdMGGTA/132",
            "level": "0",
            "timesLimit": 5,
            "timesUsed": 0,
            "hoursLimit": 4,
            "isOrderable": true,
            "orderBeginTime": "00:00:00",
            "orderEndTime": "24:00:00",
            "alreadOrderDuration": [],
            "introduction": "好教练",
            "_id": "632c86faf8656019cc8d23ab"
        },
        {
            "clubId": "101",
            "coachName": "滴滴",
            "gender": "男",
            "phone": "15111111111",
            "isInner": true,
            "expense": 200,
            "expensePercent": "10%",
            "avatarUrl": "https://thirdwx.qlogo.cn/mmopen/vi_32/fndXt7CVrdEll4znPM5MAD0nfJCDuqCYS1xvkmqArmj9rEym8Za7aofBrjndvLNIIkPcphibfeaZibhPIfdMGGTA/132",
            "level": "0",
            "timesLimit": 5,
            "timesUsed": 0,
            "hoursLimit": 4,
            "isOrderable": true,
            "orderBeginTime": "00:00:00",
            "orderEndTime": "24:00:00",
            "alreadOrderDuration": [],
            "introduction": "好教练",
            "_id": "632d1cf3f9df9d2fa674cddf"
        }
    ],
    "msg": "SUCCESS"
}
```

#### 9 获取全部预约订单信息（分页）

get   https://yunying.digitgolf.com/w/getOrderInfo?clubId=101&pageIndex=10&pageSize=5 

```
clubId:'101', // 门店id
pageIndex:'10',  // 页码
pageSize:'5', //每页数量
```

```
{
    "code": 0,
    "count": 63, //预约订单总数
    "data": [
        {
            "xtype": 1,  // 订单类型 0：充值 1：预约订单  2：卡订单
            "orderId": "202209011900303177707255", //订单id
            "transaction_id": "", //微信支付交易id
            "openid": "o99bm4nTfqftqcxGUftHUSIjHZjw", // 用户id
            "nickName": "Jason", // 昵称
            "phone": "15120076433", //手机号
            "clubId": "101", // 门店id
            "clubName": "北京中通数字高尔夫体验店", //门店名称
            "payType": "0", //门店支付类型 0不支持线上支付  1 支持线上支付
            "coachId": "630f0dcd0c9ac64f1f602b4d", //教练id
            "coachName": "普京", // 教练姓名
            "coachLevel": "0", //教练等级 0:初级教练  1:中级教练 2:高级教练 3:国家级教练  4:国际级教练
            "coachGender": "男", //教练性别
            "serviceType": "打球", //预约订单类型
            "posid": "1", //预约打位id
            "hitposition": "打位1", // 预约打位名称
            "totalFee": 0.01, //总额
            "orderDate": "2022-09-02", // 预约日期
            "orderTime": "2022-09-01 19:00:29", //预约时间
            "startTime": "2022-09-02 01:00:00", // 预约开始时间
            "endTime": "2022-09-02 02:00:00", //预约结束时间
            "duration": "1", //预约时长
            "payManner": 1, // 支付方式 0 微信支付 1 余额支付 2 还没有支付 3 后台支付 4 卡支付
            "golfcardOrderId": "", //如果是卡支付,则设置卡的golfcardOrderId
            "status": 3, //预约订单状态 0：待付款 1：待使用 2：已取消 3：已使用 4：进行中 注：过期未使用也算已使用 status=5是已退款
            "remarks": "", // 备注信息
            "TimeStamp": 1662030004930, // 时间戳
            "_id": "631090ce43127175601f4ab5"
        },
        {
            "xtype": 1,
            "orderId": "202209011858163852587096",
            "transaction_id": "",
            "openid": "o99bm4nTfqftqcxGUftHUSIjHZjw",
            "nickName": "Jason",
            "phone": "15120076433",
            "clubId": "101",
            "clubName": "北京中通数字高尔夫体验店",
            "payType": "0",
            "coachId": "630f0dcd0c9ac64f1f602b4d",
            "coachName": "普京",
            "coachLevel": "0",
            "coachGender": "男",
            "serviceType": "打球",
            "posid": "1",
            "hitposition": "打位1",
            "totalFee": 0.01,
            "orderDate": "2022-09-02",
            "orderTime": "2022-09-01 18:58:15",
            "startTime": "2022-09-02 00:00:00",
            "endTime": "2022-09-02 01:00:00",
            "duration": "1",
            "payManner": 1,
            "golfcardOrderId": "",
            "status": 3,
            "remarks": "",
            "TimeStamp": 1662029878668,
            "_id": "6310904828390e752301b62e"
        },
        {
            "xtype": 1,
            "orderId": "202209011853225073394791",
            "transaction_id": "",
            "openid": "o99bm4nTfqftqcxGUftHUSIjHZjw",
            "nickName": "Jason",
            "phone": "15120076433",
            "clubId": "101",
            "clubName": "北京中通数字高尔夫体验店",
            "payType": "0",
            "coachId": "630f0dcd0c9ac64f1f602b4d",
            "coachName": "普京",
            "coachLevel": "0",
            "coachGender": "男",
            "serviceType": "打球",
            "posid": "1",
            "hitposition": "打位1",
            "totalFee": 0.01,
            "orderDate": "2022-09-02",
            "orderTime": "2022-09-01 18:53:21",
            "startTime": "2022-09-02 12:00:00",
            "endTime": "2022-09-02 13:00:00",
            "duration": "1",
            "payManner": 1,
            "golfcardOrderId": "",
            "status": 3,
            "remarks": "",
            "TimeStamp": 1662029586895,
            "_id": "63108f224f857774e0cd083d"
        },
        {
            "xtype": 1,
            "orderId": "202209011850330176470310",
            "transaction_id": "",
            "openid": "o99bm4nTfqftqcxGUftHUSIjHZjw",
            "nickName": "Jason",
            "phone": "15120076433",
            "clubId": "101",
            "clubName": "北京中通数字高尔夫体验店",
            "payType": "0",
            "coachId": "",
            "coachName": "",
            "coachLevel": "",
            "coachGender": "",
            "serviceType": "打球",
            "posid": "1",
            "hitposition": "打位1",
            "totalFee": 0.01,
            "orderDate": "2022-09-01",
            "orderTime": "2022-09-01 18:50:32",
            "startTime": "2022-09-01 19:00:00",
            "endTime": "2022-09-01 20:00:00",
            "duration": "1",
            "payManner": 1,
            "golfcardOrderId": "",
            "status": 3,
            "remarks": "",
            "TimeStamp": 1662029337101,
            "_id": "63108e79b9e8ae7493e657da"
        },
        {
            "xtype": 1,
            "orderId": "202209011849128918538968",
            "transaction_id": "",
            "openid": "o99bm4nTfqftqcxGUftHUSIjHZjw",
            "nickName": "Jason",
            "phone": "15120076433",
            "clubId": "101",
            "clubName": "北京中通数字高尔夫体验店",
            "payType": "0",
            "coachId": "630f0dcd0c9ac64f1f602b4d",
            "coachName": "普京",
            "coachLevel": "0",
            "coachGender": "男",
            "serviceType": "打球",
            "posid": "1",
            "hitposition": "打位1",
            "totalFee": 0.01,
            "orderDate": "2022-09-01",
            "orderTime": "2022-09-01 18:49:11",
            "startTime": "2022-09-01 21:00:00",
            "endTime": "2022-09-01 22:00:00",
            "duration": "1",
            "payManner": 1,
            "golfcardOrderId": "",
            "status": 3,
            "remarks": "",
            "TimeStamp": 1662029337101,
            "_id": "63108e28b9e8ae7493e657d9"
        }
    ],
    "msg": "SUCCESS"
}
```

#### 10 获取不同状态的预约订单(分页)

get   https://yunying.digitgolf.com/w/getOrderInfoByStatus?clubId=101&pageIndex=1&pageSize=5&status=1 

```
{
    clubId:'101', //门店id
	pageIndex:'1',  //页码
	pageSize:'5',//每页数量
	status:'1', //预约订单状态 预约订单状态 0：待付款 1：待使用 2：已取消 3：已使用 5已退款
}
```

```
{
    "code": 0,
    "count": 1, // 该状态订单总数
    "data": [
        {
            "xtype": 1,
            "orderId": "202209021708359369494913",
            "transaction_id": "",
            "openid": "o99bm4nTStQKkkZLffHG1QLIWcN4",
            "nickName": "中通室内高尔夫(高视高尔夫教学)",
            "phone": "13141252823",
            "clubId": "101",
            "clubName": "北京中通数字高尔夫体验店",
            "payType": "0",
            "coachId": "630f0dfa0c9ac64f1f602b4f",
            "coachName": "拜登",
            "coachLevel": "2",
            "coachGender": "男",
            "serviceType": "打球",
            "posid": "1",
            "hitposition": "打位1",
            "totalFee": 0.01,
            "orderDate": "2022-09-03",
            "orderTime": "2022-09-02 17:08:20",
            "startTime": "2022-09-03 00:00:00",
            "endTime": "2022-09-03 01:00:00",
            "duration": "1",
            "payManner": 1,
            "golfcardOrderId": "",
            "status": 1,
            "remarks": "",
            "TimeStamp": 1662108063809,
            "_id": "6311c813313eca171327533a"
        }
    ],
    "msg": "SUCCESS"
}
```

#### 11 获取高尔夫卡订单信息（分页）

get 	 https://yunying.digitgolf.com/w/getGolfCardOrderInfo?clubId=101&pageIndex=2&pageSize=2 

```
{
    clubId:'101' //门店id
	pageIndex:'2'// 页码
	pageSize:'2'// 每页显示数量
}
```

```
{
    "code": 0,
    "count": 6, //高尔夫卡订单总数
    "data": [
        {
            "xtype": 2,  // 订单类型 0：充值 1：预约订单  2：卡订单
            "golfcardOrderId": "202209061706496773934645",//高尔夫卡订单id
            "transaction_id": "", //微信支付订单号, 用于申请退款
            "openid": "o99bm4nTfqftqcxGUftHUSIjHZjw", //用户openid
            "nickName": "Jason", //用户昵称
            "phone": "15120076433", //手机号
            "cardId": "", //卡id
            "cardGrant": 0,  // 0:普通购买的卡, 1:特惠卡
            "cardKind": "1", //卡的种类: 0:课程卡(约教练), 1:E卡(约场地)
            "cardName": "每月场地联系卡23次", //卡名称
            "golfClub": "北京中通数字高尔夫体验店", //高尔夫门店名称
            "clubId": "101", //高尔夫门店id
            "coachLevel": "", //教练等级
            "timeValid": "365", //有效期天数
            "expireTime": "", //过期时间
            "isExpire": false, //是否过使用期限
            "cardPrice": 0.01, //价格
            "cardType": "场地畅打卡", //类型， 比如成人私教课、青少年私教课
            "cardTimes": 23, //次数
            "giveTimes": 5, //新用户购买赠送次数
            "useRule": "1天10次4小时", //使用限制
            "dayLimit": 1, // 天数限制
            "timesLimit": 1, // 次数限制
            "hoursLimit": 2, // 每次的小时限制
            "dayUsed": 0, //已使用天数，改参数现在没用
            "timesUsed": 0, // 已使用次数
            "remarks": "", // 购买限制备注：0：无限制，1：限首次购卡用户，2：限每人限购一次
            "cardIntro": "非常好的练习卡", //说明	
            "cardimg": "https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/changda.jpg", //封面图
            "coachlogo": "https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/coachlogo.jpg", //教练logo
            "totalfee": 0.01, //订单总价
            "discount": 0, //优惠金额
            "orderDate": "2022-09-06", //下单日期  "orderDate":"2022-08-19",
            "orderTime": "2022-09-06 17:06:49", //下单时间
            "payTime": "", //支付时间
            "dealTime": "", //成交时间
            "payManner": 1, //支付方式 0 微信支付 1 余额支付 2 还没有支付 3 后台支付
            "status": 1, //订单状态 0：待付款 1：待使用 2：已取消 3：订单已过期 注：过期未使用也算已使用 5：已退款 6：退款中 7:售后完成已删除
            "TimeStamp": 1662452215243, //时间戳
            "_id": "63170da95d205717a984f48d"
        },
        {
            "xtype": 2,
            "golfcardOrderId": "202209061631352964617889",
            "transaction_id": "",
            "openid": "o99bm4uBHHMRhUMleN0SHmSjDeig",
            "nickName": "🌞",
            "phone": "15662170259",
            "cardId": "",
            "cardGrant": 0,
            "cardKind": "1",
            "cardName": "每月场地联系卡23次",
            "golfClub": "北京中通数字高尔夫体验店",
            "clubId": "101",
            "coachLevel": "",
            "timeValid": "365",
            "expireTime": "",
            "isExpire": false,
            "cardPrice": 0.01,
            "cardType": "场地畅打卡",
            "cardTimes": 23,
            "giveTimes": 5,
            "useRule": "1天10次4小时",
            "dayLimit": 1,
            "timesLimit": 1,
            "hoursLimit": 2,
            "dayUsed": 0,
            "timesUsed": 0,
            "remarks": "",
            "cardIntro": "非常好的练习卡",
            "cardimg": "https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/changda.jpg",
            "coachlogo": "https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/coachlogo.jpg",
            "totalfee": 0.01,
            "discount": 0,
            "orderDate": "2022-09-06",
            "orderTime": "2022-09-06 16:31:36",
            "payTime": "",
            "dealTime": "",
            "payManner": 1,
            "status": 1,
            "TimeStamp": 1662452215243,
            "_id": "631705675d205717a984f48a"
        }
    ],
    "msg": "SUCCESS"
}
```

#### 12 获取某个高尔夫卡订单详情(参数说明参考api 11)

get 	  https://yunying.digitgolf.com/w/getGolfCardOrderDetail?clubId=101&golfcardOrderId=202209061631352964617889 

```
{
    clubId:100 //门店id
	golfcardOrderId:202208261633116166419434 //高尔夫卡订单id
}
```

```
{
    "code": 0,
    "data": {
        "xtype": 2,
        "golfcardOrderId": "202209061631352964617889",
        "transaction_id": "",
        "openid": "o99bm4uBHHMRhUMleN0SHmSjDeig",
        "nickName": "🌞",
        "phone": "15662170259",
        "cardId": "",
        "cardGrant": 0,
        "cardKind": "1",
        "cardName": "每月场地联系卡23次",
        "golfClub": "北京中通数字高尔夫体验店",
        "clubId": "101",
        "coachLevel": "",
        "timeValid": "365",
        "expireTime": "",
        "isExpire": false,
        "cardPrice": 0.01,
        "cardType": "场地畅打卡",
        "cardTimes": 23,
        "giveTimes": 5,
        "useRule": "1天10次4小时",
        "dayLimit": 1,
        "timesLimit": 1,
        "hoursLimit": 2,
        "dayUsed": 0,
        "timesUsed": 0,
        "remarks": "",
        "cardIntro": "非常好的练习卡",
        "cardimg": "https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/changda.jpg",
        "coachlogo": "https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/coachlogo.jpg",
        "totalfee": 0.01,
        "discount": 0,
        "orderDate": "2022-09-06",
        "orderTime": "2022-09-06 16:31:36",
        "payTime": "",
        "dealTime": "",
        "payManner": 1,
        "status": 1,
        "TimeStamp": 1662452215243,
        "_id": "631705675d205717a984f48a"
    },
    "msg": "SUCCESS"
}
```

#### 13 删除门店的某个教练

get  https://yunying.digitgolf.com/w/delCoach?coachId=630f0e110c9ac64f1f602b50&clubId=101 

```
{
    "coachId":"630f0e110c9ac64f1f602b50", //教练id
	"clubId":"101" //门店id
}
```

```
{
	code:0,
	msg:'SUCCESS'
}

{
	code:1,
	msg:'FAIL'
}
```

#### 14 获取门店的课程卡或E卡(分页)

get   https://yunying.digitgolf.com/w/getXCardInfo?clubId=101&pageIndex=1&pageSize=2&cardKind=0 

```
{
    clubId:101 // 门店id
	pageIndex:1 //页码
	pageSize:2 //每页数量
	cardKind:0  //'0' 课程卡 '1' E卡
}
```

```
{
    "code": 0,
    "count": 1, // 卡总数
    "data": [
        {
            "cardId": "1012", //卡id
            "cardGrant": 0, // 0 普通卡 1 特惠卡
            "cardKind": "0", //卡的种类：0：课程卡，1：E卡
            "cardName": "成人私教卡现场1V1教学23节课", //卡名称
            "golfClub": "北京中通数字高尔夫体验店", //高尔夫门店名称
            "clubId": "101", //高尔夫门店id
            "coachLevel": "1", //教练等级 LV0:初级教练  LV1:中级教练 LV2:高级教练 LV3:国家级教练  LV4:国际级教练
            "timeValid": "30", //有效期天数
            "cardStart": "", //卡上架时间
            "cardEnd": "", //卡下架时间
            "cardStatus": "1", //状态：比如未上架('0')、上架中('1')、已下架('2')
            "cardPrice": "0.01", //价格
            "cardType": "成人私教课", //类型， 比如成人私教课、青少年私教课
            "cardTimes": "23", //次数
            "giveTimes": "3", //新用户购买赠送次数
            "discountMoney": 0, //按金额优惠
            "discountPercent": "0",//按百分比优惠
            "useRule": "1天10次4小时",  //限制规则
            "dayLimit": 1, // 天数限制
            "timesLimit": 10, // 次数限制
            "hoursLimit": 4, // 每次的小时限制
            "remarks": "0", //购买限制备注：0：无限制，1：限首次购卡用户，2：限每人限购一次
            "cardIntro": "非常好的课程卡", //说明	
            "cardimg": "https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/adult.jpg",  //封面图
            "coachlogo": "https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/coachlogo.jpg", //教练logo
            "isRecommend": "1", //是否设置为推荐课程卡 0 不设置  1设置
            "_id": "63088c5fe13ef7d1e3600236"
        }
    ],
    "msg": "SUCESS"
}
```

#### 15 获取门店的不同状态的课程卡或E卡(分页)(参数参考14)

get	 https://yunying.digitgolf.com/w/getXCardInfoBystatus?clubId=101&pageIndex=1&pageSize=2&cardKind=0&cardStatus=1 

```
{
    clubId:101, 	//门店id
	pageIndex:1,	// 页码
	pageSize:2,	// 每页数量
	cardKind:0,	//'0' 课程卡 '1' E卡
	cardStatus:1,	// 比如未上架('0')、上架中('1')、已下架('2')
}
```

```
{
    "code": 0,
    "count": 1,
    "data": [
        {
            "cardId": "1012",
            "cardGrant": 0,
            "cardKind": "0",
            "cardName": "成人私教卡现场1V1教学23节课",
            "golfClub": "北京中通数字高尔夫体验店",
            "clubId": "101",
            "coachLevel": "1",
            "timeValid": "30",
            "cardStart": "",
            "cardEnd": "",
            "cardStatus": "1",
            "cardPrice": "0.01",
            "cardType": "成人私教课",
            "cardTimes": "23",
            "giveTimes": "3",
            "discountMoney": 0,
            "discountPercent": "0",
            "useRule": "1天10次4小时",
            "dayLimit": 1,
            "timesLimit": 10,
            "hoursLimit": 4,
            "remarks": "0",
            "cardIntro": "非常好的课程卡",
            "cardimg": "https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/adult.jpg",
            "coachlogo": "https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/coachlogo.jpg",
            "isRecommend": "1",
            "_id": "63088c5fe13ef7d1e3600236"
        }
    ],
    "msg": "SUCESS"
}
```

#### 16 获取门店的特惠卡(分页)（参数参考14）

get 	 https://yunying.digitgolf.com/w/getTCardInfo?clubId=101&pageIndex=1&pageSize=2 

```
{
    clubId:101 // 门店id
	pageIndex:1		// 页码
	pageSize:2	// 每页数量
}
```

```
{
    "code": 0,
    "count": 2,
    "data": [
        {
            "cardId": "1014",
            "cardGrant": 1,
            "cardKind": "1",
            "cardName": "每月场地联系卡23次",
            "golfClub": "北京中通数字高尔夫体验店",
            "clubId": "101",
            "coachLevel": "",
            "timeValid": "365",
            "cardStart": "2022-07-13 12:00",
            "cardEnd": "2022-09-30 12:00",
            "cardStatus": "1",
            "cardPrice": "0.01",
            "cardType": "场地畅打卡",
            "cardTimes": "23",
            "giveTimes": "5",
            "discountMoney": 0,
            "discountPercent": "0",
            "useRule": "1天10次4小时",
            "dayLimit": 1,
            "timesLimit": 10,
            "hoursLimit": 4,
            "remarks": "2",
            "cardIntro": "非常好的练习卡",
            "cardimg": "https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/changda.jpg",
            "coachlogo": "https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/coachlogo.jpg",
            "isRecommend": "1",
            "_id": "630dcc34e13ef7d1e3607770"
        },
        {
            "cardId": "1013",
            "cardGrant": 1,
            "cardKind": "0",
            "cardName": "成人私教卡现场1V1教学23节课",
            "golfClub": "北京中通数字高尔夫体验店",
            "clubId": "101",
            "coachLevel": "1",
            "timeValid": "30",
            "cardStart": "2022-07-13 12:00",
            "cardEnd": "2022-09-20 12:00",
            "cardStatus": "1",
            "cardPrice": "0.01",
            "cardType": "成人私教课",
            "cardTimes": "23",
            "giveTimes": "3",
            "discountMoney": 0,
            "discountPercent": "0",
            "useRule": "1天10次4小时",
            "dayLimit": 1,
            "timesLimit": 10,
            "hoursLimit": 4,
            "remarks": "0",
            "cardIntro": "非常好的课程卡",
            "cardimg": "https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/adult.jpg",
            "coachlogo": "https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/coachlogo.jpg",
            "isRecommend": "1",
            "_id": "63088c91e13ef7d1e360025c"
        }
    ],
    "msg": "SUCESS"
}
```

#### 17 获取门店的不同状态的特惠卡(分页)(参数参考14)

get	 https://yunying.digitgolf.com/w/getTCardInfoBystatus?clubId=101&pageIndex=1&pageSize=2&cardStatus=1 

```
{
    clubId:101, //门店id
	pageIndex:1, //页码
	pageSize:2, // 每页数量
	cardStatus:1, //状态 比如未上架('0')、上架中('1')、已下架('2')
}
```

```
{
    "code": 0,
    "count": 2,
    "data": [
        {
            "cardId": "1014",
            "cardGrant": 1,
            "cardKind": "1",
            "cardName": "每月场地联系卡23次",
            "golfClub": "北京中通数字高尔夫体验店",
            "clubId": "101",
            "coachLevel": "",
            "timeValid": "365",
            "cardStart": "2022-07-13 12:00",
            "cardEnd": "2022-09-30 12:00",
            "cardStatus": "1",
            "cardPrice": "0.01",
            "cardType": "场地畅打卡",
            "cardTimes": "23",
            "giveTimes": "5",
            "discountMoney": 0,
            "discountPercent": "0",
            "useRule": "1天10次4小时",
            "dayLimit": 1,
            "timesLimit": 10,
            "hoursLimit": 4,
            "remarks": "2",
            "cardIntro": "非常好的练习卡",
            "cardimg": "https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/changda.jpg",
            "coachlogo": "https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/coachlogo.jpg",
            "isRecommend": "1",
            "_id": "630dcc34e13ef7d1e3607770"
        },
        {
            "cardId": "1013",
            "cardGrant": 1,
            "cardKind": "0",
            "cardName": "成人私教卡现场1V1教学23节课",
            "golfClub": "北京中通数字高尔夫体验店",
            "clubId": "101",
            "coachLevel": "1",
            "timeValid": "30",
            "cardStart": "2022-07-13 12:00",
            "cardEnd": "2022-09-20 12:00",
            "cardStatus": "1",
            "cardPrice": "0.01",
            "cardType": "成人私教课",
            "cardTimes": "23",
            "giveTimes": "3",
            "discountMoney": 0,
            "discountPercent": "0",
            "useRule": "1天10次4小时",
            "dayLimit": 1,
            "timesLimit": 10,
            "hoursLimit": 4,
            "remarks": "0",
            "cardIntro": "非常好的课程卡",
            "cardimg": "https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/adult.jpg",
            "coachlogo": "https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/coachlogo.jpg",
            "isRecommend": "1",
            "_id": "63088c91e13ef7d1e360025c"
        }
    ],
    "msg": "SUCESS"
}
```

#### 18 获取门店今日的销售额(0点-24点)

get  https://yunying.digitgolf.com/w/getTodaySale?clubId=101 

```
{
    clubId:101 // 门店id
}
```

```
{
    "code": 0,
    "data": [
        {
            "name": "日常销售额",
            sum:100,
            "data": [
                60,
                92.1,
                94.4,
                85.4,
                20,
                15,
                50,
                45,
                15,
                56,
                48,
                20,
                69
            ]
        },
        {
            "name": "商城销售额",
            sum:100,
            "data": [
                30,
                89.4,
                91.2,
                76.9,
                100,
                150,
                150,
                25,
                95,
                76,
                38,
                80,
                19
            ]
        },
        {
            "name": "餐饮销售额",
            sum:100,
            "data": [
                90,
                83.1,
                92.5,
                78.1,
                5,
                105,
                20,
                35,
                65,
                59,
                20,
                10,
                0
            ]
        }
    ],
    "msg": "SUCCESS"
}
```

#### 19 获取昨日的销售额（0点-24点）

get 	https://yunying.digitgolf.com/w/getYesterdaySale?clubId=101 

```
{
    clubId:101 // 门店id
}
```

```
{
    "code": 0,
    "data": [
        {
            "name": "日常销售额",
            sum:100,
            "data": [
                60,
                92.1,
                94.4,
                85.4,
                20,
                15,
                50,
                45,
                15,
                56,
                48,
                20,
                69
            ]
        },
        {
            "name": "商城销售额",
            sum:100,
            "data": [
                30,
                89.4,
                91.2,
                76.9,
                100,
                150,
                150,
                25,
                95,
                76,
                38,
                80,
                19
            ]
        },
        {
            "name": "餐饮销售额",
            sum:100,
            "data": [
                90,
                83.1,
                92.5,
                78.1,
                5,
                105,
                20,
                35,
                65,
                59,
                20,
                10,
                0
            ]
        }
    ],
    "msg": "SUCCESS"
}
```

#### 20 获取最近7天的销售额数据

get	 https://yunying.digitgolf.com/w/getSevendaySale?clubId=101 

```
{
    clubId:101 // 门店id
}
```

```
{
    "code": 0,
    "data": [
        {
            "name": "日常销售额",
            sum:100,
            "data": [
                60,
                92.1,
                94.4,
                85.4,
                20,
                15,
                50
            ]
        },
        {
            "name": "商城销售额",
            sum:100,
            "data": [
                30,
                89.4,
                91.2,
                76.9,
                100,
                150,
                150
            ]
        },
        {
            "name": "餐饮销售额",
            sum:100,
            "data": [
                90,
                83.1,
                92.5,
                78.1,
                50,
                105,
                20
            ]
        }
    ],
    "msg": "SUCCESS"
}
```

#### 21 获取本月的销售额数据

get 	 https://yunying.digitgolf.com/w/getMonthSale?clubId=101 

```
{
    clubId:101 // 门店id
}
```

```
{
    "code": 0,
    "data": [
        {
            "name": "日常销售额",
            sum:100,
            "data": [
                60,
                92.1,
                94.4,
                85.4,
                20,
                15,
                50,
                12,
                23,
                12,
                14,
                50,
                56,
                45,
                89,
                89,
                56,
                12,
                45,
                25,
                23,
                89,
                25,
                14,
                26,
                36,
                45,
                78,
                89,
                10
            ]
        },
        {
            "name": "商城销售额",
            sum:100,
            "data": [
                90,
                83.1,
                92.5,
                78.1,
                53,
                105,
                20,
                35,
                65,
                59,
                20,
                10,
                0,
                60,
                92.1,
                94.4,
                85.4,
                20,
                15,
                50,
                12,
                23,
                12,
                14,
                50,
                56,
                45,
                89,
                89,
                56
            ]
        },
        {
            "name": "餐饮销售额",
            sum:100,
            "data": [
                90,
                83.1,
                92.5,
                78.1,
                50,
                105,
                20,
                60,
                92.1,
                94.4,
                85.4,
                20,
                15,
                50,
                12,
                23,
                12,
                14,
                50,
                56,
                45,
                89,
                89,
                56,
                0,
                60,
                92.1,
                94.4,
                85.4,
                20
            ]
        }
    ],
    "msg": "SUCCESS"
}
```

#### 22 上传图片获得图片url

参考： https://yunying.digitgolf.com/w

```javascript
<input class="upload" type="file" ref="upload" accept="image/jpeg,image/jpg,image/png">
<script>
    	const upload = document.getElementsByClassName('upload')[0]
    	upload.onchange=(e)=>{
       		let file = e.target.files[0]
        	let formdata = new FormData()
        	formdata.append('file', file)
        	axios.post('https://yunying.digitgolf.com/w/uploadImg',formdata,{
           		headers: {
          			'Content-Type': 'multipart/form-data'
            	},
            	transformRequest: [function (data) {
                	return data
            	}],
        	}).then((data)=>{
            	console.log(data.data)
				d = data.data
        	})
    }
</script>
```

```
{
    code:0
	imgurl: "https://yunying.digitgolf.com/images/wru4a1hwi28.jpg"
	message: "SUCCESS"
}
```

#### 23 删除某个门店某张高尔夫卡

get   https://yunying.digitgolf.com/golfcard/delCard?clubId=100&_id=630dcc54e13ef7d1e360777e 

```
{
	"clubId":"100", //门店id
	"_id":"630dcc54e13ef7d1e360777e" //高尔夫卡的字段_id
}
```

```
{
	code:0,
	msg:'SUCCESS'
}

{
	code:1,
	msg:'FAIL'
}
```

#### 24 删除门店的某个打位

  post  https://yunying.digitgolf.com/golfclub/delhitpos 

```
{
	"clubId":"100",
	"posid":"lzrzpm0dk1"
}
```

```

{
  	code:0,
  	msg:'position del success'
}
 {
  	code:1,
  	msg:'club not exist' //门店不存在
 }
{
    code:2,
  	msg:'ShareGolf DB error'
}
 {
	code:3,
	msg:'clubId err'
}
```

#### 25 编辑门店某个打位

post   https://yunying.digitgolf.com/golfclub/edithitpos 

```
{
    posid:'lzrzpm0dk1', //打位id
    clubId:'100', //门店id
    posname: '包间2', //打位名称
    posimg: "https://yunying.digitgolf.com/images/8c6xabkfnin.jpg", // 打位照片
    type:'0', //0 普通打位 1 无人值守
    priceList: [
      {
        week: 1,  //星期一
        status:1,  //1开启 0 关闭	
        time: [
         {
            time_id:Math.random().toString(36).substring(2, 15), //时间段id, 随机生成多位字符串id， 比如 Math.random().toString(36).substr(2, 15)
            startTime: '08:00', //开始时间
            endTime: '16:00', //结束时间
            price: 40  //价格
          },
          {
            time_id:Math.random().toString(36).substring(2, 15),
            startTime: '16:00',
            endTime: '24:00',
            price: 60
          }
        ]
      },
      {
        week: 2,
        status:1,
        time: [
          {
            time_id:Math.random().toString(36).substring(2, 15), //时间段id, 随机生成多位字符串id， 比如 Math.random().toString(36).substr(2, 15)
            startTime: '08:00', //开始时间
            endTime: '16:00', //结束时间
            price: 40  //价格
          },
          {
            time_id:Math.random().toString(36).substring(2, 15),
            startTime: '16:00',
            endTime: '24:00',
            price: 60
          }
        ]
      },
      {
        week: 3,
        status:1,
        time: [
         {
            time_id:Math.random().toString(36).substring(2, 15), //时间段id, 随机生成多位字符串id， 比如 Math.random().toString(36).substr(2, 15)
            startTime: '08:00', //开始时间
            endTime: '16:00', //结束时间
            price: 40  //价格
          },
          {
            time_id:Math.random().toString(36).substring(2, 15),
            startTime: '16:00',
            endTime: '24:00',
            price: 60
          }
        ]
      },
      {
        week: 4,
        status:1,
        time: [
          {
            time_id:Math.random().toString(36).substring(2, 15), //时间段id, 随机生成多位字符串id， 比如 Math.random().toString(36).substr(2, 15)
            startTime: '08:00', //开始时间
            endTime: '16:00', //结束时间
            price: 40  //价格
          },
          {
            time_id:Math.random().toString(36).substring(2, 15),
            startTime:'16:00',
            endTime: '24:00',
            price: 60
          }
        ]
      },
      {
        week: 5,
        status:1,
        time: [
          {
            time_id:Math.random().toString(36).substring(2, 15), //时间段id, 随机生成多位字符串id， 比如 Math.random().toString(36).substr(2, 15)
            startTime: '08:00', //开始时间
            endTime: '16:00', //结束时间
            price: 40  //价格
          },
          {
            time_id:Math.random().toString(36).substring(2, 15),
            startTime: '16:00',
            endTime: '24:00',
            price: 60
          }
        ]
      },
      {
        week: 6,
        status:1,
        time: [
          {
            time_id:Math.random().toString(36).substring(2, 15), //时间段id, 随机生成多位字符串id， 比如 Math.random().toString(36).substr(2, 15)
            startTime: '08:00', //开始时间
            endTime: '16:00', //结束时间
            price: 40  //价格
          },
          {
            time_id:Math.random().toString(36).substring(2, 15),
            startTime: '16:00',
            endTime: '24:00',
            price: 60
          }
        ]
      },
      {
        week: 7,
        status:1,
        time: [
          {
            time_id:Math.random().toString(36).substring(2, 15), //时间段id, 随机生成多位字符串id， 比如 Math.random().toString(36).substr(2, 15)
            startTime: '08:00', //开始时间
            endTime: '16:00', //结束时间
            price: 40  //价格
          },
          {
            time_id:Math.random().toString(36).substring(2, 15),
            startTime: '16:00',
            endTime: '24:00',
            price: 60
          }
        ]
      }
    ]
}
```

```
{
  	code:0,
  	msg:'position edit success'
 }
 {
  	code:1,
  	msg:'club not exist' //门店不存在
 }

{
  	code:2,
  	msg:'ShareGolf DB error'
 }
 {
	code:3,
	msg:'clubId err'
}
```

#### 26 编辑教练信息

post	 https://yunying.digitgolf.com/coach/edit 

```
{
  _id:'632d1cf3f9df9d2fa674cddf', // 教练的_id属性
   coachName : '滴滴', // 姓名 
  gender:'男', //性别
  avatarUrl: 'https://thirdwx.qlogo.cn/mmopen/vi_32/fndXt7CVrdEll4znPM5MAD0nfJCDuqCYS1xvkmqArmj9rEym8Za7aofBrjndvLNIIkPcphibfeaZibhPIfdMGGTA/132'， //头像
   level:0, // 教练等级 0:初级教练  1:中级教练 2:高级教练 3:国家级教练  4:国际级教练
    introduction: '好教练'，// 介绍
    clubId：'101', //教练所属的高尔夫门店id
    phone: '15111111111', //手机号
    timesLimit：5, // 每日可预约次数
    orderBeginTime:'00:00:00', // 可预约开始时间
    orderEndTime：'24:00:00', //可预约结束时间
    expense：200，// 每节费用
    expensePercent: '10%' // 每节费用百分比
    isInner: true // 内部还是外聘
}
```

```
{
    "code": 0,
    "msg": "coach exit success"
}
{
	code:1,
	msg:'coach edit fail'
 }
```

#### 27 编辑高尔夫卡

post   http://yunying.digitgolf.com/golfcard/edit 

```
{
	_id: '6347df5cc9d16f1aec9d0226'
  	cardName: '成人私教卡现场1V1教学23节课', //卡名称
  	coachLevel：'中级教练', //教练等级
    golfClub：'北京中通数字高尔夫体验店' , //门店名称
    timeValid：'30', //有效期30天
    cardStart：'2022-07-13 12:00', // 卡上架开始时间
    cardEnd：'2022-08-13 12:00', //卡上架结束时间
    cardStatus: '上架中'， // 卡状态
    cardPrice：'4000' //卡价格
    cardType：'成人私教课' // 卡类型
    cardTimes：'23', //卡次数 若为 9999表示无限畅达卡
	giveTimes:'5' , //赠送次数
    discountMoney：'0' //优惠金额
    discountPercent：'0' // 优惠百分比
    useRule：'1天10次4小时', //使用规则
    cardIntro：'非常好的课程卡', //卡介绍
    remarks：'0', //购买限制：0 无限制 ，1 限首次购卡用户，2：限每人限购2次 以此类推
    cardKind:'0', //卡的种类：0：课程卡，1：E卡，
    cardimg:'https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/adult.jpg', //封面图
    clubId:'101',// 门店id
    cardGrant：'0' //0：普通卡 1 特惠卡
    dayLimit:'1',  // 参看userRule
    timesLimit:'10', // 参看userRule
    hoursLimit:'4' // 参看userRule
}
```

```
{
	code:0,
	msg:'card edit success'
}
{
	code:1,
	msg:'card edit fail'
 }
```

#### 28 修改某个高尔夫卡订单状态

get  http://yunying.digitgolf.com/gcorder/editgolfcardorder?_id=634932d0e748a93a795c7bd9&status=6 

```
{
	_id:'634932d0e748a93a795c7bd9',
	status:'6' // 订单状态 0：待付款 1：待使用 2：已取消 3：订单已过期 注：过期未使用也算已使用 5：已退款 6:退款中（已使用次数的卡需后台审批）7:售后退款已删除 8 审批失败
}
```

```
{
	code:0,
	msg:"edit golfcardorder status success"
}
{
	code:1,
	msg:"edit golfcardorder status fail"
}
```

#### 29  获取高尔夫卡订单售后列表(分页)

get    https://yunying.digitgolf.com/w/getGolfCardRefundOrderInfo?clubId=101&pageIndex=2&pageSize=2 

```
{
    clubId:'101' //门店id
	pageIndex:'2'// 页码
	pageSize:'2'// 每页显示数量
}
```

#### 30 修改高尔夫卡的状态（开启）

get   http://yunying.digitgolf.com/golfcard/editcardstatus?_id=6347df5cc9d16f1aec9d0226&cardstatus=1 

```
{
	_id:'6347df5cc9d16f1aec9d0226',
	cardstatus:'1' // 比如未上架('0')、上架中('1')、已下架('2')
}
```

```
{
	code:0,
	msg:'SUCCESS'
}
			
{
	code:1,
	msg:'FAIL'
}
```

#### 31 设置门店预约支付类型 预约有支付和预约无支付 

get    https://yunying.digitgolf.com/w/editClubpayType?_id=62cf9ff40c94de1934a4cdea&payType=1  

```
{
	_id:'62cf9ff40c94de1934a4cdea',
	payType:'1', // 支付类型 0不支持线上支付  1 支持线上支付
	cancelLimitHour: 2, //默认2小时 提前几个小时取消预约不扣费，限制小时之内取消卡支付的扣除次数，微信和余额支付的扣除金额的百分比
	cancelPercent:0  //取消扣除费用的百分比, 传小数,比如0.1
}
```

```
{
	code:0,
	msg:'SUCCESS'
}
{
	code:1,
	msg:'FAIL'
}			
```

#### 32 装修门店 第一部分 编辑imgbanner图数组

post   https://yunying.digitgolf.com/golfclub/editimgbanner 

```
{
  _id: '62cf9ff40c94de1934a4cdea',
  imgbanner: [ // imgbanner传数组
      {
        "url" : "https://yunying.digitgolf.com/images/j15uf1fhw2n.jpg",
        "cardId" : "1001"
    }, 
    {
        "url" : "https://yunying.digitgolf.com/images/j15uf1fhw2n.jpg",
        "cardId" : "1002"
    }, 
    {
        "url" : "https://yunying.digitgolf.com/images/j15uf1fhw2n.jpg",
        "cardId" : "1003"
    }
]
}
```

```
{
	code:0,
	msg:'SUCCESS'
 }
{
	code:1,
	msg:'FAIL'
}
```

#### 33 装修门店 第五部分 编辑门店电话和地址

get  https://yunying.digitgolf.com/golfclub/edithotlineandaddr?hotline=10086&address=北京市朝阳区北土城西路祁家豁子2号 

```
{
hotline:'10086',
address:'北京市朝阳区北土城西路祁家豁子2号',
_id:'62cf9ff40c94de1934a4cdea'
}
```

```
{
	code:0,
	msg:'SUCCESS'
 }
{
	code:1,
	msg:'FAIL'
}
```

#### 34 登录账号

get  https://yunying.digitgolf.com/w/home?username=admin&password=admin 

```
{
   username:'root1',   // 或者 root  root 对应PGA对应中通高尔夫学院
   password:'root1'  // 或者 admin1 admin1  体验店 101
}
```

```
{
    "code": 0,
    "data": {
    	club_id:"62cf9ff40c94de1934a4cdea",
    	clubId:"100",
    	clubName:'',
        name:'管理员',
      avatar:"https://thirdwx.qlogo.cn/mmopen/vi_32/Q0j4TwGTfTJOj8xic5yuzqJMiaXd7GxbVzyDbu5qicWKwOnZnqcwSzVWLNV1CvpTmZibL3HuYHLqaUjexTwA1N0e3A/132",
        token:"4biqoeh5rx4"
    },
    "msg": "SUCCESS"
}
```

#### 35  按状态查询门店高尔夫卡订单

get   http://yunying.digitgolf.com/gcorder/querybystatus?clubId=101&status=6 

```
{
	'clubId':'101'
	'status':'6'
}
```

```
{
    "code": 0,
    "data": [
        {
            "xtype": 2,
            "golfcardOrderId": "202210171034066290406494",
            "transaction_id": "",
            "openid": "o99bm4vtJLtZScdrJcEr73zz0FiQ",
            "nickName": "LY",
            "phone": "",
            "cardId": "0tgkujlu62",
            "cardGrant": 0,
            "cardKind": "0",
            "cardName": "测试",
            "golfClub": "北京中通数字高尔夫体验店",
            "clubId": "101",
            "coachLevel": "国际级教练",
            "timeValid": "",
            "expireTime": "",
            "isExpire": false,
            "cardPrice": 1,
            "cardType": "成人私教课",
            "cardTimes": 5,
            "giveTimes": 0,
            "_cardTimes": 11,
            "_giveTimes": 1,
            "useRule": "11次1分钟",
            "dayLimit": 1,
            "timesLimit": 1,
            "hoursLimit": 2,
            "dayUsed": 0,
            "timesUsed": 0,
            "remarks": "0",
            "cardIntro": "渐渐",
            "cardimg": "https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/adult.jpg",
            "coachlogo": "https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/coachlogo.jpg",
            "totalfee": 1,
            "discount": 0,
            "orderDate": "2022-10-17",
            "orderTime": "2022-10-17 10:34:06",
            "payTime": "",
            "dealTime": "",
            "payManner": 1,
            "status": 6,
            "TimeStamp": 1665968527510,
            "_id": "634cbf1efdef040a9d3042c4"
        }
    ],
    "msg": "query success"
}

{
	 code:2,
	 msg:'ShareGolf DB error'
}
```

#### 36 装修门店 第二部分 编辑菜单栏 课程卡1  e卡2  限时特惠3  商城4   点餐5 按钮 开启或关闭

get   https://yunying.digitgolf.com/golfclub/editmenubar?index=1&status=1&_id=62cf9ff40c94de1934a4cdea 

```
{
	index:'1', //编辑菜单栏   课程卡1  e卡2  限时特惠3  商城4   点餐5
	status:'1', //1 开启   0 关闭
	_id:'62cf9ff40c94de1934a4cdea' //门店_id
}
```

```
{
	code:0,
	msg:'SUCCESS'
 }
{
	code:1,
	msg:'FAIL'
}
```

#### 37 装修门店 第二部分 编辑imgad图（广告图）数组

post  https://yunying.digitgolf.com/golfclub/editimgad 

```
{
//imgad传数组
 imgad:[ 
        "https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/img2-2.jpg", 
        "https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/img3-3.jpg", 
        "https://yunying.digitgolf.com/images/tqlgoj5ca1b.jpg", 
        "https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/img5.jpg"
]
}
```

```
{
	code:0,
	msg:'SUCCESS'
 }
{
	code:1,
	msg:'FAIL'
}
```

#### 38 获取查询日期后一个星期的预约单

get  https://yunying.digitgolf.com/w/orderdataofweek?clubId=101&checkDate=2022-09-01 

```
{
	clubId:'101', // 门店属性clubId
	checkDate:'2022-09-01' //查询日期 格式类型 "orderDate" : "2022-09-01"
}
```

```
{
	code:0,
	data:{
		checkDate:[],
		chekDate_1:[],
		chekDate_2:[],
		chekDate_3:[],
		chekDate_4:[],
		chekDate_5:[],
		chekDate_6:[]
	},
	msg:'SUCCESS'
}

{
	code:1,
	msg:'FAIL'
}
```

#### 39 修改某个预约订单信息

post  https://yunying.digitgolf.com/w/editOrderDetail 

```
{
    clubId:
    phone: 
    payType:
    coachId: 
    coachName:
    coachGender: 
    coachLevel: 
    serviceType:
    posid: 
    hitposition: 
    totalFee: 
    orderDate: 
    orderTime: 
    startTime: 
    endTime: 
    duration:
    remarks:
    _id:
}
```

```
{
	code:0,
	msg:'SUCCESS'
 }
{
	code:1,
	msg:'FAIL'
}
```

#### 40  获取进行中的预约订单

get  https://yunying.digitgolf.com/w/getOrderInfoIng?clubId=101&pageIndex=1&pageSize=5 

```
{
	clubId:101
	pageIndex:1
	pageSize:5
}
```

```
{
	code:0,
	count:count,
	data:[],
	msg:'SUCCESS'
}
{
	code:1,
	msg:'FAIL'
}
```

#### 41 装修店铺 添加一个模板

post  https://yunying.digitgolf.com/golfclub/addTemplate

```
{
   clubId:'100',
   _clubName:'PGA中通数字学院',
   // 第一部分
   _imgbanner:[{
            "url" : "https://yunying.digitgolf.com/images/j15uf1fhw2n.jpg",
            "cardId" : "1001"
        }, 
        {
            "url" : "https://yunying.digitgolf.com/images/j15uf1fhw2n.jpg",
            "cardId" : "1002"
        }], // 数组[]

   // 第二部分 菜单栏开启或关闭， 默认开启为1 关闭为0
    _menu_coursecard:'1', //课程卡
    _menu_ecard:'1', //e卡
    _menu_tehui:'1', //特惠卡
    _menu_store:'1', //商城
    _menu_restaurant:'1', //点餐
    _menu_onlineTeaching:'1', 线上授课
    _menu_videoCourse:'1', //视频课程

    // 第三部分 
    _imgadstyle:"4", //广告图显示样式 '1', '2', '3', '4'
    _imgad:[ 
        "https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/img2-2.jpg", 
        "https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/img3-3.jpg", 
        "https://yunying.digitgolf.com/images/tqlgoj5ca1b.jpg", 
        "https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/img5.jpg"
    ], //数组[]

    // 第四部分
    _displayCoach:[ //展示的教练
    {
    "_id" : "630f0e5e0c9ac64f1f602b52",
    "clubId" : "100",
    "coachName" : "小王",
    "gender" : "男",
    "phone" : "15111111111",
    "isInner" : true,
    "expense" : 200,
    "expensePercent" : "10%",
    "avatarUrl" : "https://thirdwx.qlogo.cn/mmopen/vi_32/fndXt7CVrdEll4znPM5MAD0nfJCDuqCYS1xvkmqArmj9rEym8Za7aofBrjndvLNIIkPcphibfeaZibhPIfdMGGTA/132",
    "level" : "4",
    "timesLimit" : 99,
    "timesUsed" : 0,
    "hoursLimit" : 4,
    "isOrderable" : true,
    "orderBeginTime" : "00:00:00",
    "orderEndTime" : "24:00:00",
    "alreadOrderDuration" : [],
    "introduction" : "好教练"
},
{
    "_id" : "630f0e660c9ac64f1f602b53",
    "clubId" : "100",
    "coachName" : "小李",
    "gender" : "男",
    "phone" : "15111111111",
    "isInner" : true,
    "expense" : 200,
    "expensePercent" : "10%",
    "avatarUrl" : "https://thirdwx.qlogo.cn/mmopen/vi_32/fndXt7CVrdEll4znPM5MAD0nfJCDuqCYS1xvkmqArmj9rEym8Za7aofBrjndvLNIIkPcphibfeaZibhPIfdMGGTA/132",
    "level" : "3",
    "timesLimit" : 99,
    "timesUsed" : 0,
    "hoursLimit" : 4,
    "isOrderable" : true,
    "orderBeginTime" : "00:00:00",
    "orderEndTime" : "24:00:00",
    "alreadOrderDuration" : [],
    "introduction" : "好教练"
}
    ], //数组[]

    // 第五部分
    _hotline:'1008611',
    _address:'北京市朝阳区北土城西路2号',

    // 第六部分
    _displayGolfcardstyle : "1", //高尔夫卡显示样式 '1'竖放  '2'横放
    _displayGolfcard:[ //展示的高尔夫卡
    {
    "_id" : "62d1168b6f88ec3ad8c55f9c",
    "cardId" : "1001",
    "cardGrant" : 0,
    "cardKind" : "1",
    "cardName" : "每月场地联系卡23次",
    "golfClub" : "PGA中通数字学院",
    "clubId" : "100",
    "coachLevel" : "",
    "timeValid" : "365",
    "cardStart" : "",
    "cardEnd" : "",
    "cardStatus" : "1",
    "cardPrice" : "0.01",
    "cardType" : "场地畅打卡",
    "cardTimes" : "23",
    "giveTimes" : "5",
    "discountMoney" : 0,
    "discountPercent" : "0",
    "useRule" : "1天10次4小时",
    "dayLimit" : 1,
    "timesLimit" : 10,
    "hoursLimit" : 4,
    "remarks" : "2",
    "cardIntro" : "非常好的练习卡",
    "cardimg" : "https://yunying.digitgolf.com/images/llwzka5djt.jpg",
    "coachlogo" : "https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/coachlogo.jpg",
    "isRecommend" : "1"
},
{
    "_id" : "62d117796f88ec3ad8c55f9f",
    "cardId" : "1002",
    "cardGrant" : 0,
    "cardKind" : "0",
    "cardName" : "成人私教卡现场1V1教学23节课",
    "golfClub" : "PGA中通数字学院",
    "clubId" : "100",
    "coachLevel" : "1",
    "timeValid" : "30",
    "cardStart" : "",
    "cardEnd" : "",
    "cardStatus" : "1",
    "cardPrice" : "0.01",
    "cardType" : "成人私教课",
    "cardTimes" : "23",
    "giveTimes" : "3",
    "discountMoney" : 0,
    "discountPercent" : "0",
    "useRule" : "1天10次4小时",
    "dayLimit" : 1,
    "timesLimit" : 10,
    "hoursLimit" : 4,
    "remarks" : "0",
    "cardIntro" : "非常好的课程卡",
    "cardimg" : "https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/adult-1.jpg",
    "coachlogo" : "https://wxmini-digitgolf-yunying.oss-cn-beijing.aliyuncs.com/%E5%8C%97%E4%BA%ACcity%E9%AB%98%E5%B0%94%E5%A4%AB%E5%BA%97/coachlogo.jpg",
    "isRecommend" : "1"
}
    ], // []

    // 预约 开启或关闭， 默认开启为1 关闭为0
    _orderPos:'1',  //约场地
    _orderCoach:'1',  //约教练
    _unattended:'1',  //无人值守
   // 赛事 开启或关闭， 默认开启为1 关闭为0
     _event:'0',
     // 我的 开启或关闭， 默认开启为1 关闭为0
     _myCollection:'0', //我的收藏
     _myVideo:'0', //我的视频
     _myRecord:'0', //我的记录
     _myData:'0',  //我的数据
     _myRank:'0',  //我的排名
}
```

```
{
	code:3,
	msg:'clubId err'
}
{
  	code:2,
  	msg:'ShareGolf DB error'
 }
{
  	code:1,
  	msg:'club not exist'
 }
{
  	code:0,
	_template_id:'dsfdsfjx',
  	msg:'template add success'
}
```

#### 42 获取门店模板

get   https://yunying.digitgolf.com/golfclub/getTemplate?clubId=101 

```
{
	clubId:'101'
}
```

```
{
		code:0,
		template:[
		{
		 ....,
		 _updateAt:'2022-10-26 10:00:00'
		},
		{
		 ....,
		 _updateAt:'2022-10-26 12:00:00'
		}
		],
		msg:'success'
}
{
  	code:1,
  	msg:'club not exist'
}
{
	code:2,
	msg:'ShareGolf DB error'
}
{
	code:3,
	msg:'clubId err'
}
```

#### 43 获取门店信息

get    https://yunying.digitgolf.com/golfclub/getClubInfo?clubId=101 

 ```
{
	clubId:'101'
}
 ```

```
{
		code:0,
		clubInfo:{},
		msg:'success'
}
{
  	code:1,
  	msg:'club not exist'
}
{
	code:2,
	msg:'ShareGolf DB error'
}
{
	code:3,
	msg:'clubId err'
}
```

#### 44 发布模板

post   https://yunying.digitgolf.com/golfclub/publishTemplate

```
{
   clubId:''
   //见添加模板
}
```

```
{
	code:3,
	msg:'clubId err'
}
{
  	code:2,
  	msg:'ShareGolf DB error'
 }
{
  	code:1,
  	msg:'club not exist'
 }
{
  	code:0,
	_template_id:'dsfdsfjx',
  	msg:'success'
}
```

#### 45 编辑某个模板

post   https://yunying.digitgolf.com/golfclub/editTemplate

```
{
	clubId:''
	_template_id:'dsfdsfjx'
   //见添加模板
}
```

```
{
	code:3,
	msg:'clubId err'
}
{
  	code:2,
  	msg:'ShareGolf DB error'
 }
{
  	code:1,
  	msg:'club not exist'
 }
{
  	code:0,
  	msg:'success'
}
```

#### 46 获取门店今日账单

get   https://yunying.digitgolf.com/w/getTodaySaleBill?clubId=101

```
{
	clubId:'101'
}
```

```
{
			code:0,
			msg:'success',
			queryDate:'2022-01-10', // 日期
			income:{
				sum: 300 // 总收入
				daily:{
					total:100, // 日常收入
					orderCount:3 // 订单数
				} ,
				store:{
					total:100, // 商城收入
					orderCount:3 // 订单数
				},
				restaurant:{
					total:100, // 餐饮收入
					orderCount:3 // 订单数
				}
			},
			out:{
				sum: 100, // 总支出
				daily:{
					total:30, //日常支出
					orderCount:3 //订单数
				},
				store:{
				  total:30, // 商城支出
				  orderCount:3	//订单数	
				},
				restaurant:{
					total:40, //餐饮支出
					orderCount:3 //订单数
				}
			},
			net_income: 200//净收入
}
或
{			
			code:1,
			msg:'fail'
}

```

#### 47 获取门店昨日的账单

get https://yunying.digitgolf.com/w/getYesterdaySaleBill?clubId=101

```
{
	clubId:'101'
}
```

```
{
			code:0,
			msg:'success',
			queryDate:'2022-01-09', // 日期
			income:{
				sum: 300 // 总收入
				daily:{
					total:100, // 日常收入
					orderCount:3 // 订单数
				} ,
				store:{
					total:100, // 商城收入
					orderCount:3 // 订单数
				},
				restaurant:{
					total:100, // 餐饮收入
					orderCount:3 // 订单数
				}
			},
			out:{
				sum: 100, // 总支出
				daily:{
					total:30, //日常支出
					orderCount:3 //订单数
				},
				store:{
				  total:30, // 商城支出
				  orderCount:3	//订单数	
				},
				restaurant:{
					total:40, //餐饮支出
					orderCount:3 //订单数
				}
			},
			net_income: 200//净收入
}
或
{			
			code:1,
			msg:'fail'
}
```

#### 48 门店今日账单明细

get   https://yunying.digitgolf.com/w/getTodaySaleBillDetail?clubId=101 

```
{
	clubId:'101'
}
```

```
{
			code:0,
			msg:'success',
			detail:{
				charge_rec:charge_rec,  //充值记录,数组[]
				golfcard_rec:golfcard_rec, // 购买的卡订单的记录， 微信支付的,数组[]
				_golfcard_rec:_golfcard_rec, // 卡订单退款记录,数组[]
				order_rec:order_rec, // 预约记录，微信支付的,数组[]
				_order_rec:_order_rec //预约退款记录,数组[]
			}
}
或
{			
			code:1,
			msg:'fail'
}
```



#### 49 门店昨日账单明细

get  https://yunying.digitgolf.com/w/getYesterdaySaleBillDetail?clubId=101

```
{
	clubId:'101'
}
```

```
{
			code:0,
			msg:'success',
			detail:{
				charge_rec:charge_rec,  //充值记录,数组[]
				golfcard_rec:golfcard_rec, // 购买的卡订单的记录， 微信支付的,数组[]
				_golfcard_rec:_golfcard_rec, // 卡订单退款记录,数组[]
				order_rec:order_rec, // 预约记录，微信支付的,数组[]
				_order_rec:_order_rec //预约退款记录,数组[]
			}
}
或
{			
			code:1,
			msg:'fail'
}
```

#### 50 获取用户列表（分页）

get   https://yunying.digitgolf.com/w/getUserList?clubId=101&pageIndex=1&pageSize=2 

```
{
	clubnId:'101'
	pageIndex:1,
	pageSize:2
}
```

```
{
  code：0,
  msg:'success',
  count:'10',
  data:[]
}
或
{
	code:1,
	msg:'fail'
}
```

#### 51 后台结算预约订单

get  https://yunying.digitgolf.com/order/editOrder?_id=6361e59470c86c2f3a5b596c

```
{
	_id: '6361e59470c86c2f3a5b596c'
}
```

```
{
  code：0,
  msg:'success',
}
或
{
	code:1,
	msg:'fail'
}
```

#### 52 后台结算，修改预约订单的时间

get  https://yunying.digitgolf.com/order/editOrderTime?_id=6361e59470c86c2f3a5b596c&startTime=2022-12-08 11:00:00&endTime=2022-12-09 12:00:00&duration=1

```
{
	_id: '6361e59470c86c2f3a5b596c',
	startTime:'2022-12-08 11:00:00',
	endTime:'2022-12-09 12:00:00',
	duration:'1'
}
```

```
{
  code：0,
  msg:'success',
}
或
{
	code:1,
	msg:'fail'
}
```

#### 53 后台结算，修预约订单的金额

get https://yunying.digitgolf.com/order/editOrderTotalFee?_id=6361e59470c86c2f3a5b596c&totalFee=300

```
{
	_id: '6361e59470c86c2f3a5b596c',
	totalFee:'300'
}
```

```
{
  code：0,
  msg:'success',
}
或
{
	code:1,
	msg:'fail'
}
```

#### 54 获取用户在某个门店去取消预约的次数

get  https://yunying.digitgolf.com/users/getOrderRefundInfo?clubId=101&openid=o99bm4nTfqftqcxGUftHUSIjHZjw

```
{
	clubId:'101',
	openid:'o99bm4nTfqftqcxGUftHUSIjHZjw'
}
```

```
{
          code: 0,
          data:{
            openid:openid,
            clubId:clubId,
            wxrefundTimes:0, // 微信支付取消预约次数
            moneyrefundTimes:0, // 余额支付取消预约次数
            cardrefundTimes:0 // 卡支付取消预约次数
          },
          msg:'success'
}
或
{
        code: 1,
        msg:'fail'
}
```

#### 55 获取门店教练某天的账单,以教练基准分页

get https://yunying.digitgolf.com/w/getClubCoachBillofDay?orderDate=2022-12-13&clubId=101&pageIndex=1&pageSize=1

```
{
	orderDate:2022-12-13, //要查询的日期
	clubId:101, //门店id
	pageIndex:1, // 页码
	pageSize:2, // 每页显示数量
}
```

```
{
    "code": 0,
    "msg": "success",
    "coachCount": 4, //教练总数
    "data": [
        {
            "coachName": "琼·拉姆", // 教练姓名
            "coachId": "63637f57cf86df5a1cd7ec8b", //教练id
            "orderDate": "2022-12-13", //查询日期
            "xtype": 0, //分成类型 预约课程0或者视频课程1
            "totaldividFee": 0 //总分成金额
        },
        {
            "coachName": "琼·拉姆",
            "coachId": "63637f57cf86df5a1cd7ec8b",
            "orderDate": "2022-12-13",
            "xtype": 1,
            "totaldividFee": 0
        },
        {
            "coachName": "亨利克",
            "coachId": "63637ef4cf86df5a1cd7ec8a",
            "orderDate": "2022-12-13",
            "xtype": 0,
            "totaldividFee": 100
        },
        {
            "coachName": "亨利克",
            "coachId": "63637ef4cf86df5a1cd7ec8a",
            "orderDate": "2022-12-13",
            "xtype": 1,
            "totaldividFee": 0
        }
    ]
}
或
{
	code:1, // 失败
	msg:'fail'
}
```

#### 56 获取门店某个预约订单详情

get   https://yunying.digitgolf.com/w/getClubOrderDetail?clubId=101&orderId=202212131119487287772446

```
{
	clubId:101, //门店id 
	orderId:202212131119487287772446 // 预约订单id
}
```

```
{
    "code": 0, //成功，下面参数示意可参看前面解释
    "msg": "success",
    "data": {
        "xtype": 1,
        "orderId": "202212131119487287772446",
        "transaction_id": "",
        "openid": "o99bm4vtJLtZScdrJcEr73zz0FiQ",
        "nickName": "微信用户",
        "phone": "15176060615",
        "clubId": "101",
        "clubName": "北京中通数字高尔夫体验店",
        "payType": "0",
        "coachId": "63637ef4cf86df5a1cd7ec8a",
        "coachName": "亨利克",
        "coachLevel": "1",
        "coachGender": "",
        "serviceType": "私教课",
        "posid": "u15po15atgi",
        "hitposition": "影音间",
        "totalFee": 200.01,
        "orderDate": "2022-12-13",
        "orderTime": "2022-12-13 11:19:46",
        "startTime": "2022-12-13 18:00",
        "endTime": "2022-12-13 19:00",
        "duration": "1",
        "payManner": 4,
        "golfcardOrderId": "202211041401118606814096",
        "status": 3,
        "ing": 0,
        "remarks": "",
        "TimeStamp": 1670901453100,
        "_id": "6397ef541caee818586982c3"
    }
}
或
{
	code:1, //失败
	msg:'fail'
}
```

#### 58 查询门店教练账单的明细(分页)

get  https://yunying.digitgolf.com/w/getClubCoachBillDetail?orderDate=2022-12-13&clubId=101&pageIndex=1&pageSize=4&xtype=0&coachId=63637ef4cf86df5a1cd7ec8a

```
{
	orderDate:2022-12-13,
	clubId:101,
	pageIndex:1,
	pageSize:1,
	xtype:0,
	coachId:63637ef4cf86df5a1cd7ec8a
}
```

```
{
    "code": 0,  //成功
    "msg": "success",
    "count": 2, // 要查询日期账单总数量
    "data": [
        {
            "xtype": 0, // 类型, 预约课程0或者视频课程1
            "clubId": "101", // 门店id
            "clubName": "北京中通数字高尔夫体验店", //门店名称
            "coachName": "亨利克", // 教练名
            "coachId": "63637ef4cf86df5a1cd7ec8a", // 教练id，coach数据库里面的_id
            "orderId": "202212131119487287772446", //预约订单id
            "videoCourseId": "", //视频课程订单id
            "orderDate": "2022-12-13", //要查询的日期,也即是预约订单的日期
            "orderTime": "2022-12-13 11:19:46", //下预约订单的时间点
            "startTime": "2022-12-13 18:00",  //订单开始时间
            "endTime": "2022-12-13 19:00", //订单结束时间
            "duration": "1", //订单时长
            "totalFee": 200, //订单总价
            "dividFee": 50, //分成金额
            "TimeStamp": 1673338501163, //时间戳
            "_id": "63bd1ec667bbc82748b53af8" //_id
        }
        .......
    ]
}
或
{
	code:1, //失败
	msg:'fail'
}
```

#### 59 获取门店教练最近七天或者本月的账单，以教练为基准分页

get https://yunying.digitgolf.com/w/getClubCoachBillofSomeDays?clubId=101&pageIndex=1&pageSize=2&option=0

```
{
	clubId:101,
	pageIndex:1,
	pageSize:2,
	option:0
}
```

```
{
    "code": 0,
    "msg": "success",
    "coachCount": 4, //教练总数
    "data": [
        {
            "coachName": "琼·拉姆", // 教练姓名
            "coachId": "63637f57cf86df5a1cd7ec8b", //教练id
            "orderDate": "2022-12-13", //查询日期
            "xtype": 0, //分成类型 预约课程0或者视频课程1
            "totaldividFee": 0 //总分成金额
        },
        {
            "coachName": "琼·拉姆",
            "coachId": "63637f57cf86df5a1cd7ec8b",
            "orderDate": "2022-12-13",
            "xtype": 1,
            "totaldividFee": 0
        },
        {
            "coachName": "亨利克",
            "coachId": "63637ef4cf86df5a1cd7ec8a",
            "orderDate": "2022-12-13",
            "xtype": 0,
            "totaldividFee": 100
        },
        {
            "coachName": "亨利克",
            "coachId": "63637ef4cf86df5a1cd7ec8a",
            "orderDate": "2022-12-13",
            "xtype": 1,
            "totaldividFee": 0
        }
    ]
}
或
{
	code:1, //失败
	msg:'fail'
}
```

#### 60 搜索获取门店教练具体日期范围内的账单，以教练为基准分页

get https://yunying.digitgolf.com/w/searchClubCoachBillofSomeDays?clubId=101&pageIndex=1&pageSize=2&orderDateStart=2022-12-10&orderDateEnd=2022-12-14

````
{
	clubId:101，
	pageIndex:1，
	pageSize:2,
	orderDateStart:2022-12-10,
	orderDateEnd:2022-12-14,
}
````

```
{
    "code": 0,
    "msg": "success",
    "coachCount": 4, //教练总数
    "data": [
        {
            "coachName": "琼·拉姆", // 教练姓名
            "coachId": "63637f57cf86df5a1cd7ec8b", //教练id
            "orderDate": "2022-12-13", //查询日期
            "xtype": 0, //分成类型 预约课程0或者视频课程1
            "totaldividFee": 0 //总分成金额
        },
        {
            "coachName": "琼·拉姆",
            "coachId": "63637f57cf86df5a1cd7ec8b",
            "orderDate": "2022-12-13",
            "xtype": 1,
            "totaldividFee": 0
        },
        {
            "coachName": "亨利克",
            "coachId": "63637ef4cf86df5a1cd7ec8a",
            "orderDate": "2022-12-13",
            "xtype": 0,
            "totaldividFee": 100
        },
        {
            "coachName": "亨利克",
            "coachId": "63637ef4cf86df5a1cd7ec8a",
            "orderDate": "2022-12-13",
            "xtype": 1,
            "totaldividFee": 0
        }
    ]
}
或
{
	code:1, //失败
	msg:'fail'
}
```



 
