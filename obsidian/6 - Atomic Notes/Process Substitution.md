
#### [Piping](https://tldp.org/LDP/abs/html/special-chars.html#PIPEREF) the *stdout* of a command into the *stdin* of another is a powerful technique. But, what if you need to pipe the stdout of _multiple_ commands? This is where _process substitution_ comes in.

#### _Process substitution_ feeds the output of a [process](https://tldp.org/LDP/abs/html/special-chars.html#PROCESSREF) (or processes) into the stdin of another process.

#### In lamest terms, process substitution allows you to turn a command into a temporary file that banishes after it finishes.

```
cat <(echo hey there) # this outputs: hey there 
echo <(echo hey there) # this outputs: /dev/fd/63
```

The first command converts the output of the command `echo hey there` into a file with the contents `hey there`

The second command echoes the name of the temporary file being used.

```
Template

Command list enclosed within parentheses:
>(command_list)
<(command_list)

Process substitution uses /dev/fd/<n> files to send the results of the process(es) within parentheses to another process. 
There is no space between the the "<" or ">" and the parentheses. Space there would give an error message.
```

```

Q) Create files system_0.log to system_99.log & system_1.out to sytem_100.out
Follow up: how you verify that each .log file have respective .out file
Follow up: how can we optimize the verification part, and make it one liner.

Solution:

touch system_{0..99}.log system_{1..100}.out

ls *.log | cut -d. -f1 > system_log
ls *.out | cut -d. -f1 > system_out

diff -u system_log system_out

diff -u <(ls *.log | cut -d. -f1) <(ls *.out |cut -d. -f1)

```


Tags: [[linux]] [[bash]]  

Reference:
<iframe src="https://tldp.org/LDP/abs/html/process-sub.html" allow="fullscreen" allowfullscreen="" style="height:100%;width:100%; aspect-ratio: 16 / 9; "></iframe>

