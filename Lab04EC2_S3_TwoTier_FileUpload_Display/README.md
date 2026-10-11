Why the uploader and viewer use separate IAM roles?

I would say that the reason that the uploader and viewer both use separate IAM roles is because they do different jobs and should only have the permissions they actually need. The uploader should only need permission to put shared.txt into the S3 bucket, whilst the viewer only needs permission to read that file and list the bucket. If you were to give both instances one shared role with every permission would give each instance access it does not need. With using separate roles, that helps follow the principle of least privilege and also limits what could be accessed if one of the instances was compromised.

Why the instance does not need Git or S3 credentials to get its code

The reason that embedding the code directly into the User Data means that the instance does not need Git or S3 credentials is because the application code is already included when the instance starts up. Since the files are already being given to the instance through the Launch Template, it does not need to connect to GitHub or S3 to download its own code.
