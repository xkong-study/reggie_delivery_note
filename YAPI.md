本地项目中使用 YAPI         
直接使用：如果后端接口已经开发完成并且已经通过 YAPI 定义了接口信息，那么前端或测试可以直接通过 YAPI 访问这些接口进行开发和测试。这意味着 YAPI 中定义的接口地址应该是可访问的后端服务地址，而不是 Mock 地址。    
后端直接swagger导入json数据，导入所有api。     

Mock数据使用：在后端接口尚未开发完成的情况下，前端或测试可以利用 YAPI 生成的 Mock 数据进行独立开发和测试。这时，YAPI 中的接口就是用来 Mock 的，前端在调用接口时使用的是 YAPI 提供的 Mock 地址。         

<img width="339" alt="截屏2024-04-09 20 04 33" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/2a7ac864-486d-46bd-b01a-fca78f4e8948">
<img width="744" alt="截屏2024-04-09 20 05 25" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/bd0b4ae2-41ca-4951-afe7-360dc2f9078c">
<img width="577" alt="截屏2024-04-09 20 07 40" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/34acb791-5004-4b44-b832-8feff43ff897">
