---
title: android-crash-01
date: 2017-09-28 15:15:06
categories: android
tags: track
---

## Issue-1
```
java.lang.NullPointerException: Attempt to invoke virtual method 'java.lang.Object android.content.Context.getSystemService(java.lang.String)' on a null object reference
	at android.view.LayoutInflater.from(LayoutInflater.java:232)
	at android.view.View.inflate(View.java:21035)
	at com.lenovo.da.fragment.StreamFragment$StreamsExpandableListAdapter.getChildView(StreamFragment.java:227)
	at com.lenovo.da.fragment.StreamFragment.setCollapseListViewHeightBasedOnChildren(StreamFragment.java:417)
	at com.lenovo.da.fragment.StreamFragment$2.onGroupCollapse(StreamFragment.java:101)
	at android.widget.ExpandableListView.collapseGroup(ExpandableListView.java:779)
	at com.lenovo.da.fragment.StreamFragment$3.doResponse(StreamFragment.java:133)
	at com.lenovo.da.api.ApiService$CallbackFunc.onResponse(ApiService.java:130)
	at retrofit2.ExecutorCallAdapterFactory$ExecutorCallbackCall$1$1.run(ExecutorCallAdapterFactory.java:68)
	at android.os.Handler.handleCallback(Handler.java:751)
	at android.os.Handler.dispatchMessage(Handler.java:95)
	at android.os.Looper.loop(Looper.java:154)
	at android.app.ActivityThread.main(ActivityThread.java:6196)
	at java.lang.reflect.Method.invoke(Native Method)
	at com.android.internal.os.ZygoteInit$MethodAndArgsCaller.run(ZygoteInit.java:888)
	at com.android.internal.os.ZygoteInit.main(ZygoteInit.java:778)
```
> fragment在重新创建的过程中，可能getContext()为空，可利用onAttach(Context context)来引用context

## Issue-2
```
java.lang.IllegalArgumentException: View=DecorView@abf9228[] not attached to window manager
	at android.view.WindowManagerGlobal.findViewLocked(WindowManagerGlobal.java:473)
	at android.view.WindowManagerGlobal.removeView(WindowManagerGlobal.java:382)
	at android.view.WindowManagerImpl.removeViewImmediate(WindowManagerImpl.java:124)
	at android.app.Dialog.dismissDialog(Dialog.java:383)
	at android.app.Dialog.dismiss(Dialog.java:366)
	at com.lenovo.da.utils.CommonUtils.togglePieChartProgressDialog(CommonUtils.java:123)
	at com.lenovo.da.activity.gesturelock.ResetValidateActivity$3.doResponse(ResetValidateActivity.java:192)
	at com.lenovo.da.api.ApiService$CallbackFunc.onResponse(ApiService.java:130)
	at retrofit2.ExecutorCallAdapterFactory$ExecutorCallbackCall$1$1.run(ExecutorCallAdapterFactory.java:68)
	at android.os.Handler.handleCallback(Handler.java:751)
	at android.os.Handler.dispatchMessage(Handler.java:95)
	at android.os.Looper.loop(Looper.java:154)
	at android.app.ActivityThread.main(ActivityThread.java:6196)
	at java.lang.reflect.Method.invoke(Native Method)
	at com.android.internal.os.ZygoteInit$MethodAndArgsCaller.run(ZygoteInit.java:888)
	at com.android.internal.os.ZygoteInit.main(ZygoteInit.java:778)
```
> 创建了一个没有attached to window manager的dialog，调用dialog.dismiss时windowManagerGlobal找不到此view
