
#### Checking Selinux security context -Z flag with ls

```
ls -Z  file / folder name
```



#### To change the Selinux security context of a file 

```
chcon -t context type filename
```


#### To change the Selinux security context of a folders recursively 

```
chcon -R -t context type folder path
```


#### This is only temporary, we can restore the default context type via :

```
restoreconv -v file name

v stands for verbose. The -v option will display on the screen the previous security context and the newly changed selinux context.
```


#### You can also reset the security context of the files recursively. Use -R option as shown below.

```
restorecon -vR /var/www/html

This will reset the context or all the files in /var/www/html and under its subdirectories.
```

#### To make the changes permananent so it won't be reverted while someone changes it to default values via restorecon

```
semanage fcontext -a -t cpntext type directory 


It changes the policy of the selinux in file :

/etc/selinux/trageted/contexts/files/file_contexts.local

-a, --add - dd a OBJECT record NAME

t, --type - SELinux Type for the object
```

### Then to reflect this policy to the file / folder :

```
restorecon -v directory


It is permanent. Nobody will not be able to change the context again.
```
