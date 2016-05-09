This article will introduce about publishing your data to FTP server thought git.
So,

**ABOUT THE SCOPE**

This blog will talk about: 
+ FTP Server
+ GIT versioning
+ Publishing work-flow
+ GIT-FTP library



**Why git-ftp**

+ I want to track my data-uploading (Which, Where, When, Who upload these files to my FTP server).
+ It's able to rollback to previous version if there is a mistake.
+ I don't want to use Database, because It's so complex & I don't want to configuration any database-server. 

**HOW**
+ Prepare : `git repository`, `ftp server`, 
+ Library to use : git-ftp(https://github.com/git-ftp/git-ftp)

+ Installtion instruction: https://github.com/git-ftp/git-ftp/blob/develop/INSTALL.md

+ Use guide: 

````
# Setup
git config git-ftp.url ftp.example.net
git config git-ftp.user ftp-user
git config git-ftp.password secr3t

# Upload all files
git ftp init

# Or if the files are already there
git ftp catchup

# Work and deploy
echo "new content" >> index.txt
git commit index.txt -m "Add new content"
git ftp push
# 1 file to sync:
# [1 of 1] Buffered for upload 'index.txt'.
# Uploading ...
# Last deployment changed to ded01b27e5c785fb251150805308d3d0f8117387
````
**NOTE**

1.  If you are using msysgit. After push your file to FTP server & your file/directory name is prefixed with a `#` symbol then try to update to newest version of msysgit.
