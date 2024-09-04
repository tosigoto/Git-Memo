# feature flow


## 一人で開発していて、リモートリポジトリを　ローカルのバックアップ　として使っている場合

| branch       | git                          | (origin) branch | (origin) action |
| ------------ | ---------------------------- | --------------- | --------------- |
| develop      | # get feature-branch         |                 |                 |
|              | git checkout -b feature/some |                 |                 |
|              |                              |                 |                 |
| feature/some | # do feature and commit      |                 |                 |
|              | git add .                    |                 |                 |
|              | git commit -m "Add some"     |                 |                 |
|              | # switch to main             |                 |                 |
|              | git checkout main            |                 |                 |
|              |                              |                 |                 |
| main         | # merge feature to main      |                 |                 |
|              | git merge feature/some       |                 |                 |
|              | # apply to origin main       |                 |                 |
|              | git push origin main --force |                 |                 |
|              | # switch to develop          |                 |                 |
|              | git checkout develop         |                 |                 |
|              |                              |                 |                 |
| develop      | # rebase develop to main     |                 |                 |
|              | git rebase main              |                 |                 |
|              | # remove feature-branch      |                 |                 |
|              | git branch -d feature/some   |                 |                 |
|              | # End                        |                 |                 |
|              |                              |                 |                 |


## 複数人で開発している場合

| branch       | git                          | (origin) branch | (origin) action         |
| ------------ | ---------------------------- | --------------- | ----------------------- |
| develop      | # get feature-branch         |                 |                         |
|              | git checkout -b feature/some |                 |                         |
|              |                              |                 |                         |
| feature/some | # do feature and commit      |                 |                         |
|              | git add .                    |                 |                         |
|              | git commit -m "Add some"     |                 |                         |
|              | # push hotfix to origin      |                 |                         |
|              | git push origin feature/some |                 |                         |
|              |                              |                 |                         |
|              |                              | main            | # merge feature         |
|              |                              |                 | main <- feature/some    |
|              |                              |                 | # remove feature-branch |
|              |                              |                 | proper action           |
|              |                              |                 |                         |
| feature/some | # switch to main             |                 |                         |
|              | git checkout main            |                 |                         |
|              |                              |                 |                         |
| main         | # fetch from origin          |                 |                         |
|              | git fetch                    |                 |                         |
|              | # pull origin                |                 |                         |
|              | git pull origin main         |                 |                         |
|              | # switch to develop          |                 |                         |
|              | git checkout develop         |                 |                         |
|              |                              |                 |                         |
| develop      | # rebase to main             |                 |                         |
|              | git rebase main              |                 |                         |
|              | # remove feature-branch      |                 |                         |
|              | git branch -d feature/some   |                 |                         |
|              | # End                        |                 |                         |
|              |                              |                 |                         |
