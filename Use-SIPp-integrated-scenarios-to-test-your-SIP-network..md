## Example 1: Using the default UAC scenario to send calls
```
./sipp -sn uac -d 20000 -s 1001 108.61.211.191  -m 6
```
will generate a maximum of 6 SIP calls to the destination IP address of 108.61.211.191 , each call lasting for 20 seconds. The calls will use the uac scenario and set the From header to 1001.


|      option                      | Description                   |
|:--------------------------------:|:----------------------------|
| -sn                              |Use a default scenario (embedded in the SIPp executable) |
| -d                              |Controls the length of calls. More precisely, this controls the duration of 'pause' instructions in the scenario, if they do not have a 'milliseconds' section. Default value is 0 and default unit is milliseconds|
| -s                             |Set the username part of the request URI. Default is 'service'. |
| -m                              |Stop the test and exit when 'calls' calls are processed |

![](https://github.com/Omid-Mohajerani/siptools/blob/main/SIPP/screenshots/SIPP01.png?raw=true)

***
## Example 2: Using the default UAC scenario to send calls with rate limit
Send 6 Calls (INVITE) to 1001@108.61.211.191 with the rate of 2 concurrent calls **in 10 seconds**  - After the Call answered pause for 20000 ms and Hangup (BYE)

(target will get a call every 5 seconds)

```
./sipp -sn uac -d 20000 -s 1001 108.61.211.191  -m 6 -r 2 -rp 10000
```
|      option                      | Description                   |
|:--------------------------------:|:----------------------------|
| -r                              | Set the call rate (in calls per seconds).  | 
| -rp                              |: Specify the rate period for the call rate.  Default is 1 second and default unit is milliseconds.  This allows you to have n calls every m milliseconds (by using -r n -rp m). Example: -r 7 -rp 2000 ==> 7 calls every 2 seconds.  -r 10 -rp 5s => 10 calls every 5 seconds. |

![](https://github.com/Omid-Mohajerani/siptools/blob/main/SIPP/screenshots/SIPP02.png?raw=true)

***
## Example 3: Enabling logs 

```
./sipp -sn uac -d 20000 -s 1001 108.61.211.191  -m 6 -trace_msg -trace_shortmsg -trace_err -trace_screen
```
|      option                             | Description                   |
|:---------------------------------------:|:----------------------------|
| trace_msg                             | Displays sent and received SIP messages in <scenario filename>_<pid>_messages.log | 
|trace_shortmsg                        | Displays sent and received SIP messages as CSV in <scenario filename>_<pid>_shortmessages.log|
| trace_err                             | Trace all unexpected messages in <scenario file name>_<pid>_errors.log. | 
| trace_screen                          | Dump statistic screens in the <scenario_name>_<pid>_screens.log file when quitting SIPp. Useful to get a final status report in background mode|


                      
                        
