f you want the data to be public, you need to enable public access to your s3 bucket. That is beyond the scope of this document,
but directions are available here:
https://aws.amazon.com/premiumsupport/knowledge-center/read-access-objects-s3-bucket/

Creating a bucket policy is a good option.

# setting a default remote
By default, when adding a remote it will become the default one used. You must have access rights to it via your AWS credentials.
If you wish to make the data public so that it can be used in other places, you will want to set the bucket used to store the data
to be public and accessed via https. 

**You must make the https endpoint the default remote in order for other other people to use your data**

Continuing from the DVC setup example,

```
dvc remote add s3http https://ins-dvc.s3.amazonaws.com/ins-dvc-example
dvc remote default s3http
git add .dvc/config 
git commit -m "add s3http and change to default"
```

# use in another project

```
dvc import git@github.com:insilica/ins-dvc-example.git data -o data/ins-dvc-example
```
