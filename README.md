# CPU-Scheduling-Algorithms
An implementation of various CPU scheduling algorithms in C++. The algorithms included are First Come First Serve (FCFS), Round Robin (RR), Shortest Process Next (SPN), Shortest Remaining Time (SRT), Highest Response Ratio Next (HRRN), Feedback (FB) and Aging.

## Algorithms

### First Come First Serve (FCFS)
- FCFS is a scheduling algorithm where the first process to arrive is executed first.
- Simple and easy to understand.
- Non-preemptive: No process prioritization mechanism.
- Can lead to poor performance with processes having long burst times.
- Longer running processes can block shorter ones from execution.
- Commonly used in batch systems where the process order is important.

### Round Robin with varying time quantum (RR)
- Round Robin (RR) with variable quantum uses adjustable time slices.
- Shorter processes get smaller quantum longer processes get larger quanta.
- Maintains a queue each process gets CPU time, then moves to the back.
- Increases efficiency and reduces average waiting time.
- Prevents starvation of longer processes.

### Shortest Process Next (SPN)
- SPN prioritizes processes based on their burst time.
- Non-preemptive: Processes run to completion once started.
- Maintains a queue sorted by burst time; shortest burst time processes are executed first.
- Beneficial for minimizing average waiting time.
- Can cause longer processes to be blocked by shorter ones, potentially impacting performance.
- Commonly used when minimizing average waiting time is the goal.

### Shortest Remaining Time (SRT)
- SRT prioritizes processes based on their remaining time.
- Preemptive: Can interrupt a running process if a new process with a shorter remaining time arrives.
- Maintains a queue sorted by remaining time; shortest remaining time processes are executed first.
- Beneficial for minimizing average waiting time.
- Adaptable to situations where burst time is not known in advance.
- Commonly used to minimize average waiting time when burst time is uncertain.

### Highest Response Ratio Next (HRRN)

- HRRN prioritizes processes based on their response ratio.
- Non-preemptive: Processes run to completion once started.
- Response ratio = (Waiting time + Burst time) / Burst time.
- Processes with the highest response ratio are executed first.
- Beneficial for minimizing average waiting time, especially for processes with longer waiting times.
- Adaptable to situations where burst time is not known in advance.
- Commonly used to minimize average waiting time when burst time is uncertain.

### Feedback (FB)

- Feedback allocates CPU time based on priority levels.
- Uses multiple priority queues, each with a different priority level.
- Higher priority processes are executed first.
- New processes are added to the appropriate priority queue.
- Completed processes move to the next lower priority queue.
- Beneficial for handling a mix of short and long-running processes with varying priority levels.
- Ensures high-priority processes are executed first while eventually executing lower-priority processes.

### Feedback with varying time quantum (FBV)
- Same as [Feedback] but with varying time quantum.
- Feedback with varying time quantum also uses multiple priority queues and assigns a different time quantum for each priority level, it allows the algorithm to be more efficient by spending more time on higher-priority processes and less time on lower-priority processes.

### Aging

- Xinu is an operating system developed at Purdue University. The scheduling invariant in Xinu assumes that at any
time, the highest priority process eligible for CPU service is executing, with round-robin scheduling for processes of
equal priority. Under this scheduling policy, the processes with the highest priority will always be executing. As a
result, all the processes with lower priority will never get CPU time. As a result, starvation is produced in Xinu when
we have two or more processes eligible for execution that have different priorities. For ease of discussion, we call the
set of processes in the ready list and the current process as the eligible processes.

- To overcome starvation, an aging scheduler may be used. On each rescheduling operation, a timeout for instance, the
scheduler increases the priority of all the ready processes by a constant number. This avoids starvation as each ready
process can be passed over by the scheduler only a finite number of times before it has the highest priority.

- Each process has an initial priority that is assigned to it at process creation. Every time the scheduler is called it takes
the following steps.
    - The priority of the current process is set to the initial priority assigned to it.
    - The priorities of all the ready processes (not the current process) are incremented by 1.
    - The scheduler choses the highest priority process from among all the eligible processes.

- Note that during each call to the scheduler, the complete ready list has to be traversed.

## Input Format
- Line 1: "trace" or "stats"
- Line 2: a comma-separated list telling which CPU scheduling policies to be analyzed/visualized along with
their parameters, if applicable. Each algorithm is represented by a number as listed in the
introduction section and as shown in the attached testcases.
Round Robin and Aging have a parameter specifying the quantum q to be used. Therefore, a policy
entered as 2-4 means Round Robin with q=4. Also, policy 8-1 means Aging with q=1.
 1. FCFS (First Come First Serve)
 2. RR (Round Robin)
 3. SPN (Shortest Process Next)
 4. SRT (Shortest Remaining Time)
 5. HRRN (Highest Response Ratio Next)
 6. FB-1, (Feedback where all queues have q=1)
 7. FB-2i, (Feedback where q= 2i)
 8. Aging
- Line 3: An integer specifying the last instant to be used in your simulation and to be shown on the timeline.
- Line 4: An integer specifying the number of processes to be simulated.
- Line 5: Start of description of processes. Each process is to be described on a separate line. For algorithms 1 through 7, each process is described using a comma-separated list specifying:

    1- String specifying a process name\
    2- Arrival Time\
    3- Service Time

- **Note:** For Aging algorithm (algorithm 8), each process is described using a comma-separated list specifying:

    1- String specifying a process name\
    2- Arrival Time\
    3- Priority
- Processes are assumed to be sorted based on the arrival time. If two processes have the same arrival time, then the one with the lower priority is assumed to arrive first.

> Check the attached [testcases](https://github.com/yousefkotp/CPU-Scheduling-Algorithms/tree/main/testcases) for more details.

