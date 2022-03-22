Update Data
```
echo "\nqux" >> data/foo.txt
```

Because the file is tracked in dvc, it won't show up in git status
```
git status
On branch master
nothing to commit, working tree clean
```

dvc will pick up that there has been a change
```
dvc status
data.dvc:                                                                       
        changed outs:                                                           
		modified:           data
```

Add the data
```
dvc add data
```

git will register a change
```
git status

On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   data.dvc
```

commit this to git repo
```
git add data.dvc
git commit -m "update data.dvc"
git push origin master
```

update the data
note: we must specify the remote because our default remote is the s3 http read only remote
```
dvc push -r s3
```

# In a project which uses the data

A change is shown
```
dvc status
data/ins-dvc-example.dvc:                                                       
        changed deps:                                                           
		update available:   data (git@github.com:insilica/ins-dvc-example)
```

Grab the new data
```
dvc update data/ins-dvc-example.dvc
```
