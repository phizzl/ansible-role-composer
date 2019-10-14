# Ansible role composer
A role run the `composer install` command for PHP applications

## Requirements
- Hosts should be bootstrapped for ansible usage (have python,...)

## Role Variables

| Variable | Description | Default value |
|----------|-------------|---------------|
| `composer_php_executable` | Path to the php executable that is used during composer install | php |
| `composer_phar_file`| Path to the `composer.phar`. If it doesn't exist it will be instaled to the given location | "~/composer.phar" |
| `composer_install_directories`| The artifat definitions. See below for details. | [] |


### `composer_install_directories` details

| Variable | Description | Required | Default |
|----------|-------------|----------|---------|
| `path` | The path to execute the `composer install` command in | yes | / |
| `extraflags` | Extra flags like `--no-dev` to pass to the `composer install` command | no | "" |

## Dependencies

--

## Example playbook
```yaml
- name: Execute composer install
  hosts: composer
  roles:
    - role: composer
      vars:
        composer_install_directories:
          - path: "."
            extraflags: "--optimize-autoloader --prefer-dist --no-dev --no-scripts"
          - path: "www"
            extraflags: "--optimize-autoloader --prefer-dist --no-dev --no-scripts"
```
