# mysql_copier

A simple bash script to copy a database from one mysql server to another

## Installing

Download the mysql_copier script. Then set it to be executable.

    wget https://raw.githubusercontent.com/mrkmg/mysql_copier/master/mysql_copier
    chmod +x mysql_copier
  
## Requirements
  
Both the Source and Destination should have mysql and mysqldump installed. If using SSH, then ssh should be installed as well. The script assumes you have passwordless authentication enabled as ssh prompting for a password does not work properly.
  
## Usage

Here is an quick example illustrating copying a database named `db_remote` on a remote server at `remote-server.local.net` via an ssh tunnel to a local database name `db_local`. 
  
    ./mysql_copier \
      --src-use-ssh \
      --src-ssh-user user \
      --src-ssh-host remote-server.local.net \
      --src-user root \
      --src--prompt-pass \
      --src-db db_remote \
      --dst-user username \
      --dst-promtp-pass \
      --dst-db db_local
      
## Full list of options

This can also be seen by running `./mysql_copier --help`

  	--help 				Show this help
  	
  	--src-use-ssh		Use SSH for source [false]
  	--src-ssh-host ARG	Source SSH Hostname
  	--src-ssh-opts ARG	Extra options to pass to source ssh
  	--src-ssh-user ARG	Source SSH User 
  	--src-host ARG		Source MySQL Host ["localhost"]
  	--src-user ARG		Source MySQL User ["root"]
  	--src-pass ARG		Source MySQL Password
  	--src-prompt-pass	Prompt for Source MySQL Password
  	--src-opts ARG		Source mysqldump options ["--single-transaction --opt"]
  	--src-db ARG		Source MySQL Database
  
  	--dst-use-ssh		Use SSH for destination [false]
  	--dst-ssh-host ARG	Destination SSH Hostname
  	--dst-ssh-opts ARG	Extra options to pass to destination ssh
  	--dst-ssh-user ARG	Destination SSH User
  	--dst-host ARG		Destination MySQL Host ["localhost"]
  	--dst-user ARG		Destination MySQL User ["root"]
  	--dst-pass ARG		Destination MySQL Password
  	--dst-prompt-pass	Prompt for Destination MySQL Password
  	--dst-opts ARG		Destination mysql options
  	--dst-db ARG		Destination MySQL Database
  
  	--buffer-size ARG	Bufer Size ["10m"]
  	--use-gzip			Use gzip on both sides
  	
  	
## License

MIT License
