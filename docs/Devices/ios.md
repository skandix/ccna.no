# Interconnecting Operating System

## Commands

### ios commands
```bash
show flash # see whats already in the flash memory
delete flash:/<name_of_flash_to_delete>
```

### transfering new ios version to the cisco device
* setup local tftp server

Then on the cisco device
```bash
copy tftp flash
```

### verify file and set it to boot on next boot
```bash
show flash
conf term

boot system flash:/<name_of_flash>
exit
copy run start
reload
```
* After reload check that you have booted the correct ios
```bash
en
show ver # and now you should see the new version running on the device
```
