2025/07/16

thread.c
 - added function : bool compare_waketime() , int64_t min_waketime()
 - bool compare_waketime() : used in list_insert_ordered() as a LESS function; called in add_to_sleep_list()
 - min_waketime() : function returns the minimum wake_time of thread in sleep list
    used at timer_interrupt() as a condition to call wakeup_thread()
 - edit add_to_sleep() : now sleep list is sorted by wake_time ascending order
 - edit wakeup_thread() : during loop through sleep list, if current tick is smaller than thread's wake_time, return; else remove the thread from sleep list; 

timer.c  
 - timer_interrupt() : add condition to call wakeup_thread; call when (current tick) >= (minimum wake_time) AND sleep_list isn't empty (min_waketime() != 0)

2025/07/21

timer.c
  - timer_sleep(ticks) : add if clause to check whether ticks <= 0, return without sleeping the thread if it is

2025/08/08
lock release에서 priority가 클 경우 현재 thread를 yeild 하는 로직 추가


TO DO
 - priority donation
   priority is donated when a thread fails to acquire the lock
   check the donated thread's condition for possible nested or multiple locks

 - Advanced scheduler
   * No priority donation
   * Scheduling algorithm should be set at Pintos start time
   * priority argument to thread_create() should be ignored, as well as any
     calls to thread_set_priority(), and thread_get_priority() should return the thread’s current priority as set by the scheduler

