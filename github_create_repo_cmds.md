#this is a markdown file guiding you through the very first steps to create and manage a git repo with github
##lets start on your bash shell
##crete a directory

![Alt text](lab1_imgs/Screen Shot 2015-09-02 at 1.17.55 AM.png)

```
mkdir gittest_fbianco
```

##get in the directory to start working

```
cd gittest_fbianco/
```

## the following command initiates a LOCAL git repository: files can be tracked on your own machine from now on.

```
git init
git status
```

##create a first file. this commands creates an empty file with the name you pass as argument

```
touch myfirstfile.txt
```

##see if it got created ok

```
ls -l
git status
```

##your git repo knows nothing about it yet: you need to add it to the repo for it to be tracked

```
git add myfirstfile.txt 
git status
```

##can we commit it to github to have it in the cloud?

```
git commit myfirstfile.txt -m 'trying to commit'
git push
```

##why did you get an error message?? because you have not told this repo where in the cloud to look for its remote version

#first go online and create a repository. 
![Alt text](lab1_imgs/Screen\ Shot\ 2015-09-02\ at\ 1.53.34\ AM.png)

![Alt text](lab1_imgs/Screen Shot 2015-09-02 at 2.04.06 AM.png)

![Alt text](lab1_imgs/Screen Shot 2015-09-02 at 2.04.21 AM.png)

##then follow the directions in the image above (use the appropriate URL in the command below)

```
git remote add origin  https://github.com/fedhere/gittest_fbianco.git
git push -u origin master 
```

##the following command shows you what URL you push and pull from (need not be the same generally)

```
git remote -v 
git status
```

##lets make local changes to the file...

```
echo "whatever" >> myfirstfile.txt 
git status
```

##...and commit them

```
git commit myfirstfile.txt -m 'commit changes'
```

##and send them to the cloud

```
git push 
```

##now go online to your new github repo, and make changes directly to the online version of the file online

![Alt text](lab1_imgs/Screen Shot 2015-09-02 at 2.11.31 AM.png)

![Alt text](lab1_imgs/Screen Shot 2015-09-02 at 2.14.17 AM.png)

##and make some local changes as well on your machine

```
echo  "this is gonna go wrong..." >> myfirstfile.txt 
git commit myfirstfile.txt -m 'commit changes without pulling first'
git push
```

##congratulations: you got your first merge conflict! to fix it pull the changes over first

```
git pull
```

##edit the file removing the lines starting with \>\>, \<\<, and ==, and decide what you want the file to look like to solve the conflict

```
emacs myfirstfile.txt 
```
![Alt text](lab1_imgs/Screen Shot 2015-09-02 at 2.22.03 AM.png)

#...

##now add the file again and commit. NOTE: the commit has to be global. i.e. you cannot use git commit myfirstfile.txt and commit only that right now: you have to commit everything.

```
git add myfirstfile.txt 
git commit 
```

##NOTE: you could also have stashed (thrown away) your changes when you got the error message

```
git stash
```

#now let's mess with someone else's repo! the lady or gentelman to your left will do.
##go online and fork your neighbor's repo

##then clone it: the URL was given to you online on your fork page 

![Alt text](lab1_imgs/Screen Shot 2015-09-02 at 2.29.58 AM.png)

```
cd ../
git clone https://github.com/fedhere/gittest_<the neighor on your left>.git
ls -ltr
cd gittest_<the neighor on your left>
ls
```

##mess with it

```
echo "Hello there, this is Dr Bianco messing with your file" >> myfirstfile.txt 
git commit myfirstfile.txt  -m "messing with my neighbor's repo"
git push
```

##go online to your fork, check the changes, request a merge

![Alt text](lab1_imgs/Screen Shot 2015-09-02 at 1.21.46 AM.png)


#back to your own repo...
##check your email: you will find the merge request from your new friend!
##let's get back to our own repo online and look for pull requests. let's accept this request!

![Alt text](lab1_imgs/Screen Shot 2015-09-02 at 1.34.13 AM.png)
![Alt text](lab1_imgs/Screen Shot 2015-09-02 at 1.35.43 AM.png)


```
cd -
cd gittest_fbianco/
git status
git pull
less myfirstfile.txt 
git log
```
#now don't forget to pull the file before you make more changes or you may get another conflict. However note that if you change _a different line_ than the one your friend changed, the merge may work: github will pull the line you changed from your version and the line your friend changed from his. give it a try on your own!

```
