# hotfix flow


- [hotfix flow](#hotfix-flow)
  - [Solo - hotfix flow](#solo---hotfix-flow)
  - [Team - hotfix flow](#team---hotfix-flow)


## Solo - hotfix flow
  - 一人でリモートリポジトリを使っている場合

| branch      | git                          | (origin) branch | (origin) action |
|-------------|------------------------------|-----------------|-----------------|
| main        | **# get hotfix-branch**      |                 |                 |
|             | git checkout -b hotfix/some  |                 |                 |
|             |                              |                 |                 |
| hotfix/some | **# do hotfix and commit**   |                 |                 |
|             | git add .                    |                 |                 |
|             | git commit -m "Fix some"     |                 |                 |
|             | **# switch to main**         |                 |                 |
|             | git checkout main            |                 |                 |
|             |                              |                 |                 |
| main        | **# merge hotfix to main**   |                 |                 |
|             | git merge hotfix/some        |                 |                 |
|             | **# apply to origin main**   |                 |                 |
|             | git push origin main --force |                 |                 |
|             | **# remove hotfix-branch**   |                 |                 |
|             | git branch -d hotfix/some    |                 |                 |
|             | **# End**                    |                 |                 |


## Team - hotfix flow
  - チームでリモートリポジトリを使っている場合

| branch      | git                         | (origin) branch | (origin) action            |
|-------------|-----------------------------|-----------------|----------------------------|
| main        | **# get hotfix-branch**     |                 |                            |
|             | git checkout -b hotfix/some |                 |                            |
|             |                             |                 |                            |
| hotfix/some | **# do hotfix and commit**  |                 |                            |
|             | git add .                   |                 |                            |
|             | git commit -m "Fix some"    |                 |                            |
|             | **# push hotfix to origin** |                 |                            |
|             | git push origin hotfix/some |                 |                            |
|             |                             |                 |                            |
|             |                             | main            | **# merge hotfix**         |
|             |                             |                 | main <- hotfix/some        |
|             |                             |                 | **# remove hotfix-branch** |
|             |                             |                 | proper action              |
|             |                             |                 |                            |
| hotfix/some | **# switch to main**        |                 |                            |
|             | git checkout main           |                 |                            |
|             |                             |                 |                            |
| main        | **# fetch origin**          |                 |                            |
|             | git fetch                   |                 |                            |
|             | **# pull origin**           |                 |                            |
|             | git pull origin main        |                 |                            |
|             | **# switch to develop**     |                 |                            |
|             | git checkout develop        |                 |                            |
|             |                             |                 |                            |
| develop     | **# rebase to main**        |                 |                            |
|             | git rebase main             |                 |                            |
|             | **# remove hotfix-branch**  |                 |                            |
|             | git branch -d hotfix/some   |                 |                            |
|             | **# End**                   |                 |                            |
