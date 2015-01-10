# GIT_SSH for GitHub Using SSHFP Records

A cartridge to make it easier to build from GitHub with the OpenShift Jenkins. **Bitbucket does not work with this menthod as they do not publish SSHFP records yet.**

In short, cartridges may never write to ~/.ssh, so connecting to GitHub or Bitbucket will fail with an error about the host key.

This cartridge provides an executable called `git-ssh` and the `GIT_SSH` environmental variable to point at that executable. 

The script will cause all git operations to run with the `VerifyHostKeyDNS=yes` option set to trust the SSHFP records published in DNS. GitHub has [published](https://help.github.com/articles/what-are-github-s-ssh-key-fingerprints/) their keys via SSHFP records. If you would like this cartridge to support Bitbucket, please [open a ticket with Atlassian](https://bitbucket.org/support) and request they add the SSHFP records.

## Keys and Credentials

A new key is automatically generated for use with GitHub when this cartridge is installed. You will be informed of the public key upon installation. It is located at `$OPENSHIFT_DATA_DIR/git-ssh/id_rsa.pub` if needing to be viewed post-install.

You can put a custom SSH key into `$OPENSHIFT_DATA_DIR/git-ssh/id_rsa` and the `git-ssh` command will use it.

Finally, for good measure, this cartridge creates ~/.netrc, in case your Jenkins builds need to store credentials there.
