# Docker

## Docker简介
来自维基百科的简介

Docker 是一个开放源代码软件，是一个开放平台，用于开发应用、交付应用、运行应用。 Docker允许用户将基础设施中的应用单独分割出来，形成更小的颗粒（容器），从而提高交付软件的速度。

Docker容器与虚拟机类似，但二者在原理上不同。容器是将操作系统层虚拟化，虚拟机则是虚拟化硬件，因此容器更具有便携性、高效地利用服务器。 容器更多的用于表示软件的一个标准化单元。由于容器的标准化，因此它可以无视基础设施的差异，部署到任何一个地方。另外，Docker也为容器提供更强的业界的隔离兼容。

Docker 利用Linux核心中的资源分离机制，例如cgroups，以及Linux核心名字空间，来创建独立的容器。这可以在单一Linux实体下运作，避免引导一个虚拟机造成的额外负担。Linux核心对名字空间的支持完全隔离了工作环境中应用程序的视野，包括行程树、网络、用户ID与挂载文件系统，而核心的cgroup提供资源隔离，包括CPU、存储器、block I/O与网络。从0.9版本起，Dockers在使用抽象虚拟是经由libvirt的LXC与systemd - nspawn提供界面的基础上，开始包括libcontainer库做为以自己的方式开始直接使用由Linux核心提供的虚拟化的设施，


## Docker镜像操作


## Docker容器操作


## Docker安装常用软件



## Docker挂载Volume
