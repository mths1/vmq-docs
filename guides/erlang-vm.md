= Erlang Tuning =

The Erlang Virtual Machine offers a log of configurable choices that encompass process scheduler configurations, 
memory allocation, garbage collection, I/O operations, and additional settings. Adjusting these parameters can profoundly alter 
the operational dynamics of a VerneMQ node during runtime. In the following we briefly discuss the two most important factors Memory allocation 
and CPU tuning.

== CPU ==

== Memory Allocation ==
Erlang (or to be more precise the Erlang VM) is responsible for memory management. Erlang is known to be very stable and almost all crashes of the Erlang VM are due to out-of-memory (OOM) situations.

Memory allocation occurs through block assignments sourced from pre-allocated regions, Erlang terminology, called carriers. 
The parameters governing carrier size, block dimensions, memory allocation strategies, and comparable facets collectively fall 
under the umbrella of allocator settings.

Memory fragmentation in VerneMQ varies based on the chosen allocator settings and the nature of the workload. Identifying the optimal 
configuration for your specific workload demands a blend of experimentation, metric-driven assessments, 
and a trial-and-error methodology. Importantly, it's crucial to recognize that a certain level of fragmentation is inherent to the process.

== Swap space ==
Erlang applications such as VerneMQ, built for real-time and low-latency scenarios, are designed to take advantage of physical RAM. Swapping data between RAM and disk is significantly slower than accessing data directly from memory. This can lead to noticeable slowdowns and increased response times. Therefore, utilizing swap space for Erlang applications is generally not recommended. Nonetheless, swap space can prevent an application from crashing due to running out of memory. Swap space can serve as a safety net, in case the garbage collector needs too much memory for a brief period of time. It is recommended to monitor the swap space usage and in case it is non-zero to investigate. Especially, in case you experience performance degradation.

== Transparent Huge Pages (THP) ==




