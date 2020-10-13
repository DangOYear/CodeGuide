# LinuxIO模型

## select

轮询有个数限制1024个

## poll

也是轮询没有个数限制1024，底层链表存储

## epoll

IO就绪回调处理。