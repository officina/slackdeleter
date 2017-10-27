# SlackDeleter
Python script to delete Slack files that meet a specific age and size criteria.

## Requirements:
* Click
* Requests

Both are pip installable.

# Usage
<pre>
$ python slackdeleter.py --help
Usage: slackdeleter.py [OPTIONS]

Options:
  --token TEXT             Your Slack test token (https://api.slack.com/docs/oauth-test-tokens)
  --days INTEGER           How old a file must be in order to delete it.
  --only_created BOOLEAN   Only delete files you created?
  --sort [size|date|user]  Sort by 'size', 'date' or 'user'.
  --min_kb INTEGER         Minimum number of Kilobytes for file to qualify.
  --quiet                  Deletes automatically the files (no prompt, so be really careful!)
  --help                   Show this message and exit.
  
</pre>

# In Action
<pre>
$ python slackdeleter.py
Slack Test Token: xoxp-SECRET-SECRET-SECRET-SECRET
Age of files to delete. [31]: 2
Only delete files you created? [True]: 
Sort by [size]: 
Minimum filesize to delete (in kilobytes) [1000]: 100

Querying Slack's Servers . 
Files:
  Pasted image at 2016_08_07 10_08 AM.png     139.72 KB   	Firstname Lastname       	3 days ago
  Pasted image at 2016_08_03 12_31 PM.png     119.84 KB   	Firstname Lastname       	6 days ago
  Pasted image at 2016_08_07 10_13 AM.png     101.91 KB   	Firstname Lastname       	3 days ago
  Pasted image at 2016_08_07 10_11 PM.png     101.52 KB   	Firstname Lastname       	2 days ago

4 files match your criteria. (463.00 KB)

Do you want to delete all of these files now? [y/N]: y
Type "YES" to really delete the files listed above: YES

DELETING FILES:
  Deleting Pasted image at 2016_08_07 10_08 AM.png (139.72 KB) ...  Deleted
  Deleting Pasted image at 2016_08_03 12_31 PM.png (119.84 KB) ...  Deleted
  Deleting Pasted image at 2016_08_07 10_13 AM.png (101.91 KB) ...  Deleted
  Deleting Pasted image at 2016_08_07 10_11 PM.png (101.52 KB) ...  Deleted

4 files deleted (463.00 KB)
</pre>

# Quiet Mode:
<pre>
python slackdeleter.py --token xoxp-SECRET-SECRET-SECRET-SECRET --days 31 --min_kb 1000 --only_created FALSE --sort size --quiet TRUE
Querying Slack's Servers . . . . .
Files:
  xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx     72.65 MB    	John Doe          	49 days ago
  xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx     60.28 MB    	Mark Appleseed 		49 days ago
  
9 files match your criteria. (289.06 MB)

  Deleting xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx (72.65 MB) ...  Deleted
  Deleting xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx (60.28 MB) ...  Deleted
  
</pre>
