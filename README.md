# timecard

A simple CLI utility to record timecards, written in Bash.

## Simple example

```bash
# Create 'timecard.txt' in current directory
$ timecard init

# Start your work at office
$ timecard start -c "office"

# Check status
$ timecard status
Pending tasks for 'user':
07/17/19
  17:00:00 (dur: 0h0m30s) office

# Start writing a report at office
$ timecard start -c "report"
$ timecard status
Pending tasks for 'user':
07/17/19
  17:00:00 (dur: 0h1m00s) office
  17:00:30 (dur: 0h0m30s) report

# You finished with the report
$ timecard stop
user worked 00:01:00 for work 'report'
$ timecard status
Pending tasks for 'user':
07/17/19
  17:00:00 (dur: 0h1m30s) office

# You left the office
$ timecard stop
$ timecard status
Pending tasks for 'user':
```

# Function
## Collaboration

You can manage timecard.txt in your project directory.
It enables merging timecards with your team member.
You can specify username with `-u`, if you prefer.

## Show

```bash
$ timecard show
07/17/19
  /- 00:00:00 user 1
  |  /- 16:20:00 user 2
  |  |  /- 16:20:00 user 3
  |  |  \- 16:30:00 (dur: 0h10m1s)
  |  \- 16:30:00 (dur: 0h10m1s)
  \- 16:30:00 (dur: 16h30m1s)
  /- 17:10:00 user abc
  |  /- 17:10:00 user abc
  |  |  /- 17:30:00 user 
  |  |  |  /- 17:30:00 user 
  |  |  |  \- 17:39:59 (dur: 0h10m0s)
  |  |  \- 17:39:59 (dur: 0h10m0s)
  |  \- 18:19:59 (dur: 1h10m0s)
```

## Git link

It can display git log in the output of `timecard show`.
Use `--git=dir[@@branch]` flag or option `%git=dir[@@branch]` in `timecatd.txt`.

## Roundoff

You can specify roundmethod in `timecard.txt` to make the starting or stopping time aligned. Sample:
```
%roundmethod="10 minutes outset"
%roundmethod="5 minutes roundup"
%roundmethod="15 minutes nearest"
```
