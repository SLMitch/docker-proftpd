## proftpd


An easy-to-use, tiny yet full-featured installation of ProFTPD.

Fork of instantlinux/docker-tools, but without secret, all in environment variable (less secure, but for other workflow)

### Usage

The most-common directives can be specified in environment variables as shown below. One is required, the PASV_ADDRESS. If you need further customizations, put them in one or more files under mount points /etc/proftpd.d and /etc/proftpd/modules.d.

A single upload user can be specified via the FTPUSER_xxx variables. It is activated by defining ftp-user-password-secret thus:


An example compose file is provided here in docker-compose.yml. This is for the common scenario of sharing from Docker swarm the contents of a network-attached volume as a read-only anonymous-ftp service.

### Variables

Variable | Default | Description |
-------- | ------- | ----------- |
ALLOW_OVERWRITE | on | allow clients to modify files
ANONYMOUS_DISABLE | off | anonymous login
ANON_UPLOAD_ENABLE | DenyAll | anonymous upload
FTPUSER_PASSWORD | ftppassword | pw of upload user
FTPUSER_NAME | ftpuser | upload username
FTPUSER_UID | 1001 | upload file ownership UID
LOCAL_UMASK | 022 | upload umask
MAX_CLIENTS | 10 | maximum simultaneous logins
MAX_INSTANCES | 30 | process limit
PASV_ADDRESS |  | required--address of docker engine
PASV_MAX_PORT | 30100 | range of client ports (rebuild image if changed)
PASV_MIN_PORT | 30091 | 
TIMES_GMT | off | local time for directory listing
TZ | UTC | local timezone
WRITE_ENABLE | AllowAll | allow put/rm
