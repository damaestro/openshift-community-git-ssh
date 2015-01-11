# GIT\_SSH for Git Hosting Providers

A cartridge to make it easier to build from the following git hosting providers with the OpenShift Jenkins:

* GitHub
* Bitbucket
* Gitlab.com

In short, cartridges may never write to ~/.ssh, so connecting to these hosting providers via ssh will fail with an error about the host key. (Host key verification failed.)

This cartridge provides an executable called `git-ssh` and the `GIT_SSH` environmental variable to point at that executable.

## Known Hosts Implementation

To support connecting to the supported git hosting providers, this cartridge uses `ssh-keyscan` to pre-populate a known\_hosts file to be used for verification during git operations via ssh.

## Keys and Credentials

A new key is automatically generated for use with your git hosting provider when this cartridge is installed. You will be informed of the public key upon installation. It is located at `$OPENSHIFT_DATA_DIR/git-ssh/id_rsa.pub` if needing to be viewed post-install.

You can put a custom SSH key into `$OPENSHIFT_DATA_DIR/git-ssh/id_rsa` and the `git-ssh` command will use it.

Finally, for good measure, this cartridge creates ~/.netrc, in case your Jenkins builds need to store credentials there.

## Supporting SSHFP

Instead of having to pre-populate a known\_hosts file, you can also use SSHFP. See [the sshfp branch](https://github.com/damaestro/openshift-community-git-ssh/tree/sshfp) for SSHFP support and for information about how to request support for SSHFP from these providers. The listed providers currently do not fully support SSHFP.
