# GIT_SSH Using SSHFP

A cartridge to make it easier to build from git with the OpenShift Jenkins. **This method will only work if the git host you are connecting to has published SSHFP records and is using DNSSEC.**

In short, cartridges may never write to ~/.ssh, so connecting to a git repo via ssh will fail with an error about the host key. (Host key verification failed.)

This cartridge provides an executable called `git-ssh` and the `GIT_SSH` environmental variable to point at that executable. 

The script will cause all git operations to run with the `VerifyHostKeyDNS=yes` option set to trust the SSHFP records published in DNS.

If you would like this cartridge to support GitHub, please [open a ticket with GitHub](https://github.com/contact) and request they add DNSSEC to their zone.

If you would like this cartridge to support Bitbucket, please [open a ticket with Atlassian](https://bitbucket.org/support) and request they add the SSHFP records and add DNSSEC to their zone.

If you would like this cartridge to support Gitlab.com, please [open a ticket with Gitlab](https://gitlab.com/gitlab-com/support-forum/issues) and request they add the SSHFP records and add DNSSEC to their zone. (If you are a paying customer, use the support email address you were given.)

## Keys and Credentials

A new key is automatically generated for use with your repo when this cartridge is installed. You will be informed of the public key upon installation. It is located at `$OPENSHIFT_DATA_DIR/git-ssh/id_rsa.pub` if needing to be viewed post-install.

You can put a custom SSH key into `$OPENSHIFT_DATA_DIR/git-ssh/id_rsa` and the `git-ssh` command will use it.

Finally, for good measure, this cartridge creates ~/.netrc, in case your Jenkins builds need to store credentials there.
