# Publication Pipeline

1) **publication directory:** This README file is located in an `exclude-from-pub` directory, which is a special sub-directory of a publication directory: meaning the contents are intended to be published via web publication pipeline
2) **local Git repo:** The obsidian vault to which the publication directory belong is set up as a Git repository.  This local repo is set up to sync with my github repo. 
3) **`hooks` directory**: in the hooks directory, there is a shell script `post-commit` which rsync's the parent directory contents to a local destination directory.  It is assumed that the local destination directory is a git repo. This rsync excludes the contents of the  `exclude-from-pub` directory.
4) **staging, committing, push at the destination directory:** one the rsync is completed,  shell script `post-commit` will stage and commit at the local destination.  It will then push the changes at the local destination directory to the upstream destination directory
5) CI/CD: at the upstream destination directory, GitHub Actions are used to implement observers of repo changes and when a trigger is detected, quartz commands are issued which publishes webpages from the markdown content

to trigger this pipeline, command-P to find Git: commit-and-sync