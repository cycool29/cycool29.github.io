---
layout: post
title: Storing Large Files on GitHub with Git LFS
description: Git LFS is a fantastic solution that enables developers to manage and store large files efficiently within their GitHub repositories.
author: cycool29
date: 2023-8-11 21:50 +08:00
permalink: /post/000006.html
tags: git-lfs github large-file git
read-time: 5
medium-link: https://medium.com/@cycool29/storing-large-files-on-github-with-git-lfs-b1f8a43e1d0
dev-link: https://dev.to/cycool29/storing-large-files-on-github-with-git-lfs-2d31
---

---

## Table of Contents

- [Understanding the Challenge](#understanding-the-challenge)
- [Introducing Git LFS](#introducing-git-lfs)
- [Installation](#installation)
- [Set-up Git LFS](#set-up-git-lfs)
- [How it Works?](#how-it-works)

---



GitHub has become the go-to platform for collaborative software development, allowing developers to work together seamlessly on projects of all sizes. However, when it comes to version control for projects that involve large files, the standard Git repository can fall short due to its limitations. This is where Git LFS (Large File Storage) comes into play. Git LFS is a fantastic solution that enables developers to manage and store large files efficiently within their GitHub repositories, without compromising on performance or slowing down the development process.

<h2><span id="understanding-the-challenge">Understanding the Challenge</span></h2>

Git, the distributed version control system that powers GitHub, was primarily designed to manage text-based source code files. While it excels at tracking changes in code, it struggles with large binary files like images, videos, audio files, and other non-text assets. Attempting to store large files directly in a Git repository can lead to several issues:

- Large files can slow down cloning, pushing, and pulling operations, making collaboration and development inefficient.

- Storing large files in a Git repository can quickly bloat its size, making it difficult to clone and maintain, especially for developers with limited bandwidth.

- Traditional Git version control is based on changes within files. Storing binary files directly in the repository can cause issues with versioning, as even small changes can lead to complete file duplication.

- Developers can encounter conflicts when attempting to merge or resolve differences in large binary files.

- GitHub only allows up to 100MB file upload limit, which may not be enough for some large binary files.

<h2><span id="introducing-git-lfs">Introduction Git LFS</span></h2>

Git LFS is an open-source extension to Git that addresses these challenges by providing an efficient way to manage large files in a Git repository. Instead of storing the actual content of large files in the repository, Git LFS stores pointers (or metadata) to these files. The actual file content is then stored on a remote server, typically provided by GitHub itself or other supported Git hosting platforms.


- Git LFS stores large files on remote servers, allowing your repository to remain compact and fast, even when dealing with large binary files.

- Cloning, pushing, and pulling operations are significantly faster since you're only dealing with pointers to large files rather than the files themselves.

- By storing the actual binary files separately, you can keep your repository size manageable, which is crucial for maintaining a smooth development process.

- Developers can collaborate without the burden of large files, avoiding the typical slowdowns and conflicts associated with them.

<h2><span id="installation">Installation</span></h2>

### On Linux

Debian and RPM packages are available from packagecloud, see the [Linux installation instructions](https://github.com/git-lfs/git-lfs/blob/main/INSTALLING.md).

### On macOS

[Homebrew](https://brew.sh) bottles are distributed and can be installed via `brew install git-lfs`.

### On Windows

Git LFS is included in the distribution of [Git for Windows](https://gitforwindows.org/).
Alternatively, you can install a recent version of Git LFS from the [Chocolatey](https://chocolatey.org/) package manager.

### From binary

[Binary packages](https://github.com/git-lfs/git-lfs/releases) are
available for Linux, macOS, Windows, and FreeBSD.
The binary packages include a script which will:

- Install Git LFS binaries onto the system `$PATH`
- Run `git lfs install` to perform required global configuration changes.

```ShellSession
$ ./install.sh
```

Note that Debian and RPM packages are built for multiple Linux distributions and versions for both amd64 and i386.
For arm64, only Debian packages are built and only for recent versions due to the cost of building in emulation.

### From source

- Ensure you have the latest version of Go, GNU make, and a standard Unix-compatible build environment installed.
- On Windows, install `goversioninfo` with `go install github.com/josephspurrier/goversioninfo/cmd/goversioninfo@latest`.
- Run `make`.
- Place the `git-lfs` binary, which can be found in `bin`, on your system’s executable `$PATH` or equivalent.


<h2><span id="set-up-git-lfs">Set-up Git LFS</span></h2>

After installation, `cd` into your repository and configure your repository to use Git LFS by running:
```
git lfs install
```

### Selecting Large Files
Determine which files in your cloned local repository need to be tracked using Git LFS. Git LFS can be used when you want to version large files, usually, valuable output data, which is larger than the Github limit (100Mb). These files can be plain text or binaries.
1. Track Files: To start tracking large files, use the command:
   ```
   git lfs track "<file_pattern>"
   ```
   This command tells Git LFS to manage files matching the specified pattern.

2. Commit and Push: After tracking the necessary files, commit and push your changes to the repository.
   ```shell
   git commit
   git add .
   git push
   ```
   That's all! Git LFS will handle the rest, replacing the large files with pointers.


<h2><span id="how-it-works">How it Works?</span></h2>
Git LFS operates on a simple yet ingenious principle: it offloads the storage and management of large files from the primary Git repository.

- Instead of storing large files directly, Git LFS generates small pointer files containing metadata about the files. These pointers replace the actual content in the repository.

- Large files are hosted on an external Git LFS server, either GitHub's or a custom one you set up. The pointer files reference the server's location.

- When you clone a repository or fetch updates, only the pointer files are transferred initially, making the process quick and efficient.

- As you work, Git LFS fetches the actual large file content from the server only when needed, keeping your local repository light.

-------------------------

Git LFS is a game-changer for teams working with large files in Git repositories. By separating file pointers from the actual content, Git LFS optimizes storage, enhances performance, and streamlines collaboration. Whether you're building a game with high-resolution assets, working on video production, or dealing with any project involving large binary files, Git LFS can help you maintain a lean repository without sacrificing version control capabilities. Embrace the power of Git LFS to unlock the full potential of version control for projects of all sizes.

Thanks for reading! 😎
