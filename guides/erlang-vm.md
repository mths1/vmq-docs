# Erlang Tuning 

The Erlang Virtual Machine offers a log of configurable choices that encompass process scheduler configurations, 
memory allocation, garbage collection, I/O operations, and additional settings. Adjusting these parameters can profoundly alter 
the operational dynamics of a VerneMQ node during runtime. In the following we briefly discuss the two most important factors Memory allocation 
and CPU tuning, as well as some OS configurations that have a direct impact on them.

## CPU 

## Memory 
In the following we will briefly discuss memory allocation, as well swap space and transparent huge pages (THP).

### Memory Allocation
Erlang (or to be more precise the Erlang VM) is responsible for memory management. Erlang is known to be very stable and almost all crashes of the Erlang VM are due to out-of-memory (OOM) situations.

Memory allocation occurs through block assignments sourced from pre-allocated regions, Erlang terminology, called carriers. 
The parameters governing carrier size, block dimensions, memory allocation strategies, and comparable facets collectively fall 
under the umbrella of allocator settings.

Memory fragmentation in VerneMQ varies based on the chosen allocator settings and the nature of the workload. Identifying the optimal 
configuration for a specific workload needs experimentation and metric-driven assessments.

Erlang documentation:
* http://erlang.org/doc/man/erts_alloc.html

### Swap space 
Erlang applications such as VerneMQ, built for real-time and low-latency scenarios, are designed to take advantage of physical RAM. Swapping data between RAM and disk is significantly slower than accessing data directly from memory. This can lead to noticeable slowdowns and increased response times. Therefore, utilizing swap space for Erlang applications is generally not recommended. Nonetheless, swap space can prevent an application from crashing due to running out of memory. Swap space can serve as a safety net, in case the garbage collector needs too much memory for a brief period of time. It is recommended to monitor the swap space usage and in case it is non-zero to investigate. Especially, in case you experience performance degradation.

There is currently no consensus on if its preferable to run a server with our without swap space. Riak recommends to disable swap space, while RabbidMQ highly recommends enabling it.  


### Transparent Huge Pages (THP)
Transparent Huge Pages (THP) is a Linux kernel feature designed to optimize memory management by consolidating standard memory pages into larger pages, reducing memory overhead and improving memory access speed for data-intensive applications. The kernel manages page conversion based on memory usage patterns. While THP can enhance performance in some cases, its impact varies depending on the workload, and it might introduce overhead for latency-sensitive applications due to potential memory fragmentation and page migration delays. 

Riak suggests to disable THP, as well as Redis, MongoDB, RabbitMQ and Kafka. 
