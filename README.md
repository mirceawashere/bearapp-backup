# **# bearapp backup**
basically a .sh script for the automatic backup of the  [Bear app](https://bear.app) notes database

**keep in mind**: 
- in my current set-up, I already have a cloud-based backup tool (Dropbox), which automatically backups certain folders on my hard drive. So you’re going to need something similar for this whole thing to work.
- you need to ***give [cron](https://en.wikipedia.org/wiki/Cron) full disk access*** in macOS. in order to do that:

> 1.	Open System Preferences → Privacy & Security → Privacy tab.
> 2.	Scroll to Full Disk Access.
> 3.  Click the + button to add an application or binary.
> 4.  Press Command + Shift + G in the file browser to open the Go to Folder dialog.
> 5.  Enter /usr/sbin and press Enter.
> 6.  Locate and select cron, then click Open to add it to the Full Disk Access list.

## the idea
This idea came up after I read the [documentation](https://bear.app/faq/where-are-bears-notes-located/) of the [Bear app](https://bear.app), where it stated that notes are ***only*** stored on a local macOS database located at: 

`/Library/Group Containers/9K33E3U3T4.net.shinyfrog.bear/Application Data/database.sqlite`

I needed a backup, so I came up with the following solution.

## steps

### 1. make a .sh script to copy the database to your cloud backup folder

adapt/alter the [script](https://github.com/mirceawashere/bearapp-backup/blob/main/script.sh) to suit your system path

### 2. give user execute permissions to the script

```
chmod u+x scriptname.sh
```

### 3. automate the process to make sure that the script runs at 8 PM every day

so I <ins>know</ins> that there are better ways to do this, but I wanted a simple solution using **cron**. 

using your terminal, enter the following:

`crontab -e`

inside of crontab, enter the following command and then save:

```
0 20 * * * /{path-to-script-location}/{scriptname}.sh
```

you can change the scheduler to whatever suits you best (the above is just an example).


#### and voila. that’s it.

-m
