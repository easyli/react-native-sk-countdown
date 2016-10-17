# react-native-sk-countdown

##What is it
react-native-sk-countdown is a simple countdown component for React Native, pure js implementation

##How to use it

1. `npm install react-native-sk-countdown@latest --save`

2. Write this in index.ios.js / index.android.js

```javascript
/**
 * Sample React Native App
 * https://github.com/facebook/react-native
 */
'use strict';
import React, {
  AppRegistry,
  StyleSheet,
  Text,
  View
} from 'react-native';

var {CountDownText} = require('react-native-sk-countdown');

var test = React.createClass({
  render: function(){
    return (
      <View style={styles.container}>
        <Text style={styles.tip}>{'CountDown in seconds \n 以秒为单位的倒计时'}</Text>
        <View style={styles.row}>
          <CountDownText
            style={styles.cd}
            countType='seconds' // 计时类型：seconds / date
            auto={true} // 自动开始
            afterEnd={() => {}} // 结束回调
            timeLeft={10} // 正向计时 时间起点为0秒
            step={-1} // 计时步长，以秒为单位，正数则为正计时，负数为倒计时
            startText='获取验证码' // 开始的文本
            endText='获取验证码' // 结束的文本
            intervalText={(sec) => sec + '秒重新获取'} // 定时的文本回调
          />
        </View>
        <Text style={styles.tip}>{'CountDown in timestamp \n 以日期-时间为单位的倒计时'}</Text>
        <View style={styles.row}>
          <CountDownText // 倒计时
            style={styles.cd}
            countType='date' // 计时类型：seconds / date
            auto={true} // 自动开始
            afterEnd={() => {}} // 结束回调
            timeLeft={10} // 正向计时 时间起点为0秒
            step={-1} // 计时步长，以秒为单位，正数则为正计时，负数为倒计时
            startText='' // 开始的文本
            endText='' // 结束的文本
            intervalText={(date, hour, min, sec) => date + '天' + hour + '时' + min + '分' + sec} // 定时的文本回调
          />
        </View>
      </View>
    )
  }
});


const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'space-around',
    alignItems: 'center',
    backgroundColor: '#F5FCFF',
  },
  row: {
    padding: 7,
    backgroundColor: 'red',
    borderRadius: 7,
  },
  tip: {
    fontSize: 20,
  },
  cd: {
    textAlign: 'center',
    color: 'white',
    fontSize: 20,
  },
});

AppRegistry.registerComponent('test', () => test);

```
![](https://raw.githubusercontent.com/shigebeyond/react-native-sk-countdown/master/demo.gif)

##Properties

Any [Text property](http://facebook.github.io/react-native/docs/text.html) and the following:

| Prop | Description | Default |
|---|---|---|
|**`countType`**|Countdown type, one of 'seconds' and 'date'. |*None*|
|**`auto`**|Whether to start countdown right now. |*false*|
|**`timeLeft`**|Seconds lefted to countdown. |*None*|
|**`step`**|Number to increment in each step. |*-1*|
|**`startText`**|Text before countdown. |*None*|
|**`endText`**|Text after countdown. |*None*|
|**`intervalText`**|A function to reture a text during countdown. |*None*|
|**`afterEnd`**|A callback function after countdown. |*None*|

##Methods

| Method | Description | Params |
|---|---|---|
|**`start`**|start countdown. |*None*|
|**`end`**|finish countdown. |*None*|
