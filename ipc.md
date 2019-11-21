### if.05.01 TINF Operting Systems

# Assignment 5: Basics of Interprocess Communication

1. **Race Condition**
Describe with your own words: What is a race condition?
happens when two processes access a critical region nearly at the same time and the process that enters last win, that means the last process 
overwrites the data from the process who wrote his data first, e.g. printerqueue

2. **Disabling Interrupts**
   1. Why is it impossible to achieve Mutual Exclusion via disabling interrupts on a multi-core machine?
   disabling interrupts is only for one core valid, that means the other cores are still able to acces same data at the same time and
   maybe cause problem with the Race Conditions
   2. Why is it dangerous to give user processes the power to disable interrupts?
   while disabling interrupts the user could unintentionaly enter a infinite loop causing the machine to stop working 
   
3. **Peterson's Solution**
   1. Play through the two scenarios of the handout of Peterson's solution. Document how it works.
   *Scenario 1:*
  process 0 calls enter_region() sets interested[0] to true and loser = 0. then 0 enters the CR and then process 1 calls enter_region()
  and sets interested[1] to true and loser to 1. Then 1 enters the while and has to wait. Then 0 enter leave_region() and sets   interrested[0]
  to false, and 1 escapes the while and enters the CR.
  *Scenario 2:* 
  
   2. Play through the scenario which makes the strict alternation approach fail. Document how it fails.
   lets say that process 0 has a higher priority then process 1. Process 0 enters enter_region() and sets turn = 1 and then process 1 gets
   to run through the CR and process 0 checks again if turn != 0, but turn is 1. So process checks the while unecessary, because it will 
   never turn to 0 because the scheduler only lets process 0 do things. 
   3. What is the meaning of the variable `loser` in Peterson's solution? When does it have any effect?
   the loser variable defines the process who enters last. only has a effect when the other process is also interested
   4. Extend the given functions such they can handle three processes.
