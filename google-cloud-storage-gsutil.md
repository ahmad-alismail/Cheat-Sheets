# Gsutil cheatsheet
`gsutil` is Google Storage CLI tool. Equivalent to `aws s3` but for the Google Cloud Platform, it allows you to access Google Cloud Storage from the command line. Beyond moving files and managing buckets, gsutil is a powerful file management (rsync) and file publication tool (signed urls).

Please find below a shortlist of the most important and frequent commands and their relative syntax.

This is a work in progress that will be updated within the next few days.



## Definitions
GCP: Google Cloud Platform
## Before you begin
* Make sure that billing is enabled for your Cloud project. Check out this [link](https://cloud.google.com/storage/docs/discover-object-storage-gsutil?cloudshell=true) for more information.
* To set your Cloud Platform project in terminal use: `gcloud confg set project [PROJECT_ID]`
* or create a Google Cloud project: `gcloud projects create [PROJECT_ID]`
## General Commands

`gsutil ls`: lists all your buckets
`gsutil help <topic>`: help on the topic

## Buckets
`gsutil mb -b on -l us-east1 gs://my-awesome-bucket/`: create a bucket

`gsutil mb gs://<bucket_name>`: creates the gs://bucket_name1.

`gsutil rm -r gs://my-awesome-bucket`: deletes the bucket.


## Files
`gsutil cp <filename> gs://<bucket_name>/`: copies the local filename into the bucket ****.

`gsutil cp <filename> gs://<bucket_name>/directory/`: copies the local filename into the directory ****2.

`gsutil mv <src_filename> gs://<bucket_name>/directory/<tgt_filename>`: moves the local src_filename to the directory and renames it as tgt_filename

`gsutil rm gs://<bucket_name>/file_or_dir`: deletes the file_or_dir object.

## Folder
`gsutil cp <filename> gs://<bucket_name>/`: copies the local filename into the bucket ****.

## Permission
`gsutil iam ch allUsers:objectViewer gs://my-awesome-bucket`: grant all users permission to read the files stored in your bucket

`gsutil iam ch -d allUsers:objectViewer gs://my-awesome-bucket`: remove this access

`gsutil iam ch user:jane@gmail.com:objectCreator,objectViewer gs://my-awesome-bucket`: give someone access to your bucket

`gsutil iam ch -d user:jane@gmail.com:objectCreator,objectViewer gs://my-awesome-bucket`: remove this permission


## Footnotes
1. The bucket name has to be unique across GCP.
2. Note the trailing ‘/’ slash after < directory > to tell gsutil that the target is a directory and not a file

[Reference page](https://cloud.google.com/storage/docs/gsutil/commands/acl) for `gsutil` Commands
