# lunchbox
Simple Lunchbox Server Deployment
=================================

Create a bootable lunchbox image from a base Red Hat Enterprise Linux 7 install image on your localhost.  Currently only customizes the UEFI boot menu.

Requirements
------------

- Runs as user with privileges to create temporary files
- Runs as user with privileges to mount loop devices
- Either needs the following packages installed or runs as user with privileges to install them:
  - `mkisofs`
  - `syslinux`
  - `isomd5sum`

Variables
--------------

| Variable | Required | Default | Description |
| -------- | -------- | ------- | ----------- |
| `local_home` | :heavy_check_mark: | | Local $HOME user environment |
| `custom_install_image_src_iso` | :heavy_check_mark: | | Fully qualified location of EL7 ISO (currently only RHEL 7.6+ functions) |
| `custom_install_image_dst_iso` | :heavy_check_mark: | | Fully qualified location to save the newly created ISO (will be overwritten if it exists) |
| `custom_install_image_ks_file` | :heavy_check_mark: | | Fully qualified location of the custom kickstart file |
| `custom_install_image_label` |  | ```custom_image``` | Label that appears when the custom ISO/disk is mounted |
| `custom_install_image_menu_label` |  | ```Custom Image``` | Label that appears in the installer menu |

External Vars File
------------------

- You will need to set up the following variables in an "external_vars.yml" file

  - `rhuser: myusername`
  - `rhpass: mypassword`
  - `poolid: 8675309a8675309a8675309a8675309a`

Example
------------

ansible-playbook build-lunchbox-iso.yml -K
