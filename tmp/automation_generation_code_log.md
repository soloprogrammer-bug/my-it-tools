# 配置HTTP和HTTPS代理（把7890改成你自己的代理端口）
git config --global http.proxy http://127.0.0.1:7897
git config --global https.proxy http://127.0.0.1:7897

# 验证配置是否成功
git config --list | grep proxy

# 以后如果不需要代理了，可以用这个命令取消：
git config --global --unset http.proxy
git config --global --unset https.proxy

# 以普通用户身份打开 PowerShell（不需要管理员）永久修改当前用户的执行策略
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned