# IntroductionOS

Nama: Salsabilla zahratul ramadhani

NRP: 3124521013

Kelas: 1 TI A 

# Practicexcersises

1.1.	 What are the three main purposes of an operating system?

•	Manage hardware resources like CPU, memory, storage, and I/O devices.

•	Provide an interface for users and applications to interact with the system.

•	Ensure that programs run efficiently by handling tasks like scheduling and memory management.

1.2	We have stressed the need for an operating system to make efficient use of the computing hardware. When is it appropriate for the operating system to forsake this principle and to "waste" resources? Why is such a system not really wasteful?

An OS may "waste" resources to improve usability, reliability, and security. Examples include GUI for better user experience, idle CPU time for responsiveness, redundant storage for faster access, and virtualization for flexibility. These trade-offs enhance overall system effectiveness, making them not truly wasteful. 

1.3	What is the main difficulty that a programmer must overcome in writing an operating system for a real-time environment?

The main challenge in writing an OS for a real-time environment is ensuring that tasks meet strict timing constraints. The system must guarantee that critical operations complete within a defined time, regardless of workload. This requires precise scheduling, low-latency response times, and efficient resource management to avoid delays. Failure to meet deadlines can lead to system failures, especially in critical applications like medical devices.

1.4	Keeping in mind the various definitions of operating system, consider whether the operating system should include applications such as web browsers and mail programs. Argue both that it should and that it should not, and support your answers.

The OS is mainly there to manage hardware and provide core services. One view is that including apps like web browsers and mail programs can offer a seamless, integrated experience. Built-in apps can be fine-tuned for the system, making them more secure and easier for users to access right out of the box. On the other hand, these apps aren't really part of the OS’s essential job. Keeping them separate means they can be updated independently, allowing more flexibility and avoiding unnecessary bloat in the OS. So while a bundled approach might simplify things for some users, it can also limit choice and make maintenance tougher.

1.5	How does the distinction between kernel mode and user mode function as a rudimentary form of protection (security)?

The kernel/user mode split works as a basic security measure by limiting what a program can do. In user mode, a program can’t access hardware or sensitive system areas directly, which stops buggy or malicious code from messing up core functions. Only when a process needs to perform a privileged operation does it switch to kernel mode, which has full access. This separation, enforced by the CPU, helps keep the system stable and secure.

1.6	Which of the following instructions should be privileged? 

a. Set value of timer. 

b. Read the clock. 

c. Clear memory. 

d. Issue a trap instruction.

e. Turn off interrupts. 

f. Modify entries in device-status table. 

g. Switch from user to kernel mode. 

h. Access I/O device.

Privileged instructions:  Set value of timer, Clear memory, Turn off interrupts, Modify entries in device-status table, Switch from user to kernel mode, Access I/O device.
Non-privileged: Read the clock, Issue a trap instruction.

1.7	Some early computers protected the operating system by placing it in a memory partition that could not be modified by either the user job or the operating system itself. Describe two difficulties that you think could arise with such a scheme.

1.	No OS Updates or Fixes: I think the OS cannot modify itself, meaning bug fixes, security patches, or system updates would be impossible without replacing the entire OS.
2.	Limited Flexibility:  Modern OSes need to dynamically manage memory, load drivers, and modify configurations. A fully protected partition would restrict these essential operations.

1.8	 Some CPUs provide for more than two modes of operation. What are two possible uses of these multiple modes?

Extra modes can be used for virtualization, allowing a hypervisor to run multiple OSes without giving them full kernel access. They also help in setting different privilege levels for system processes, separating critical OS functions from regular kernel tasks. This improves security and access control.

1.9	Timers could be used to compute the current time. Provide a short description of how this could be accomplished.

A timer can be set to generate interrupts at regular intervals, such as every millisecond. The OS maintains a counter that increments with each timer interrupt. By keeping track of these increments, the system can calculate the current time based on a predefined starting point, such as system boot time.

1.10	Give two reasons why caches are useful. What problems do they solve? What problems do they cause? If a cache can be made as large as the device for which it is caching (for instance, a cache as large as a disk, why not make it that large and eliminate the device?

Caches are useful because they speed up data access by storing frequently used information closer to the CPU, reducing the need to fetch data from slower memory or storage. They solve the problem of slow memory access by making retrieval faster and reducing latency. But they also cause issues like cache consistency, where data needs to stay in sync with the main storage, and they can be expensive because fast memory costs more. A cache can’t just replace the main device because it would be too costly to make one as large as a disk. Plus, caches are designed for temporary storage, while disks provide long-term, non-volatile storage.

1.11	Distinguish between the client-server and peer-to-peer models of distributed systems.

In the client-server model, one device (the server) provides services, and other devices (clients) request them. It’s centralized, making management easier but creating a single point of failure. In the peer-to-peer model, all devices share resources directly without a central server. It’s more scalable and resilient but harder to manage since there’s no central control.

1.12	How do clustered systems differ from multiprocessor systems? What is required for two machines belonging to a cluster to cooperate to provide a highly available service?

Clustered systems use multiple independent computers working together, while multiprocessor systems have multiple CPUs within a single machine sharing memory and resources. Clusters rely on network connections, whereas multiprocessors use shared memory for faster communication.

For two machines in a cluster to provide high availability, they need to share storage and use a coordination mechanism.

1.13	Consider a computing cluster consisting of two nodes running a database. Describe two ways in which the cluster software can manage access to the data on the disk. Discuss the benefits and disadvantages of each.

One way is asymmetric clustering, where one node actively handles the database while the other stays on standby, ready to take over if the active node fails. This improves reliability but wastes resources since the standby node is mostly idle. Another way is symmetric clustering, where both nodes actively process database requests, sharing the workload. This improves performance and resource utilization but requires complex synchronization to avoid conflicts when accessing the disk.

1.14	What is the purpose of interrupts? How does an interrupt differ from a trap? Can traps be generated intentionally by a user program? If so, for what purpose?

Interrupts signal the CPU to stop its current task and handle an important event, like input from a keyboard or a completed I/O operation. They help the OS manage multiple tasks efficiently.

A trap is a type of software-generated interrupt, usually triggered by an error like division by zero or a system call. Unlike hardware interrupts, traps come from the executing program itself. And yes, traps can be intentionally generated by user programs, mainly to request OS services through system calls, like reading a file or allocating memory.

1.15	Explain how the Linux kernel variables HZ and jiffies can be used to determine the number of seconds the system has been running since it was booted.

In Linux, HZ defines the number of timer ticks per second, and jiffies is a counter that increments with each tick. To calculate uptime, you divide jiffies by HZ. For example, if HZ is 100 and jiffies is 500,000 means the system has been running for 5000 sec since boot. 

1.16	Direct memory access is used for high-speed I/O devices in order to avoid increasing the CPU's execution load. 

a. How does the CPU interface with the device to coordinate the transfer? 

b. How does the CPU know when the memory operations are complete? 

c. The CPU is allowed to execute other programs while the DMA controller is transferring data. Does this process interfere with the execution of the user programs? If so, describe what forms of interference are caused.

a.	The CPU sets up the Direct Memory Access (DMA) transfer by giving the DMA controller details like memory addresses, transfer size, and the I/O device involved. Once configured, the DMA controller handles the transfer independently.

b.	When the transfer is complete, the DMA controller sends an interrupt to the CPU, letting it know that the operation has finished.

c.	Yes, DMA can interfere with user programs because it accesses the memory bus, temporarily blocking the CPU from accessing memory. This can cause minor delays in execution, especially if multiple DMA transfers happen at once. However, the performance gain from offloading data transfers usually outweighs the small interruptions.


1.17	Some computer systems do not provide a privileged mode of operation in hardware. Is it possible to construct a secure operating system for these computer systems? Give arguments both that it is and that it is not possible.

Possible: A secure OS can still be built using software-based protection mechanisms like virtualization, sandboxing, and access control policies. The OS can enforce strict execution rules and limit what user programs can do, reducing security risks.

Not possible: Without hardware-enforced privilege levels, user programs could directly access system resources, making it easier for malware or faulty programs to corrupt memory, modify system settings, or interfere with critical operations. Software-based protections alone may not be strong enough to prevent all security threats.

1.18	Many SMP systems have different levels of caches; one level is local to each processing core, and another level is shared among all processing cores. Why are caching systems designed this way?

Caching is designed this way to balance speed and efficiency.

•	Local (per-core) caches provide fast access to frequently used data, reducing latency since each core can retrieve data without waiting on others.
•	Shared caches allow cores to exchange data efficiently and help maintain consistency, reducing the need for expensive memory access.

1.19	Rank the following storage systems from slowest to fastest:

a.	Hard-disk drivers

b.	Registers

c.	Optical disk

d.	Main memory

e.	Nonvolatile memory

f.	Magnetic tapes

g.	Cache

Magnetic tapes → Optical disk → Hard-disk drives → Non-volatile memory → Main memory → Cache → Registers

1.20	Consider an SMP system similar to the one shown in figure 1.8. Illustrate with an example how data residing in memory could in fact have a different value in each of the local caches.

In an SMP system, each core has its own local cache, which can lead to cache inconsistency if proper synchronization isn’t maintained.

For Example: 

	Core 1 loads J = 10 into its local cache and updates it to J = 20.

	Core 2, unaware of Core 1’s update, loads J = 10 into its own cache.

	Now, memory still has J= 10, but Core 1’s cache has J = 20, and Core 2’s cache has J = 10, which causing inconsistency.

1.21	Discuss, with examples, how the problem of maintaining coherence of cached data manifests itself in the following processing environments:

a.	Single-processor systems

b.	Multiprocessor systems

c.	Distributed systems

a.	Single-processor systems: Issues arise when external devices likeDMA update memory, but the CPU still reads old cached data.

b.	Multiprocessor systems: Each core has its own cache, leading to outdated values if changes aren’t synchronized. Solved using cache coherence protocols like MESI.

c.	Distributed systems: Different computers may store outdated copies of shared data. Solved using consistency models like write-through caching or distributed locking.

1.22	Describe a mechanism for enforcing memory protection in order to prevent a program from modifying the memory associated with other programs.

Memory protection is enforced using an MMU with base and limit registers. The base register sets the program’s memory start, and the limit register defines its range. If a program accesses memory outside this range, the OS blocks it, preventing interference with other programs.

1.23	Which network configuration (LAN or WAN) would best suit with other programs.

a.	A campus students union

b.	Several campus location across a statewide university system

c.	A neighborhood

a.	Campus student union = LAN, Covers a small area with high-speed connectivity.

b.	Several campus locations across a statewide university system = WAN, Connects multiple distant locations.

c.	A neighborhood = LAN, If within a small area, like a community network.

1.24	Describe some of the challenges of designing operating systems for mobile devices compared with designing operating systems for traditional PCs.

•	Limited resources, Mobile devices have less CPU power, memory, and battery life, requiring efficient resource management.

•	Touch interface, Unlike PCs with keyboards and mice, mobile OS must be optimized for touch gestures.

•	Connectivity, Mobile OS needs to handle frequent network changes (Wi-Fi, cellular) and power-efficient communication.

•	App restrictions, Security and sandboxing are stricter to prevent malicious apps from affecting the system.

•	Energy efficiency, Power management is crucial since mobile devices rely on batteries.

1.25	What are some advantages of peer-to-peer systems over client-server systems?

•	No single point of failure, Since there’s no central server, the system is more resilient.

•	Scalability, More devices can join without overloading a central server.

•	Cost-effective, No need for expensive server hardware or maintenance.

•	Better resource utilization, Each device contributes computing power and storage.

1.26	Describe some distributed applications that would be appropriate for a peer-to-peer system.

•	File-sharing networks, Users share files directly without a central server.

•	Blockchain and cryptocurrencies, Transactions are verified by multiple peers instead of a central authority.

•	Video conferencing, Calls can be routed directly between users.

•	Online gaming, Some multiplayer games use P2P to reduce server load and latency.

1.27	Identify several advantages and several disadvantages of open-source operating systems. Identify the types of people who would find each aspect to be an advantage or a disadvantage.

Open-source OS is free, customizable, and has strong community support, making it great for developers, researchers, and tech enthusiasts. It also offers better security through transparency. However, it can be less user-friendly, lacks official support, and may have compatibility issues, which can be a drawback for casual users and businesses.
