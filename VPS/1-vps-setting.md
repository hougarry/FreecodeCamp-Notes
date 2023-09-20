# Part 1 New settings
## add new superuser
<details>
    <summary>add new superuser</summary>
**Step 1: Log In as Root**

Connect to your VPS using SSH as the root user.

```bash
ssh root@your_server_ip
```

**Step 2: Create a New User**

Create a new user account by replacing `<username>` with your desired username. You'll be prompted to set a password and provide additional information.

```bash
adduser <username>

#if you wanna delte
sudo userdel -r <username>

```

**Step 3: Add User to the Sudo Group**

To grant superuser privileges to the new user, add them to the sudo group.

```bash
usermod -aG sudo <username>
```

**Step 4: Test the New User**

Disconnect from your VPS and reconnect using the new username you created. You should be able to log in.

```bash
ssh <username>@your_server_ip
```

**Step 5: Test Sudo Access**

To confirm that the new user has superuser privileges, run a command with `sudo`. For example:

```bash
sudo apt update
```
</details>

##  2. add Visual env to execute
    
    构建虚拟环境可以帮助你在VPS上隔离不同的应用程序和项目，以防止它们之间的冲突。在Linux系统中，你可以使用Python的`virtualenv`工具来创建虚拟环境。以下是在VPS上构建虚拟环境并执行命令的基本步骤：
    
    1. **连接到VPS**: 使用SSH等远程连接工具连接到你的VPS。
    2. **安装`virtualenv`**: 在VPS上，首先需要安装`virtualenv`工具。你可以使用以下命令安装：
        
        ```
        sudo apt update
        sudo apt install python3-venv
        
        ```
        
    3. **创建虚拟环境**: 在VPS上的特定目录中，你可以创建一个新的虚拟环境。例如，要在`/path/to/your/project`目录中创建一个虚拟环境”name”，可以执行：
        
        ```
        python3 -m venv name
        
        ```
        
        这将在项目目录中创建一个名为`venv`的虚拟环境。
        
    4. **激活虚拟环境**: 进入虚拟环境，以便在其中执行命令。执行以下命令：
        
        ```
        source name/bin/activate
        
        ```
        
        一旦虚拟环境被激活，你会在命令提示符前看到环境名称（例如，`(venv)`）。
        
    5. **执行命令**: 在虚拟环境中，你可以执行你想要的各种命令。例如，安装Python包：
        
        ```
        pip install package_name
        
        ```
        
        运行Python脚本：
        
        ```
        python script.py
        
        ```
        
    6. **退出虚拟环境**: 当你完成在虚拟环境中的操作后，可以通过执行以下命令退出虚拟环境：
        
        ```
        deactivate
        
        ```
    7. delete it if you don't wanna use this virtualenv

        ```
            rm -r /path/to/venv
        ```   
    
    虚拟环境允许你隔离不同的项目和应用程序，以防止它们之间的冲突。这对于在VPS上管理多个应用程序或项目非常有用。记住，在虚拟环境中，你可以执行任何你通常在全局Python环境中执行的命令，但不会影响其他虚拟环境或全局环境。
    
