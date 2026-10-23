
## 1. Fork 官方仓库

打开 [SagerNet/sing-box](https://github.com/SagerNet/sing-box)，点击右上角 Fork，将仓库复制到自己的 GitHub 账号。

## 2. 克隆自己的仓库

把 `你的用户名` 替换为自己的 GitHub 用户名：

```
git clone https://github.com/你的用户名/sing-box.git
cd sing-box
```

添加官方仓库：

```
git remote add upstream https://github.com/SagerNet/sing-box.git
git fetch upstream
```

## 3. 创建自己的 stable 分支

先检查官方是否存在 `stable`：

```
git branch -r
```

确认有 `upstream/stable` 后，执行：

```
git switch -c stable --track upstream/stable
git push -u origin stable
```

如果本地已经有 `stable` 分支，则执行：

```
git switch stable
git branch --set-upstream-to=upstream/stable stable
```

## 4. 创建自己的功能分支

```
git switch -c my-stable
git push -u origin my-stable
```

之后你新增的功能都在 `my-stable` 分支上开发：

```
git add .
git commit -m "feat: add my custom feature"
git push
```

## 5. 官方 stable 更新后同步

先同步官方代码：

```
git switch stable
git fetch upstream
git merge upstream/stable
git push origin stable
```

再同步到你的功能分支：

```
git switch my-stable
git merge stable
git push origin my-stable
```

如果有冲突，解决后再提交即可。

最终结构：

| 分支                 | 用途             |
| ------------------ | -------------- |
| `upstream/stable`  | 官方最新 stable 代码 |
| `origin/stable`    | 你仓库中同步后的官方代码   |
| `origin/my-stable` | 你自己的功能修改       |

这样就能持续跟进官方 `stable` 更新，同时保留自己的功能。