# 【关键】直接修改远程仓库地址为你自己的
git remote set-url origin https://github.com/soloprogrammer-bug/my-it-tools.git

# 验证一下，确认已经改成你的地址了
git remote -v

# 添加所有文件
git add .

# 提交
git commit -m "初始化 my-it-tools 项目"

# 推送到远程仓库（如果你的分支是 main）
git push -u origin main

# 如果上面的命令报错，试试这个（如果你的分支是 master）
git push -u origin master

git config --global user.name "soloprogrammer-bug"
git config --global user.email "solowolf0114@163.com"