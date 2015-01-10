# GIT_SSH

A cartridge to make it easier to build from GitHub with the OpenShift Jenkins. BitBucket does not work with this menthod as they do not publish SSHFP records.

In short, cartridges may never write to ~/.ssh, so connecting to GitHub or BitBucket will fail with an error about the host key.

This cartridge provides an executable called `git-ssh` and the `GIT_SSH` environmental variable to point at that executable. 

The script will cause all git operations to SSH command with the `VerifyHostKeyDNS=yes` option set to trust the SSHFP records for GitHub.

## Keys and Credentials

You can put a SSH key into `$OPENSHIFT_DATA_DIR/git-ssh/id_rsa` and the `git-ssh` command will use it.

Finally, for good measure, it will unlock ~/.netrc, in case your Jenkins builds need to store credentials there.
