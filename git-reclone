#!/bin/bash
# @Author: TimsManter
# @AuthorSite: TimsManter.NET
# @CreateDate: 2017-11-12
# @License: MIT

TMP_DIR="/tmp/git-reclone"
GIT_DIR=$(ls -a | grep "^.git$")
GIT_URL=""

function setGitUrl {
  if [ -z "$1" ]; then
    echo "Git repository address:"
    read GIT_URL
    if [ -z "$GIT_URL" ]; then
      echo "Git repository URL is empty. Stopping..."
      exit 1
    fi
  else
    GIT_URL=$1
  fi
  echo "Git repository address will be $GIT_URL"
}

echo "Script started"

if [ -e "$GIT_DIR" ] && [ -d "$GIT_DIR" ]; then
  setGitUrl $(git remote get-url origin)
  rm -rf $GIT_DIR
  echo ".git directory removed"
else
  echo ".git directory doesn't exist. Skipping..."
  setGitUrl
fi

echo "Cloning repository"
git clone $GIT_URL $TMP_DIR
echo "Moving .git directory"
mv "$TMP_DIR/.git" .
echo "Removing temp directory"
rm -rf "$TMP_DIR"
echo "Done!"
exit 0