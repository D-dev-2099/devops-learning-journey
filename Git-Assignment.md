#!/bin/bash
echo "Git Helper Menu"
echo "1. Clone a repo"
echo "2. Create new branch"
echo "3. Commit & push changes"
echo "4. Create tag"

read -p "Choose option: " opt

case $opt in
  1) read -p "Enter repo URL: " url
     git clone "$url"
     ;;
  2) read -p "Branch name: " name
     git checkout -b "$name"
     ;;
  3) git add . && git commit -m "Update" && git push
     ;;
  4) read -p "Tag name: " tag
     git tag -a "$tag" -m "Release $tag"
     git push origin "$tag"
     ;;
  *) echo "Invalid option" ;;
esac
