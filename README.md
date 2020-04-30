## "# Multithreading-VS-Multitasking" 
#  Multi-threading:  
Multithreading is the ability of a central processing unit (CPU) (a single core in a multiprocessor) to provide multiple threads of execution concurrently, supported by the operating system. Multithreading lets the CPU execute multiple threads of a process simultaneously.  
Before studying multithreading let us talk about what is thread? A thread is a basic execution unit which has its own program counter, set of the register, stack but it shares code, data, file of the process to which it belongs.  
•	Multithreading increases the responsiveness of the system as, if one thread of the application is not responding, the other would respond in that sense the user would not have to sit idle.  
•	Creating a different process is costlier as the system has to allocate different memory and resources to each process, but creating threads is easy as it does not require allocating separate memory and resources for threads of the same process.  
 
## Let’s do some code :  


    use std::thread;
    use std::time::Duration;
     fn new(){
        let thread_one = thread::spawn(|| {
            thread::sleep(Duration::from_millis(200));
            println!("Thread 1");
        });
        
        let thread_two = thread::spawn( || {
            println!("Thread 2");
        });
    thread_one.join().expect("Thread one panicked");
    thread_two.join().expect("Thread two panicked");
    }
    fn main() {
        new();
    }

 
  In this code we have used two threads in which at thread_one   we used a time duration of 200 milliseconds as in thread_two   we haven’t given any time duration.  
  Due to the no time duration the result will print Thread 2 and then it will print Thread 1 because as we discussed above that multithreading will run both the threads simultaneously.  
# MultiTasking:  
As the name itself suggests, multitasking refers to execution of multiple tasks (processes, programs, threads etc.) at a time.  
•	In the modern operating system, we are able to play MP3 music, edit documents in Microsoft Word, programming in VS Code, surf Google Chrome all simultaneously, this is accomplished by means of multitasking.  
In a time sharing system, each process is assigned some specific quantum of time for which a process is meant to execute. Say there are 4 processes P1, P2, P3, P4 ready to execute. So each of them are assigned some time quantum for which they will execute e.g time quantum of 5 nanoseconds (5 ns). As one process begins execution (say P2), it executes for that quantum of time (5 ns). After 5 ns the CPU starts the execution of the other process (say P3) for the specified quantum of time.  

## Let check by an example:
        use std::thread;
        use std::task;
        use std::time::Duration;
        fn new(){
            let task_1 = {
                thread::sleep(Duration::from_millis(2000));
                println!("Task 1" )};
            let task_2 = {
                println!("Task 2" )};
        }

        fn main(){
            new();
        }


So now this is the same example like previous example. There is two tasks instead of threads. As we described above that in multitasking there are execution of multiple tasks. So now what would be the result?
The result is it will print Task 1 Then Task 2 because it will wait for first task to complete then it will execute other .

## ThankYou!


