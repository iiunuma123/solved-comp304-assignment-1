Download Link: https://assignmentchef.com/product/solved-comp304-assignment-1
<br>



<h1>Problem 1</h1>

(5×3 points) In Unix/Linux, new processes are created using the <strong>fork() </strong>system call. Calling <strong>fork() </strong>creates a copy of the current process (in which <strong>fork() </strong>is called) and the new process starts executing immediately. After the <strong>fork() </strong>call, both parent and child process start executing the same code.s

<ul>

 <li><strong>Part (a) </strong>Write a C program, which calls <strong>fork() </strong>4 times consecutively. Then each of the forked processes prints its ID, its parents ID and its level in the process tree (The level of the main process is 0). Sample output for 3 forks is shown in Figure 1.</li>

</ul>

Base Process ID: 30511, level: 0

Process ID: 30512, Parent ID: 30511, level: 1

Process ID: 30513, Parent ID: 30511, level: 1

Process ID: 30514, Parent ID: 30511, level: 1

Process ID: 30515, Parent ID: 30512, level: 2

Process ID: 30517, Parent ID: 30512, level: 2

Process ID: 30516, Parent ID: 30513, level: 2 Process ID: 30518, Parent ID: 30515, level: 3

Figure 1

<ul>

 <li><strong>Part (b) </strong>As mentioned previously, the child process is the copy of the parent process when created with <strong>fork() </strong>system call. However, it is possible to replace the contents of the child process with a new process. This is made possible through <strong>exec() </strong>family of system calls. Write a C program that forks a child process which executes <strong>ps f </strong> The <strong>ps f </strong>command will display a process tree. While the child process executes the command, the parent should wait for the child to finish. When the child finishes, the parent should print a message <em>Child finished execution</em>.</li>

 <li><strong>Part (c) </strong>Write a C program that forks a child process that immediately becomes a zombie process. This zombie process must remain in the system for at least 5 seconds.</li>

</ul>

1

<em>PROBLEM 2</em>

A zombie process is created when a process terminates but its parent does not invoke <strong>wait() </strong>immediately. By not invoking wait(), the child maintains its <strong>PID </strong>and an entry in the process entry table.

<ul>

 <li>Use the <strong>sleep() </strong>system call API for the time requirement.</li>

 <li>Run the program in the background (using the <strong>&amp; </strong>parameter) and then run the command <strong>ps -l </strong>to determine whether the child is a zombie process.</li>

 <li>The process states are shown below the S column; processes with a state of Z are zombies in the ps command output.</li>

 <li>The process identifier (PID) of the child process is listed in the PID column, and that of the parent is listed in the PPID column.</li>

 <li>You dont want to create too many zombies. If you need, you can kill the parent process with <strong>kill -9 PID</strong>.</li>

 <li>Provide the source code (only .c) and the screenshots of the ps commands.</li>

</ul>

<h1>Problem 2</h1>

(10 points) Write a C program on Unix/Linux that creates two children processes. Your program will do the following

<ul>

 <li>The parent process (A) creates one child process (B).</li>

 <li>The parent process A sends the current time to this child process B by using ordinary pipes.</li>

 <li>The child process B prints the time after receiving it and then the child process B sleeps for 3 secs.</li>

 <li>Then the child process B creates another process C and sends the current time to this child process C using ordinary pipes.</li>

 <li>The child process C prints the time after it receives it.</li>

 <li>The child process C sleeps for 3 secs and then sends the current time to its parent process B using ordinary pipes.</li>

 <li>When the parent process B receives the message, prints the received time.</li>

 <li>The child process B sleeps for 3 secs and then sends the current time to its parent process A using ordinary pipes.</li>

 <li>When the parent process A receives the message, prints the received time.</li>

 <li>The parent B terminates the child process C.</li>

 <li>After that, the parent A terminates the child process B.</li>

</ul>

<em>PROBLEM 3</em>

<ul>

 <li>Then the parent terminates.</li>

</ul>

You may use <strong>sleep(), kill(), gettimeofday() </strong>system call APIs in your assignment. You are required to submit your .c source code file and a snapshot of a sample run on your terminal. You may refer to the ordinary pipe example in the textbook.

<h1>Problem 3</h1>

(10+15 points) In this question, you will learn how to create a kernel module and load it into the Linux kernel. Note that you need to be a superuser on the computer for this assignment.

<ol>

 <li>Read Linux Kernel Modules under the Programming Projects from the book in Chapter2 (Page 96). Perform Part I and Part II of the assignment. You can arbitrarily set the day, month, year variables. Use the make file and template program we have provided as a starting point.</li>

 <li>Design a separate kernel module that outputs the following characteristics of the processes:

  <ul>

   <li>PID (process ID) • its parent’s ID</li>

   <li>executable name,</li>

   <li>its sibling list (their process ids and executable names),</li>

  </ul></li>

</ol>

You need to read through the task struct structure in <em>&lt; linux/sched.h &gt; </em>to obtain necessary information about a process. The kernel module should take an PID as an argument. If no process ID is provided or the process ID is invalid, print an error message to kernel log.

<strong>Some Useful References:</strong>

<ul>

 <li>Info about task link list (scroll down to Process Family Tree):</li>

</ul>

http://www.informit.com/articles/article.aspx?p=368650 – Linux Cross Reference:

https://github.com/torvalds/linux/blob/master/include/linux/sched.h

<ul>

 <li>You can use the <strong>pstree </strong>command to check if the sibling list is correct. Use -p to list the processes with their PIDs.</li>

 <li>Refer this website on how to pass arguments to a kernel module:</li>

</ul>

http://www.tldp.org/LDP/lkmpg/2.6/html/x323.html