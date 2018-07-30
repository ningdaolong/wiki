---
title: Android 编译时警告
date: 2018-05-08
categories: 
- android
tags: 
- android
---
Unchecked cast: Any? to Triple<String, String, String>
------------------------------------------------------------ 
val value = message.annex as Triple<String, String, String> 提示 Unchecked cast: Any? to Triple<String, String, String>
添加 @Suppress("UNCHECKED_CAST") 
@Suppress("UNCHECKED_CAST") 
val value = message.annex as Triple<String, String, String>

Parameter 'newItemPosition' is never used
---------------------------------------------------------------
fun getChangePayload(oldItemPosition: Int, newItemPosition: Int): Unit{} 
提示 Parameter 'newItemPosition' is never used 修改如下
fun getChangePayload(oldItemPosition: Int, @Suppress("UNUSED_PARAMETER")newItemPosition: Int): Unit{}

INSTALL_FAILED_NO_MATCHING_ABIS: Failed to extract native libraries, res=-113
---------------------------------------------------------------
在AndroidStudio 的build.gradle（Moudule：app） 文件中
android{
	splits {
		abi {
			enable true
			reset()
			include 'x86', 'armeabi-v7a','x86_64'
			universalApk true
		}
	}
}




