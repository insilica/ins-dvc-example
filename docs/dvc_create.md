# Create a new DVC data source

dvc relies on git, so
```
git init
```

then

```
dvc init
```

dvc will auto add the files it needs tracked
```
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   .dvc/.gitignore
	new file:   .dvc/config
	new file:   .dvcignore
```
commit this

```
git commit -m "initial dvc commit"
```

create some data
```
mkdir data ; echo "foo\nbar\nbaz" > data/foo.txt ; echo "alpha\nbravo\ncharlie" > data/alpha.txt
```

add the data
```
dvc add data
```
add a git remote
```
git remote add origin git@github.com:jborden/r-dsv-test.git
```

add a dvc remote

```
dvc remote add -d s3 s3://ins-dvc/r-dsv-test
```


commit the changes in git
```
git add .gitignore
git add data.dvc
git commit -m "added data dir"
```

push the commit
```
git push origin master
```

push the data

```
dvc push
```


