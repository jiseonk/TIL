* Date : 2020-05-12
* Tags : #git #command

## Get started with Git version control

<pre>
<code>$ git init</code>
</pre>
Initialize a local directory for git version control

<pre>
<code>$ nano</code>
</pre>
Create a new file and edit using the nano editor. 
On windows, the default editor will be Vim.

## Repeat edit -> add -> commit !

<pre>
<code>$ git status</code>
</pre>
Shows current state of the working tree (directory).
This command lists all the files you still need to add or commit.
*Untracked* means that file will not be version controlled.

<pre>
<code>$ git add hello.txt</code>
</pre>
Add a file to staging area to start version control with git.

<pre>
<code>$ git add .</code>
</pre>
Add all files under the current directory to staging area.

*note* Git doesn't control a file automatically. **You have to add it** to staging area.
