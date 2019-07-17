---
title: postMessage异步通讯
date: 2019-07-17 14:17:04
tags: JS
---
## 1.文档目的
web端异步消息传递机制,特别是对于跨域情况下的通讯,显得尤其重要,主要应用场景iframe和webview

## 2.实践积累
iframe形式
```
// 父页面
<html>
  <body>
    <p>我是父页面</p>
    <button id="btn">获取子页面信息</button>
    <iframe id="mapIframe" height="850px" width="1500px" src="http://fp1.xys.gov.cn/map/index.html#/map"></iframe>
    <script>
      // 触发事件
      document.getElementById('btn').addEventListener('click', function() {
        document.getElementById('mapIframe').contentWindow.postMessage(JSON.stringify({ data: 'getLocation' }), '*')
      })
      // 父页面监听事件
      window.addEventListener('message',function(event) {
        console.log(JSON.parse(event.data), '--父页面监听数据')
      },false)
    </script>
  </body>
</html>
// 子页面监听
      window.addEventListener('message', function (event) {
        if (typeof (event.data) === 'string') {
          console.log(JSON.parse(event.data), '--子页面接收的数据')
          // 向父窗口发送事件
          if (window.parent && window.postMessage) {
            // let message = { loadFinish: true }
            window.parent.postMessage(JSON.stringify({ data: 'success' }), '*')
          }
        }
      }, false)
```
webview形式
```
// RN项目父页面
import { WebView } from 'react-native-webview'
<View style={{ flex: 1 }}>
        <WebView
          ref={ref => (this.webView = ref)}
          source={webviewUrl}
          startInLoadingState={true}
          renderLoading={() => <Loading active />}
          javaScriptEnabled={true}
          domStorageEnabled={true}
          useWebKit={true}
          automaticallyAdjustContentInsets={false}
          onLoadEnd={this.onLoadEnd}
          onLoadStart={this.onLoadStart}
          obLoadEnd={this.onLoadEnd}
          onError={this.onLoadError}
          onMessage={this.onMessage}
        />
      </View>

   onLoadEnd = () => {
    this.webView.postMessage(JSON.stringify({data:'hi'}))
  }

    onMessage = event => {
    try {
      let { loadFinish } = JSON.parse(event.nativeEvent.data)
    } catch (error) {}
  }
// web端子页面
window.onload = () => {
  document.addEventListener('message', ({ data }) => {
    const msg = JSON.parse(data);
  })
  // 消息回传给rn端
  if (window.postMessage) {
            let message = { loadFinish: true };
            window.postMessage(JSON.stringify(message));
          }
}
```
