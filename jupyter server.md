# Jupyter Server

Most of the time, we don't have computationally heavy work, and we are just using laptops. However, sometimes we need to perform intermediate-level computational tasks quickly or maintain a consistent development environment. Running a Jupyter server somewhere secure is a good solution.

## Is it for you?
### Pros
- Easy access and unmanaged: It's not a managed cluster; it's just a computer in the lab, at home, or on some online virtual machine. We have admin privileges for it and can perform any desired actions.
- Consistent development environment: Whether it's a Conda environment or a virtual environment, we can easily manage the environment of the notebook. Additionally, we can run several kernels from different environments simultaneously.
- Persistent: Unlike Colab, we can keep the PC on, and the Jupyter kernel will always be active. This prevents losing work due to accidentally closing the laptop, as often happens with local setups.
- Interactive: It can handle decent computations while also rendering results nicely. 2D plots will render instantly, and 3D interactive plots are also available, albeit with some delay.

### Cons
- Not suitable for heavy loads: It's just a single PC, not a cluster. For heavy workloads, it's better to use clusters.
- Unmanaged: There's a small chance of misuse, such as accidentally changing the environment (e.g., updating some package), and those changes are permanent.

## Usages
- Find the IP address: You can use `ipconfig` in the terminal to obtain your server's IP address. For home networks in the US, the IP address is relatively stable, usually changing only after modem restarts. Alternatively, services like `DuckDNS` can be used to maintain a consistent address for your server.
- SSH to server: Use `ssh user@server_ip` to connect to your server. To simplify this process, you can add your client's public key to the authorized keys file on the server.
- Start a TMUX session: Without TMUX, jobs running over SSH will terminate upon closing the SSH connection. TMUX is a tool for terminal window management that keeps sessions active even after SSH sessions end.
- Start a notebook: Use commands like `jupyter notebook` in the SSH window. The terminal will provide a URL like `localhost:xxxx/asdfasdfasdfasdfas`, which you can open in a web browser or in VSCode to start using the notebook.

## Debug
While the setup is relatively simple, there are some common issues to keep in mind when debugging:
- Related to SSH client: Check the SSH config file, located in `~/.ssh` for Linux and macOS, or `$HOME\.ssh\config` for Windows. Also, ensure the public key file is in the same folder.
- Related to SSH server: If you encounter issues like being unable to log in without entering a password, check the server config and the authorized keys file, located at `~/.ssh/authorized_keys` for Unix-like systems and `$HOME\.ssh\authorized_keys` or `__PROGRAMDATA__/ssh/administrators_authorized_keys` for Windows.
note ssh is for client and sshd is for server. 
- Related to Jupyter notebook: If you can't log in or start a kernel, check the notebook config file located at `~/.jupyter/jupyter_notebook_config.py`. Ensure that the setting allowing connections from all sources is enabled if necessary.
