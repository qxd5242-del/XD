# 此笔记基于王道
TCP/IP五层模型：物理层，数据链路层，网络层，传输层，应用层   
OSI参考模型：物理层，数据链路层，网络层，运输层，会话层，表示层，应用层   
## 数据链路层    
- 停止等待协议（S-W）：滑动窗口机制、确认机制（确认帧ACK）、超时重传，可以实现流量控制、可靠传输  
- 后退N帧协议（GBN）：滑动窗口机制、确认帧（可以累计确认）、超时重传（若未收到第i个帧，则重传i帧及其之后的所有帧）  
- 选择重传协议（SR）：滑动窗口机制（发送窗口>1，接收窗口>1，接收窗口不能大于发送窗口）、确认机制（不能累计确认，新增否定帧NAK）、超时重传、请求重传  
- ALOHA协议：纯ALOHA、时隙ALOHA
    - 纯ALOHA：立即发送，未收到ACK则随机等待一段时间后重传
    - 时隙ALOHA：时隙大小固定
- CSMA/CD协议：先听后发，边听边发，冲突停发，随机重发（第10次冲突为分水岭，第16此次冲突时放弃传帧并报告网络层）
- CSMA/CA协议：先听后发，忙则随机退避（用二进制指数退避算法确定随机退避时间），可选信道预约机制（发送方广播RTS控制帧、AP广播CTS控制帧、其余无关节点收到CTS后会禁言）
- 点对点协议（PPP协议）：由链路控制协议（LCP）、网络控制协议（NCP）和PPP帧格式构成
    - LCP：用于建立、配置LCP链路（例如协商数据链路层的MTU、认证协议）
    - NCP：为网络层协议建立和配置逻辑链接（例如：网络层使用IP协议，则NCP要负责申请一个IP地址，每个不同的网络层协议都要有一个相应的NCP来配置）
    ![图1](picture/p1.jpg)
    ![图2](picture/p2.jpg)

## 网络层  
- 地址解析协议（ARP协议）：
    ![图3](picture/p3.jpg)
    ![图4](picture/p4.jpg)
   
- 动态主机配置协议（DHCP）：
    ![图5](picture/p5.jpg)
    ![图6](picture/p6.jpg)
  
- 网际控制报文协议（ICMP）：
    ![图7](picture/p7.jpg)
  
- 路由信息协议（RIP）：
    ![图8](picture/p8.jpg)
    ![图9](picture/p9.jpg)
    ![图10](picture/p10.jpg)
    ![图11](picture/p11.jpg)
  
- 开发最短路径优先协议（OSPF）:
    ![图12](picture/P12.jpg)
    ![图13](picture/P13.jpg)
	![图14](picture/P14.jpg)

- 边界网关协议(BGP)：
 	![图15](picture/p15.jpg)
	![图16](picture/p16.jpg)
	![图17](picture/p17.jpg)
	![图18](picture/p18.jpg)
	![图19](picture/p19.jpg)

## 传输层
- UDP协议：
	![图20](picture/p20.jpg)
	![图21](picture/p21.jpg)
	![图22](picture/p22.jpg)
	![图23](picture/p23.jpg)
	![图24](picture/p24.jpg)

- ### **TCP协议:**
	![图25](picture/p25.jpg)
	![图26](picture/p26.jpg)
	![图27](picture/p27.jpg)
	![图28](picture/p28.jpg)
	![图29](picture/p29.jpg)
	![图30](picture/p30.jpg)
	![图31](picture/p31.jpg)
	![图32](picture/p32.jpg)
	![图33](picture/p33.jpg)
	![图34](picture/p34.jpg)
	![图35](picture/p35.jpg)
	![图36](picture/p36.jpg)
	![图37](picture/p37.jpg)
	![图38](picture/p38.jpg)
	![图39](picture/p39.jpg)
	![图40](picture/p40.jpg)
	![图41](picture/p41.jpg)
	![图42](picture/p42.jpg)
	![图43](picture/p43.jpg)
	![图44](picture/p44.jpg)
	![图45](picture/p45.jpg)
	![图46](picture/p46.jpg)
	![图47](picture/p47.jpg)
	![图48](picture/p48.jpg)
	![图49](picture/p49.jpg)
	![图50](picture/p50.jpg)
	![图51](picture/p51.jpg)
	![图52](picture/p52.jpg)
  
## 应用层  
- DNS：
	![图53](picture/p53.jpg)
	![图54](picture/p54.jpg)
	![图55](picture/p55.jpg)
	![图56](picture/p56.jpg)
	![图57](picture/p57.jpg)
	![图58](picture/p58.jpg)
	![图59](picture/p59.jpg)

- 文件传输协议（FTP）：
	![图60](picture/p60.jpg)
	![图61](picture/p61.jpg)

- 超文本传输协议（HTTP）:
	![图62](picture/p62.jpg)
	![图63](picture/p63.jpg)
	![图64](picture/p64.jpg)

