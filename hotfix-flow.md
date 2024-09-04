# hotfix flow

## 一人で開発していて、リモートリポジトリを　ローカルのバックアップ　として使っている場合
| branch      | git                          | (origin) branch | (origin) action |
| ----------- | ---------------------------- | --------------- | --------------- |
| main        | # get hotfix-branch          |                 |                 |
|             | git checkout -b hotfix/some  |                 |                 |
|             |                              |                 |                 |
| hotfix/some | # do hotfix and commit       |                 |                 |
|             | git add .                    |                 |                 |
|             | git commit -m "Fix some"     |                 |                 |
|             |                              |                 |                 |
| main        | # merge hotfix to main       |                 |                 |
|             | git checkout main            |                 |                 |
|             | git merge hotfix/some        |                 |                 |
|             | # apply to origin main       |                 |                 |
|             | git push origin main --force |                 |                 |
|             | # switch to develop          |                 |                 |
|             | git checkout develop         |                 |                 |
|             |                              |                 |                 |
| develop     | # rebase develop to main     |                 |                 |
|             | git rebase main              |                 |                 |
|             | # remove hotfix-branch       |                 |                 |
|             | git branch -d hotfix/some    |                 |                 |
|             | # End                        |                 |                 |
|             |                              |                 |                 |


## 複数人で開発している場合
| branch      | git                         | (origin) branch | (origin) action        |
| ----------- | --------------------------- | --------------- | ---------------------- |
| main        | # get hotfix-branch         |                 |                        |
|             | git checkout -b hotfix/some |                 |                        |
|             |                             |                 |                        |
| hotfix/some | # do hotfix and commit      |                 |                        |
|             | git add .                   |                 |                        |
|             | git commit -m "Fix some"    |                 |                        |
|             | # push hotfix to origin     |                 |                        |
|             | git push origin hotfix/some |                 |                        |
|             |                             |                 |                        |
|             |                             | main            | # merge hotfix         |
|             |                             |                 | main <- hotfix/some    |
|             |                             |                 | # remove hotfix branch |
|             |                             |                 | proper action          |
|             |                             |                 |                        |
| hotfix/some | # switch to main            |                 |                        |
|             | git checkout main           |                 |                        |
|             |                             |                 |                        |
| main        | # fetch from origin         |                 |                        |
|             | git fetch                   |                 |                        |
|             | # pull origin               |                 |                        |
|             | git pull origin main        |                 |                        |
|             | # switch to develop         |                 |                        |
|             | git checkout develop        |                 |                        |
|             |                             |                 |                        |
| develop     | # rebase to main            |                 |                        |
|             | git rebase main             |                 |                        |
|             | # remove hotfix-branch      |                 |                        |
|             | git branch -d hotfix/some   |                 |                        |
|             | # End                       |                 |                        |
|             |                             |                 |                        |