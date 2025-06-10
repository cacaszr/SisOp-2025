# scheduling-algorithms

nama : salsabilla zahratul ramadhani
nrp : 3124521013
Kelas : IT A

## 1.SJF without arrival time (non-preemptive)

### kode program :
![Gambar teks editor VS Code](jsf1.jpg)

#include<stdio.h>
struct proc
{
    int no,bt,ct,tat,wt;
};
struct proc read(int i)
{
    struct proc p;
    printf("\nProcess No: %d\n",i);
    p.no=i;
    printf("Enter Burst Time: ");
    scanf("%d",&p.bt);
    return p;
}
int main()
{
    struct proc p[10],tmp;
    float avgtat=0,avgwt=0;
    int n,ct=0;
    printf("<--SJF Scheduling Algorithm Without Arrival Time (Non-Preemptive)-->\n");
    printf("Enter Number of Processes: ");
    scanf("%d",&n);
    for(int i=0;i<n;i++)
        p[i]=read(i+1);
    for(int i=0;i<n-1;i++)
        for(int j=0;j<n-i-1;j++)    
            if(p[j].bt>p[j+1].bt)
            {
				tmp=p[j];
				p[j]=p[j+1];
				p[j+1]=tmp;
            }
    printf("\nProcessNo\tBT\tCT\tTAT\tWT\tRT\n");
    for(int i=0;i<n;i++)
    {
        ct+=p[i].bt;
		p[i].ct=p[i].tat=ct;
		avgtat+=p[i].tat;
        p[i].wt=p[i].tat-p[i].bt;
        avgwt+=p[i].wt;
        printf("P%d\t\t%d\t%d\t%d\t%d\t%d\n",p[i].no,p[i].bt,p[i].ct,p[i].tat,p[i].wt,p[i].wt);
    }
    avgtat/=n,avgwt/=n;
    printf("\nAverage TurnAroundTime=%f\nAverage WaitingTime=%f",avgtat,avgwt);
}


### output :
![Gambar teks editor VS Code](output1.jpg)

analisa : This C program simulates the Shortest Job First (SJF) scheduling algorithm in a non-preemptive manner, assuming all processes arrive at time zero. It begins by defining a proc structure to hold process details such as number, burst time, completion time, turn-around time, and waiting time. The read function is responsible for interactively taking the burst time input for each process. In the main function, after obtaining the total number of processes, the program reads the burst time for each. Crucially, it then implements a bubble sort algorithm to arrange the processes in ascending order based on their burst times. Following this sorting, the program iterates through the sorted processes to calculate their completion time, turn-around time (which equals completion time as arrival time is 0), and waiting time. Finally, it prints a table summarizing these metrics for each process and calculates and displays the average turn-around time and average waiting time for all processes.

## 2.SJF with arrival time (non-prremptive)

### kode program :
![Gambar teks editor VS Code](sjf1.jpg)
![Gambar teks editor VS Code](sjf2.jpg)

### output :
![Gambar teks editor VS Code](output2.jpg)

analisa : This C program simulates the non-preemptive Shortest Job First (SJF) scheduling algorithm, explicitly incorporating process arrival times to determine the execution order. It begins by defining a proc structure to hold details for each process, including its number, arrival time, burst time, initial start time, completion time, turn-around time, and waiting time. After gathering the number of processes and their individual arrival and burst times from the user, the program initially sorts all processes based on their arrival times. Subsequently, it ensures that among processes arriving simultaneously at the earliest time, the one with the shortest burst time is scheduled first. The core scheduling loop then iteratively selects the shortest job from the set of processes that have already arrived by the completion time of the previously executed process. For each selected process, its initial execution time is calculated, accounting for any potential CPU idle time if the process arrives after the previous one finishes. Following this, the program calculates the completion time, turn-around time (completion time minus arrival time), and waiting time (turn-around time minus burst time) for every process. Finally, it presents a comprehensive table summarizing these metrics for all processes and computes the overall average turn-around time and average waiting time, providing a complete simulation of the non-preemptive SJF algorithm with dynamic arrival times.

## 3.STRF (preemptive) contoh kasus sesuaikan dengan PPT

### kode program :
![Gambar teks editor VS Code](srtf1.jpg)
![Gambar teks editor VS Code](srtf2.jpg)

### output :
![Gambar teks editor VS Code](output3.jpg)

analisa : This C program meticulously simulates the Shortest Remaining Time First (SRTF) scheduling algorithm, which is a preemptive variant of Shortest Job First, by explicitly incorporating process arrival times. The program defines a proc structure to store each process's number, arrival time, total burst time, remaining burst time, completion time, turn-around time, and waiting time, initializing the remaining time with the burst time. After gathering the number of processes and their respective arrival and burst times from the user, the processes are initially sorted based on their arrival times. The core of the SRTF logic is implemented in a time-driven loop that simulates CPU execution. In each time unit, the program dynamically identifies the process that has arrived and currently possesses the shortest remaining burst time among all available processes. This selected process is then allowed to execute for one time unit, decrementing its remaining burst time. This continuous re-evaluation and selection mechanism inherently implements preemption, allowing the CPU to switch to a newly arrived or currently available process if its remaining time is shorter than the currently running one. When a process finishes execution (its remaining time becomes zero), its completion time is recorded, and its turn-around time and waiting time are calculated and accumulated for overall averages. Finally, the program outputs a detailed table displaying these metrics for each process and presents the calculated average turn-around time and average waiting time for the entire set of processes.





