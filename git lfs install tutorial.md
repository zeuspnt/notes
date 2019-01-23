Run this script

```bash
curl -s https://packagecloud.io/install/repositories/github/git-lfs/script.rpm.sh | sudo bash
```

ubuntu:

```bash
sudo apt-get install git-lfs
```

macOS:

```bash
brew install git-lfs
```

Then, cd into repository folder and run this command

```bash
git lfs install
```

Track the large file.

```bash
git lfs track <path_to_file>
```

Commit and push file.

```bash
git commit <...>
git push <...>
```
