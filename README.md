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

TO DO
 - priority donation
 - sync
