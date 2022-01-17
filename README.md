# Home Work Week One (Advanced GIT)
Home Work Week One : Advanced GIT
<br/>
The goal of this class is to understand and learn more about git. The concept, how it works, and the flow. For that, the course will use the command line to understand git better and not through application/wizard, since it created to spare you the trouble.
<br/>

# What's git?
```
git is distributed version control system
```
<br/>
OTHER OPTIMIZATIONS - PACKFILES, DELTAS
<ol>
    <li>Git objects are compressed</li>
    <li>As files change, their contents remain mostly similar.</li>
    <li>Git optimizes for this by compressing these files together, into a Packfile</li>
    <li>The Packfile stores the object, and “deltas”, or the diﬀerences between one version of the file and the next.</li>
    <li>Packfiles are generated when: you have too many objects, during gc, or during a push to a remote</li>
</ol>

# Storage
Git stores the compressed data in a blob, along with meta data in the header. Git store its data in git directory which contains data about our repository, and the blobs are stored in git objects. In git object, the blob missing some information (filename, directory structures) which is stored in a tree. A tree contain pointers to blobs and other trees because directory can be nested.
<br/>
How Git stores information comparing it to a key-value store where data is the value and the hash of the data is the key. This system is also known as content-addressable storage, which is when the content to generate the key.
- you can then use the key to retrieve the content
- the key it's called a SHA1, is cryptographic hash function given a piece of data.
- it produces a 40-digit hexadecimal number and this value should always be the same if the given input is the same

# Git Commit</h2>
<div>
  Commit is a give information in git any changes up to the current condition, it's a combination from previous commit.
  Most important in commit:
  <ul>
    <li>cant change this commit</li>
    <li>cant edit</li>
    <li>cant go back</li>
    <li>cant change the author</li>
    <li>cant change the date</li>
  </ul>
</div>
Commits, which is an object that stores the current contents of the project in a new commit with a log message from the user describing the changes, there's three types of object will create when we do git commit 
<ul>
<li>Tree</li>
<li>Blob</li>
<li>Commit</li>
</ul>

[here](https://github.com/nnja/advanced-git/blob/master/exercises/Exercise1-SimpleCommit.md) for exercice to know more about what we are talking about
```
% tree .git/objects
.git/objects
├── 58
│   └── 1caa0fe56cf01dc028cc0b089d364993e046b6
├── 98
│   └── 0a0d5f19a64b4b30a87d4206aade58726b60e3
├── 99
│   └── b2172e47a9367ff4cb3fc9c093090087688807
├── info
└── pack
```

- the Tree
```
% git cat-file -t 581ca         
tree
% git cat-file -p 581ca
100644 blob 980a0d5f19a64b4b30a87d4206aade58726b60e3	hello.txt
```
- the Blob
```
% git cat-file -t 980a0
blob
% git cat-file -p 980a0
Hello World!
```
- the Commit
```
% git cat-file -t 99b21
commit
% git cat-file -p 99b21
tree 581caa0fe56cf01dc028cc0b089d364993e046b6
author Rezha Erlangga <reza@machtwatch.co.id> 1642390839 +0700
committer Rezha Erlangga <reza@machtwatch.co.id> 1642390839 +0700

Initial commit
```
# Git Areas and Stashing 
Three areas where code lives : working area (or sometimes called as working tree), staging area (or cache or index) and repository. The working area are the files in your working area that are not in staging area and not handled by git, basically the files in your local directory in your computer. The staging area is how git knows what will change between the current commit and the next commit. The repository contains all your commits. Git stash is used to save un-committed work and safe from git destructive operation like changing branches while in the middle of work or overwriting file. And you can apply it back to your branch anytime when needed.

# Command for stashing your code

```sh
git stash
```

# Command for how to show your list stash

```sh
git stash list
```

# Command for how to show your list stash

```sh
git stash list
```

# Command for show your content in your list stash

```sh
git stash show stash@{n}
```

# Command for apply ur last stash

```sh
git stash apply
```

# Command for apply ur specific stash

```sh
git stash apply stash@{n}
```

# Command for stashing untracked files

```sh
git stash --include-untracked
```

# Command for stashing all files

```sh
git stash --all
```

# Command for delete last stashing and applying change

```sh
git stash pop
```

# Command for delete last stash

```sh
git stash drop
```

# Command for delete specific stash

```sh
git stash drop stash@{n}
```

# Command for delete all stash

```sh
git stash clear
```

# Reference
Advanced GIT Nina Zakharenko [here](https://github.com/nnja/advanced-git)
