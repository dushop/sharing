### 为什么通常在发送数据埋点请求的时候使用的是 1x1 像素的透明 gif 图？

原文 https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/87

- 能够完成整个 HTTP 请求+响应（尽管不需要响应内容）
- 触发 GET 请求之后不需要获取和处理数据、服务器也不需要发送数据
- 跨域友好
- 执行过程无阻塞
- 相比 XMLHttpRequest 对象发送 GET 请求，性能上更好
- GIF的最低合法体积最小（最小的BMP文件需要74个字节，PNG需要67个字节，而合法的GIF，只需要43个字节）

参考资料：
- [SegmentFault 上的回答](https://segmentfault.com/q/1010000000146284/a-1020000000146319)
- [Web beacon](https://en.wikipedia.org/wiki/Web_beacon)
- [Using a Beacon Image for GitHub, Website and Email Analytics](https://www.sitepoint.com/using-beacon-image-github-website-email-analytics/)
- [为什么前端监控要用 GIF 打点](https://mp.weixin.qq.com/s/v6R2w26qZkEilXY0mPUBCw?utm_source=tuicool&utm_medium=referral)