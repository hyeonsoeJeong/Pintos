2025/07/16

thread.c
 - added function : bool compare_waketime() , int64_t min_waketime()
 - bool compare_waketime() : used in list_insert_ordered() as a LESS function; called in add_to_sleep_list()
 - min_waketime() : function returns the minimum wake_time of thread in sleep list
    used at timer_interrupt() as a condition to call wakeup_thread()
 - adjust add_to_sleep() : now sleep list is sorted by wake_time ascending order

timer.c 
 
 - timer_interrupt() : add condition to call wakeup_thread; call when (current tick) >= (minimum wake_time) AND sleep_list isn't empty (min_waketime() != 0)

TO DO
 - 변경한 ordered sleep_list에 맞춰 wakeup_thread() 변경 : 앞에서부터 확인해가며 current tick이 wake_time 보다 작아지면 return
