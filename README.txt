﻿epoll多线程模式，模仿IOCP设计,一个线程在epoll上监听，一组工作线程等待在完成队列上。
用户发出IO请求时，如果当前IO处于激活态，则直接完成IO请求并返回结果，否则，请求将被缓存。
当epoll发现套接口从非激活态变成激活态时，如果有未被处理的IO请求，则弹出一个请求执行，并
将结果提交到完成队列中，供工作线程提取。