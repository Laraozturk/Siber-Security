# ***WHAT IS CRONTAB AND HOW TO USE IT?***
# **1.What is Crontab?**
It is a Unix command that creates a script of tasks that will be repeated at a given time.
# **2.How to use?**
┌───────────── minute (0 – 59)
│ ┌───────────── hour (0 – 23)
│ │ ┌───────────── calendar day (1 – 31)
│ │ │ ┌───────────── month (1 – 12)
│ │ │ │ ┌───────────── day (0 – 6) (0=Sunday, 1=Monday … 6=Saturday
│ │ │ │ │                                            and also only on Sunday 7=Sunday)
│ │ │ │ │
│ │ │ │ │
*  *  *  * *  Command directory to be run
# **Crontab Usage Example**
The code that will run the example2.sh script every hour is as follows.
'''
0 * * * * /home/kali/yedek/ornek2.sh
'''
