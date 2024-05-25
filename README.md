# boot_loader
ansible role for bootloader management

## requirements
- grubby

## variables
- grub_file: /etc/default/grub
  - global grub settings
- grub_task: configure
  - use **configure** to add or modify settings
  - use **remove** to remove settings
- grubby_task: configure
  - use **configure** to add or modify settings
  - use **remove** to remove settings

## dependencies

## examples
```
- name: display grub menu
  ansible.builtin.include_role:
    name: boot_loader
    tasks_from: grub_settings.yml
  vars:
    grub_task: configure
    grub_settings:
      - key: GRUB_HIDDEN_TIMEOUT
        value: 0
      - key: GRUB_TIMEOUT_STYLE
        value: menu
      - key: GRUB_TIMEOUT
        value: 5
```
```
- name: remove default kernel arguments
  ansible.builtin.include_role:
    name: boot_loader
    tasks_from: kernel_arguments.yml
  vars:
    grubby_task: remove
    kernel_arguments:
      - crashkernel
      - quiet
      - rhgb
```
