# feature flow


- [feature flow](#feature-flow)
  - [Solo - feature flow](#solo---feature-flow)
  - [Team - feature flow](#team---feature-flow)


## Solo - feature flow
  - 一人でリモートリポジトリを使っている場合

| branch       | git                          | (origin) branch | (origin) action |
|--------------|------------------------------|-----------------|-----------------|
| main         | **# get feature-branch**     |                 |                 |
|              | git switch -c feature/some   |                 |                 |
|              |                              |                 |                 |
| feature/some | **# do feature and commit**  |                 |                 |
|              | git add .                    |                 |                 |
|              | git commit -m "Add some"     |                 |                 |
|              | **# switch to main**         |                 |                 |
|              | git switch main              |                 |                 |
|              |                              |                 |                 |
| main         | **# merge feature to main**  |                 |                 |
|              | git merge feature/some       |                 |                 |
|              | **# apply to origin main**   |                 |                 |
|              | git push origin main --force |                 |                 |
|              | **# remove feature-branch**  |                 |                 |
|              | git branch -d feature/some   |                 |                 |
|              | **# End**                    |                 |                 |


## Team - feature flow
  - チームでリモートリポジトリを使っている場合

| branch       | git                          | (origin) branch | (origin) action             |
|--------------|------------------------------|-----------------|-----------------------------|
| develop      | **# get feature-branch**     |                 |                             |
|              | git switch -c feature/some   |                 |                             |
|              |                              |                 |                             |
| feature/some | **# do feature and commit**  |                 |                             |
|              | git add .                    |                 |                             |
|              | git commit -m "Add some"     |                 |                             |
|              | **# push hotfix to origin**  |                 |                             |
|              | git push origin feature/some |                 |                             |
|              |                              |                 |                             |
|              |                              | main            | **# merge feature**         |
|              |                              |                 | main <- feature/some        |
|              |                              |                 | **# remove feature-branch** |
|              |                              |                 | proper action               |
|              |                              |                 |                             |
| feature/some | **# switch to main**         |                 |                             |
|              | git switch main              |                 |                             |
|              |                              |                 |                             |
| main         | **# fetch from origin**      |                 |                             |
|              | git fetch                    |                 |                             |
|              | **# pull origin**            |                 |                             |
|              | git pull origin main         |                 |                             |
|              | **# switch to develop**      |                 |                             |
|              | git switch develop           |                 |                             |
|              |                              |                 |                             |
| develop      | **# rebase to main**         |                 |                             |
|              | git rebase main              |                 |                             |
|              | **# remove feature-branch**  |                 |                             |
|              | git branch -d feature/some   |                 |                             |
|              | **# End**                    |                 |                             |
