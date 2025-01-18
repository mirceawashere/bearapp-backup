# **# bearapp backup**
basically a .sh script for the automatic backup of the  [Bear app](https://bear.app) notes database

**requierments**: in my current set-up, I already have a cloud-based backup tool (Dropbox), which automatically backups certain folders on my hard drive. So you’re going to need something similar for this whole thing to work.

## the idea
This idea came up after I read the [documentation](https://bear.app/faq/where-are-bears-notes-located/) of the [Bear app](https://bear.app), where it stated that notes are ***only*** stored on a local macOS database located at: 

`/Library/Group Containers/9K33E3U3T4.net.shinyfrog.bear/Application Data/database.sqlite`

I needed a backup, so I came up with the following solution.

## steps

### 1. make a .sh script to copy the database to your cloud backup folder

the script should be as follows:

```
cp /Users/{username}/Library/Group\ Containers/9K33E3U3T4.net.shinyfrog.bear/Application\ Data/database.sqlite /Users/{username}/{path-to-cloud-folder}

```

### 2. automate the process to make sure that the script runs at 8 PM every day

so I <ins>know</ins> that there are better ways to do this, but I wanted a simple solution using **cron**. 

using your terminal, enter the following:

`crontab -e`

inside of crontab, enter the following command and then save:

```
0 20 * * * /{path-to-script-location}/{scriptname}.sh
```

you can change the scheduler to whatever suits you best (the above is just an example).

and voila. that’s it.
