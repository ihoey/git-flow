# git-flow

## Git 分支开发规范

### master

- `master` 只能用于创建分支和接收合并，严格对应线上代码，不能直接 `commit`；
- `master` 只能通过向前合并分支的方式对其修改，接收 `stage` 和 `hotfix` 的 `merge request`。

### feature

- `feature` 由 `master` 创建分支，分支保持原子性的功能。不能直接合并到 `master`；
- 开发自测完毕后，先从 `master` 创建 `stage` 分支，再将 `feature` 合并到 `stage`，最后由 `stage` 合并到 `master`。

### stage

- `stage` 分支是为 `QA` 团队测试使用的，需要设定一个版本号，如 `stage/1.3.0` ；
- 在 `stage` 上测试出的 `bug` ，在对应的 `feature` 分支上进行修复，最后在合并到 `stage` 进行复测。

### hotfix

- 应对线上代码的紧急 `bug` 修复，需要从 `master` 创建 `hotfix` 分支；
- `hotfix` 上线后需要提交 `merge request` 合并到 `master`，同时要 `merge` 到所有 `stage` 分支；
- 最终通过 `stage` 上线，确认无误后提交 `merge request` 合并回 `master` 和所有 `stage` 分支。

### tag

- 同时从 `master` 创建 `tag` ，名称使用版本号，如 `1.4.0`；
- 创建 `tag` 时，务必使用 `md` 填写 `Release notes`。

### Notice

* 开发时从 `master` 切分支
* `feature` 分支命名为 `feature/xxx`, `xxx`命名尽量语义化；
* 尽量使用 `gitlab` 的权限管理与 `merge request`。
* 项目 `leader` 拥有 `master` 权限。
* 开发人员为 `developer` 权限，只能通过 `merge request` 合并代码。
* `leader` 在 `merge request` 中进行 `code review` 。
* 定期清理掉已完成的 `feature`、`hotfix`、`stage` 分支。
