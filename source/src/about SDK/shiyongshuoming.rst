﻿.. _sdk_Instructions:

SDK使用说明
=====================

SDK开发包随本文档一起提供，开发包中分为linux和windows版本。其中windows版本依赖库放在SDK-bin.zip中，Linux版依赖库放在SDK-lin.zip中，头文件放在include文件夹中，demo文件夹存放了示例代码。

要使用SDK，首先需要创建SDK对象：

.. code-block:: javascript

  CIMRSDK* pSDK = new CIMRSDK();

为了获得原始IMU及摄像头数据，按照如下方式设置回调函数：

.. code-block:: javascript

  void IMUCallback(double time, float accX, float accY, float accZ, float gyrX, float gyrY, float gyrZ, void* pParam){}

  pSDK->RegistModuleIMUCallback(IMUCallback,param);

  void ImageCallback(double time, unsigned char* pLeft, unsigned char* pRight, int width, int height, int channel, void* pParam){}

  pSDK->RegistModuleIMUCallback(ImageCallback,param);

要获取Slam解算后的位姿，需要设置如下回调：

.. code-block:: javascript

  void ModulePoseCallback(int, void* pData, void* pParam) {
  }

  //pSDK->RegistModulePoseCallback(HMDPoseCallback, NULL);

要获取depthimage插件的左目去畸变图像：

.. code-block:: javascript

  void DepthImageCallback(int ret, void* pData, void* pParam) {
  }

  //pSDK->AddPluginCallback("depthimage", "depth", DepthImageCallback, NULL);

后续将提供更多插件以增强SDK的功能。


