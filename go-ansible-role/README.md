Ansible Role for Go! - Manage Go installation with Ansible.

> The following variables are used to configure the role. Please edit the `defaults/main.yml` file to change the default values or you can also override the variables in your playbook.

| Variable             | Description               | Default                       | Possible Opts                   |
| -------------------- | ------------------------- | ----------------------------- | ------------------------------- |
| `go_os`              | GOOS environment var      | `linux`                       | `linux`                         |
| `go_arch`            | GOARCH environment var    | `amd64`                       | `amd64`                         |
| `go_path`            | GOPATH environment var    | `~/.gopath`                   | any path                        |
| `go_root`            | GOROOT env var            | `~/.goroot`                   | any path                        |
| `go_version`         | Golang version            | `1.20.3`                      | any golang version              |
| `shell_profile`      | Shell profile rc          | `~/.bashrc`                   | `~/.bashrc`, `~/.profile`, etc. |
| `go_source_dest`     | Golang source destination | `/tmp/<src>`                  | any path                        |
| `go_source_url`      | Golang source slug        | `https://golang.org/dl/<src>` | valid dl slug of golang         |
| `go_source_checksum` | Checksum of golang source | - (ommitted)                  | please visit go dl page         |
| `upgrade_pkgs`       | Upgrade install pkgs      | `false`                       | `true`, `false`                 |
| `install_pkgs`       | Install essential pkgs    | `false`                       | `true`, `false`                 |
| `enable_debug`       | Enable debug mode         | `false`                       | `true`, `false`                 |
| `go_get_pkgs`        | Download any go packages  | `false`                       | any valid go packages           |
| `go_install_pkgs`    | Install any go packages   | `false`                       | any valid go packages           |                        

> Note: [https://golang.org/dl/](https://golang.org/dl/) is the official download page for Golang. You can find the versions and checksums of all current and previous go versions. 
