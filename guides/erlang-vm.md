Erlang Tuning

The Erlang Virtual Machine offers a log of configurable choices that encompass process scheduler configurations, 
memory allocation, garbage collection, I/O operations, and additional settings. Adjusting these parameters can profoundly alter 
the operational dynamics of a VerneMQ node during runtime. In the following we briefly discuss the two most important factors Memory allocation 
and CPU tuning.

CPU

Memory Allocation
Erlang (or to be more precise the Erlang VM) is responsible for memory management. Erlang is known to be very stable. 

Memory allocation occurs through block assignments sourced from pre-allocated regions, Erlang terminology, called carriers. 
The parameters governing carrier size, block dimensions, memory allocation strategies, and comparable facets collectively fall 
under the umbrella of allocator settings.

Memory fragmentation in VerneMQ varies based on the chosen allocator settings and the nature of the workload. Identifying the optimal 
configuration for your specific workload demands a blend of experimentation, metric-driven assessments, 
and a trial-and-error methodology. 
Importantly, it's crucial to recognize that a certain level of fragmentation is inherent to the process.

