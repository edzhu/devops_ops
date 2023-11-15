# `ops` Envornment Configuration for `devops` Repo

All data under **secret** directory is encrypted using [git-crypt](https://www.agwa.name/projects/git-crypt/).

## How to Encrypt Repository

0. Install git-crypt: `sudo apt install git-crypt` or `brew install git-crypt`
1. Enable git-crypt for this repo: `git-crypt init`
2. Create directory to hold encrypted files: `mkdir secret`
3. Create .gitattributes to enable encryption:
   * `echo '* filter=git-crypt diff=git-crypt' > secret/.gitattributes`
   * `echo '.gitattributes !filter !diff' >> secret/.gitattributes`
4. Export symmetric key: `git-crypt export-key /path/to/keyfile`
5. Add files into _secret_ directory and content will be automatically encrypted on push.

## How to Decrypt Repository

0. Install git-crypt: `sudo apt install git-crypt` or `brew install git-crypt`
1. Obtain shared secret key file.
2. `cd /path/to/repo`
3. `git-crypt unlock /path/to/key`
4. Use as usual, files will be automatically encrypted when pushing to remote repository
