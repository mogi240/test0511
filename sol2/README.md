1. https://github.com/mogi240/test0511.git 생성 및 clone
2. ~/.bashrc export TF_VAR_AWS_REGION="eu-west-1"
3. 아일랜드 리전에 기본 VPC설정
4. 테라폼적용
   ta
   terraform init
   terraform plan
   terraform apply -auto-approve
5.보안그룹에서 http 80포트 인바운드 허용

#아마존 ssh접속
`````
ubuntu@u1:/mnt/hgfs/Desktop/terraform-course/test0511$ ssh -i ~/mykey ubuntu@54.229.49.63
Warning: Permanently added '54.229.49.63' (ECDSA) to the list of known hosts.
Welcome to Ubuntu 20.04 LTS (GNU/Linux 5.4.0-1009-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Mon May 11 02:54:56 UTC 2020

  System load:  0.21              Processes:             105
  Usage of /:   18.2% of 7.69GB   Users logged in:       0
  Memory usage: 20%               IPv4 address for eth0: 172.31.6.233
  Swap usage:   0%


19 updates can be installed immediately.
10 of these updates are security updates.
To see these additional updates run: apt list --upgradable


Last login: Mon May 11 02:52:59 2020 from 59.13.4.75
ubuntu@ip-172-31-6-233:~$ df -k
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/root        8065444 1467248   6581812  19% /
devtmpfs          488748       0    488748   0% /dev
tmpfs             501052       0    501052   0% /dev/shm
tmpfs             100212     784     99428   1% /run
tmpfs               5120       0      5120   0% /run/lock
tmpfs             501052       0    501052   0% /sys/fs/cgroup
/dev/loop0         96256   96256         0 100% /snap/core/9066
/dev/loop1         56320   56320         0 100% /snap/core18/1705
/dev/loop2         70656   70656         0 100% /snap/lxd/14804
/dev/loop3         18432   18432         0 100% /snap/amazon-ssm-agent/1566
tmpfs             100208       0    100208   0% /run/user/1000
ubuntu@ip-172-31-6-233:~$
````

#테라폼 생성
```
Initializing the backend...

Initializing provider plugins...

The following providers do not have any version constraints in configuration,
so the latest version was installed.

To prevent automatic upgrades to new major versions that may contain breaking
changes, it is recommended to add version = "..." constraints to the
corresponding provider blocks in configuration, with the constraint strings
suggested below.

* provider.aws: version = "~> 2.60"

Terraform has been successfully initialized!

You may now begin working with Terraform. Try running "terraform plan" to see
any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your working directory. If you forget, other
commands will detect it and remind you to do so if necessary.
aws_key_pair.mykey: Creating...
aws_key_pair.mykey: Creation complete after 3s [id=mykey]
aws_instance.example[0]: Creating...
aws_instance.example[2]: Creating...
aws_instance.example[1]: Creating...
aws_instance.example[3]: Creating...
aws_instance.example[0]: Still creating... [10s elapsed]
aws_instance.example[2]: Still creating... [10s elapsed]
aws_instance.example[1]: Still creating... [10s elapsed]
aws_instance.example[3]: Still creating... [10s elapsed]
aws_instance.example[2]: Still creating... [20s elapsed]
aws_instance.example[0]: Still creating... [20s elapsed]
aws_instance.example[1]: Still creating... [20s elapsed]
aws_instance.example[3]: Still creating... [20s elapsed]
aws_instance.example[2]: Still creating... [30s elapsed]
aws_instance.example[0]: Still creating... [30s elapsed]
aws_instance.example[1]: Still creating... [30s elapsed]
aws_instance.example[3]: Still creating... [30s elapsed]
aws_instance.example[0]: Provisioning with 'file'...
aws_instance.example[2]: Still creating... [40s elapsed]
aws_instance.example[0]: Still creating... [40s elapsed]
aws_instance.example[1]: Still creating... [40s elapsed]
aws_instance.example[3]: Still creating... [40s elapsed]
aws_instance.example[3]: Provisioning with 'file'...
aws_instance.example[1]: Provisioning with 'file'...
aws_instance.example[0]: Provisioning with 'remote-exec'...
aws_instance.example[0] (remote-exec): Connecting to remote host via SSH...
aws_instance.example[0] (remote-exec):   Host: 18.203.100.225
aws_instance.example[0] (remote-exec):   User: ubuntu
aws_instance.example[0] (remote-exec):   Password: false
aws_instance.example[0] (remote-exec):   Private key: true
aws_instance.example[0] (remote-exec):   Certificate: false
aws_instance.example[0] (remote-exec):   SSH Agent: false
aws_instance.example[0] (remote-exec):   Checking Host Key: false
aws_instance.example[2]: Provisioning with 'file'...
aws_instance.example[0] (remote-exec): Connected!
aws_instance.example[3]: Provisioning with 'remote-exec'...
aws_instance.example[3] (remote-exec): Connecting to remote host via SSH...
aws_instance.example[3] (remote-exec):   Host: 34.241.193.25
aws_instance.example[3] (remote-exec):   User: ubuntu
aws_instance.example[3] (remote-exec):   Password: false
aws_instance.example[3] (remote-exec):   Private key: true
aws_instance.example[3] (remote-exec):   Certificate: false
aws_instance.example[3] (remote-exec):   SSH Agent: false
aws_instance.example[3] (remote-exec):   Checking Host Key: false
aws_instance.example[1]: Provisioning with 'remote-exec'...
aws_instance.example[1] (remote-exec): Connecting to remote host via SSH...
aws_instance.example[1] (remote-exec):   Host: 3.250.148.103
aws_instance.example[1] (remote-exec):   User: ubuntu
aws_instance.example[1] (remote-exec):   Password: false
aws_instance.example[1] (remote-exec):   Private key: true
aws_instance.example[1] (remote-exec):   Certificate: false
aws_instance.example[1] (remote-exec):   SSH Agent: false
aws_instance.example[1] (remote-exec):   Checking Host Key: false
aws_instance.example[0]: Still creating... [50s elapsed]
aws_instance.example[2]: Still creating... [50s elapsed]
aws_instance.example[1]: Still creating... [50s elapsed]
aws_instance.example[3]: Still creating... [50s elapsed]
aws_instance.example[2]: Provisioning with 'remote-exec'...
aws_instance.example[2] (remote-exec): Connecting to remote host via SSH...
aws_instance.example[2] (remote-exec):   Host: 3.249.187.15
aws_instance.example[2] (remote-exec):   User: ubuntu
aws_instance.example[2] (remote-exec):   Password: false
aws_instance.example[2] (remote-exec):   Private key: true
aws_instance.example[2] (remote-exec):   Certificate: false
aws_instance.example[2] (remote-exec):   SSH Agent: false
aws_instance.example[2] (remote-exec):   Checking Host Key: false
aws_instance.example[1] (remote-exec): Connected!
aws_instance.example[3] (remote-exec): Connected!
aws_instance.example[2] (remote-exec): Connected!
aws_instance.example[0] (remote-exec): 0% [Working]
aws_instance.example[0] (remote-exec): Get:1 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal InRelease [265 kB]
aws_instance.example[0] (remote-exec): 0% [1 InRelease 0 B/265 kB 0%] [Connect
aws_instance.example[0] (remote-exec): 0% [Connecting to security.ubuntu.com (
aws_instance.example[0] (remote-exec): Get:2 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates InRelease [107 kB]

aws_instance.example[0] (remote-exec): Get:3 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports InRelease [98.3 kB]
aws_instance.example[0] (remote-exec): 0% [Connecting to security.ubuntu.com (
aws_instance.example[0] (remote-exec): 0% [Waiting for headers]
aws_instance.example[0] (remote-exec): Get:4 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 Packages [970 kB]
aws_instance.example[0] (remote-exec): 0% [4 Packages 26.6 kB/970 kB 3%] [Wait
aws_instance.example[0] (remote-exec): 0% [Waiting for headers]
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B] [Waiting for
aws_instance.example[0] (remote-exec): Get:5 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main Translation-en [506 kB]
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B] [5 Translatio
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B] [Waiting for
aws_instance.example[0] (remote-exec): Get:6 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 c-n-f Metadata [29.5 kB]
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B] [6 Commands-a
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B] [Waiting for
aws_instance.example[0] (remote-exec): Get:7 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe amd64 Packages [8628 kB]
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B] [7 Packages 0
aws_instance.example[0] (remote-exec): Get:8 http://security.ubuntu.com/ubuntu focal-security InRelease [107 kB]
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B] [7 Packages 7
aws_instance.example[0] (remote-exec): Get:9 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe Translation-en [5124 kB]
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B] [9 Translatio
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B] [9 Translatio
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B] [9 Translatio
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[0] (remote-exec): Get:10 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe amd64 c-n-f Metadata [265 kB]
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B] [10 Commands-
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[0] (remote-exec): Get:11 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse amd64 Packages [144 kB]
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B] [11 Packages
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[0] (remote-exec): Get:12 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse Translation-en [104 kB]
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B] [12 Translati
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[0] (remote-exec): Get:13 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse amd64 c-n-f Metadata [9136 B]
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B] [13 Commands-
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[0] (remote-exec): Get:14 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [84.4 kB]
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B] [14 Packages
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[0] (remote-exec): Get:15 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main Translation-en [30.2 kB]
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B] [15 Translati
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[0] (remote-exec): 0% [Waiting for headers]
aws_instance.example[0] (remote-exec): Get:16 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main amd64 c-n-f Metadata [1940 B]
aws_instance.example[0] (remote-exec): 0% [16 Commands-amd64 0 B/1940 B 0%]
aws_instance.example[0] (remote-exec): 0% [Working]
aws_instance.example[0] (remote-exec): Get:17 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/restricted amd64 Packages [4180 B]
aws_instance.example[0] (remote-exec): 0% [17 Packages 0 B/4180 B 0%]
aws_instance.example[0] (remote-exec): 0% [Working]
aws_instance.example[0] (remote-exec): Get:18 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/restricted Translation-en [1360 B]
aws_instance.example[0] (remote-exec): 0% [18 Translation-en 0 B/1360 B 0%]
aws_instance.example[0] (remote-exec): 0% [Working]
aws_instance.example[0] (remote-exec): Get:19 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [27.2 kB]
aws_instance.example[0] (remote-exec): 0% [19 Packages 0 B/27.2 kB 0%]
aws_instance.example[0] (remote-exec): 0% [5 Translation-en store 0 B] [19 Pac
aws_instance.example[0] (remote-exec): 0% [5 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): Get:20 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe Translation-en [13.3 kB]
aws_instance.example[0] (remote-exec): 0% [5 Translation-en store 0 B] [20 Tra
aws_instance.example[0] (remote-exec): 0% [5 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): Get:21 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe amd64 c-n-f Metadata [1132 B]
aws_instance.example[0] (remote-exec): 0% [5 Translation-en store 0 B] [21 Com
aws_instance.example[0] (remote-exec): 0% [5 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): Get:22 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 c-n-f Metadata [116 B]
aws_instance.example[0] (remote-exec): 0% [5 Translation-en store 0 B] [22 Com
aws_instance.example[0] (remote-exec): 0% [5 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): 0% [Working]
aws_instance.example[0] (remote-exec): 0% [6 Commands-amd64 store 0 B]
aws_instance.example[0] (remote-exec): 0% [Working]
aws_instance.example[0] (remote-exec): 0% [7 Packages store 0 B]
aws_instance.example[0] (remote-exec): 0% [7 Packages store 0 B]
aws_instance.example[0] (remote-exec): Get:23 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/main amd64 c-n-f Metadata [112 B]
aws_instance.example[0] (remote-exec): 0% [7 Packages store 0 B]
aws_instance.example[0] (remote-exec): Get:24 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/restricted amd64 c-n-f Metadata [116 B]
aws_instance.example[0] (remote-exec): 0% [7 Packages store 0 B] [Waiting for
aws_instance.example[0] (remote-exec): Get:25 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe amd64 Packages [2792 B]
aws_instance.example[0] (remote-exec): 0% [7 Packages store 0 B] [Waiting for
aws_instance.example[0] (remote-exec): Get:26 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe Translation-en [1280 B]
aws_instance.example[0] (remote-exec): 0% [7 Packages store 0 B] [Waiting for
aws_instance.example[0] (remote-exec): Get:27 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe amd64 c-n-f Metadata [188 B]
aws_instance.example[0] (remote-exec): 0% [7 Packages store 0 B] [Waiting for
aws_instance.example[0] (remote-exec): Get:28 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/multiverse amd64 c-n-f Metadata [116 B]
aws_instance.example[0] (remote-exec): 0% [7 Packages store 0 B]
aws_instance.example[0] (remote-exec): 92% [7 Packages store 0 B]
aws_instance.example[0] (remote-exec): Get:29 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages [50.1 kB]
aws_instance.example[0] (remote-exec): 92% [7 Packages store 0 B] [29 Packages
aws_instance.example[0] (remote-exec): 93% [7 Packages store 0 B]
aws_instance.example[0] (remote-exec): Get:30 http://security.ubuntu.com/ubuntu focal-security/main Translation-en [18.5 kB]
aws_instance.example[0] (remote-exec): 93% [7 Packages store 0 B] [30 Translat
aws_instance.example[0] (remote-exec): 93% [7 Packages store 0 B]
aws_instance.example[0] (remote-exec): Get:31 http://security.ubuntu.com/ubuntu focal-security/main amd64 c-n-f Metadata [1352 B]
aws_instance.example[0] (remote-exec): 93% [7 Packages store 0 B] [Waiting for
aws_instance.example[0] (remote-exec): Get:32 http://security.ubuntu.com/ubuntu focal-security/restricted amd64 Packages [4180 B]
aws_instance.example[0] (remote-exec): 93% [7 Packages store 0 B] [32 Packages
aws_instance.example[0] (remote-exec): Get:33 http://security.ubuntu.com/ubuntu focal-security/restricted Translation-en [1360 B]
aws_instance.example[0] (remote-exec): 93% [7 Packages store 0 B] [33 Translat
aws_instance.example[0] (remote-exec): Get:34 http://security.ubuntu.com/ubuntu focal-security/universe amd64 Packages [7548 B]
aws_instance.example[0] (remote-exec): 93% [7 Packages store 0 B] [34 Packages
aws_instance.example[0] (remote-exec): Get:35 http://security.ubuntu.com/ubuntu focal-security/universe Translation-en [5636 B]
aws_instance.example[0] (remote-exec): 93% [7 Packages store 0 B] [35 Translat
aws_instance.example[0] (remote-exec): Get:36 http://security.ubuntu.com/ubuntu focal-security/universe amd64 c-n-f Metadata [608 B]
aws_instance.example[0] (remote-exec): Get:37 http://security.ubuntu.com/ubuntu focal-security/multiverse amd64 c-n-f Metadata [116 B]
aws_instance.example[0] (remote-exec): 93% [7 Packages store 0 B]
aws_instance.example[0] (remote-exec): 93% [7 Packages store 0 B]
aws_instance.example[0] (remote-exec): 93% [Working]
aws_instance.example[0] (remote-exec): 93% [9 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): 93% [9 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): 93% [Working]
aws_instance.example[0] (remote-exec): 93% [10 Commands-amd64 store 0 B]
aws_instance.example[0] (remote-exec): 94% [Working]
aws_instance.example[0] (remote-exec): 94% [11 Packages store 0 B]
aws_instance.example[0] (remote-exec): 94% [Working]
aws_instance.example[0] (remote-exec): 94% [12 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): 94% [Working]
aws_instance.example[0] (remote-exec): 94% [13 Commands-amd64 store 0 B]
aws_instance.example[0] (remote-exec): 94% [Working]
aws_instance.example[0] (remote-exec): 94% [14 Packages store 0 B]
aws_instance.example[0] (remote-exec): 95% [Working]
aws_instance.example[0] (remote-exec): 95% [15 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): 95% [Working]
aws_instance.example[0] (remote-exec): 95% [16 Commands-amd64 store 0 B]
aws_instance.example[0] (remote-exec): 95% [Working]
aws_instance.example[0] (remote-exec): 95% [17 Packages store 0 B]
aws_instance.example[0] (remote-exec): 95% [Working]
aws_instance.example[0] (remote-exec): 95% [18 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): 95% [Working]
aws_instance.example[0] (remote-exec): 95% [19 Packages store 0 B]
aws_instance.example[0] (remote-exec): 96% [Working]
aws_instance.example[0] (remote-exec): 96% [20 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): 96% [Working]
aws_instance.example[0] (remote-exec): 96% [21 Commands-amd64 store 0 B]
aws_instance.example[0] (remote-exec): 96% [Working]
aws_instance.example[0] (remote-exec): 96% [22 Commands-amd64 store 0 B]
aws_instance.example[0] (remote-exec): 96% [Working]
aws_instance.example[0] (remote-exec): 96% [23 Commands-amd64 store 0 B]
aws_instance.example[0] (remote-exec): 97% [Working]
aws_instance.example[0] (remote-exec): 97% [24 Commands-amd64 store 0 B]
aws_instance.example[0] (remote-exec): 97% [Working]
aws_instance.example[0] (remote-exec): 97% [25 Packages store 0 B]
aws_instance.example[0] (remote-exec): 97% [Working]
aws_instance.example[0] (remote-exec): 97% [26 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): 97% [Working]
aws_instance.example[0] (remote-exec): 97% [27 Commands-amd64 store 0 B]
aws_instance.example[0] (remote-exec): 98% [Working]
aws_instance.example[0] (remote-exec): 98% [28 Commands-amd64 store 0 B]
aws_instance.example[0] (remote-exec): 98% [Working]
aws_instance.example[0] (remote-exec): 98% [29 Packages store 0 B]
aws_instance.example[0] (remote-exec): 98% [Working]
aws_instance.example[0] (remote-exec): 98% [30 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): 98% [Working]
aws_instance.example[0] (remote-exec): 98% [31 Commands-amd64 store 0 B]
aws_instance.example[0] (remote-exec): 99% [Working]
aws_instance.example[0] (remote-exec): 99% [32 Packages store 0 B]
aws_instance.example[0] (remote-exec): 99% [Working]
aws_instance.example[0] (remote-exec): 99% [33 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): 99% [Working]
aws_instance.example[0] (remote-exec): 99% [34 Packages store 0 B]
aws_instance.example[0] (remote-exec): 99% [Working]
aws_instance.example[0] (remote-exec): 99% [35 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): 100% [Working]
aws_instance.example[0] (remote-exec): 100% [36 Commands-amd64 store 0 B]
aws_instance.example[0] (remote-exec): 100% [Working]
aws_instance.example[0] (remote-exec): 100% [37 Commands-amd64 store 0 B]
aws_instance.example[0] (remote-exec): 100% [Working]
aws_instance.example[0] (remote-exec): Fetched 16.6 MB in 3s (5967 kB/s)
aws_instance.example[2]: Still creating... [1m0s elapsed]
aws_instance.example[0]: Still creating... [1m0s elapsed]
aws_instance.example[1]: Still creating... [1m0s elapsed]
aws_instance.example[3]: Still creating... [1m0s elapsed]
aws_instance.example[1] (remote-exec): 0% [Working]
aws_instance.example[1] (remote-exec): Get:1 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal InRelease [265 kB]
aws_instance.example[1] (remote-exec): 0% [1 InRelease 0 B/265 kB 0%] [Connect
aws_instance.example[1] (remote-exec): 0% [Connecting to security.ubuntu.com (
aws_instance.example[1] (remote-exec): Get:2 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates InRelease [107 kB]

aws_instance.example[1] (remote-exec): Get:3 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports InRelease [98.3 kB]
aws_instance.example[1] (remote-exec): 0% [Connecting to security.ubuntu.com (
aws_instance.example[1] (remote-exec): 0% [Waiting for headers]
aws_instance.example[1] (remote-exec): Get:4 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 Packages [970 kB]
aws_instance.example[1] (remote-exec): 0% [4 Packages 47.6 kB/970 kB 5%] [Wait
aws_instance.example[1] (remote-exec): 0% [Waiting for headers]
aws_instance.example[1] (remote-exec): Get:5 http://security.ubuntu.com/ubuntu focal-security InRelease [107 kB]
aws_instance.example[1] (remote-exec): 0% [5 InRelease 5484 B/107 kB 5%]
aws_instance.example[1] (remote-exec): Get:6 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main Translation-en [506 kB]
aws_instance.example[1] (remote-exec): 0% [6 Translation-en 26.6 kB/506 kB 5%]
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B] [6 Translatio
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B] [5 InRelease
aws_instance.example[1] (remote-exec): Get:7 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 c-n-f Metadata [29.5 kB]
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B] [7 Commands-a
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B] [5 InRelease
aws_instance.example[1] (remote-exec): Get:8 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe amd64 Packages [8628 kB]
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B] [8 Packages 0
aws_instance.example[1] (remote-exec): Get:9 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe Translation-en [5124 kB]
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B] [9 Translatio
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B] [9 Translatio
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B] [9 Translatio
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:10 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe amd64 c-n-f Metadata [265 kB]
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B] [10 Commands-
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:11 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse amd64 Packages [144 kB]
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B] [11 Packages
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:12 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse Translation-en [104 kB]
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B] [12 Translati
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:13 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse amd64 c-n-f Metadata [9136 B]
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B] [13 Commands-
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:14 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [84.4 kB]
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B] [14 Packages
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:15 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main Translation-en [30.2 kB]
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B] [15 Translati
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:16 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main amd64 c-n-f Metadata [1940 B]
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B] [16 Commands-
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:17 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/restricted amd64 Packages [4180 B]
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B] [17 Packages
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:18 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/restricted Translation-en [1360 B]
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B] [18 Translati
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:19 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [27.2 kB]
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B] [19 Packages
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:20 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe Translation-en [13.3 kB]
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B] [20 Translati
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:21 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe amd64 c-n-f Metadata [1132 B]
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B] [21 Commands-
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:22 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 c-n-f Metadata [116 B]
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B] [22 Commands-
aws_instance.example[1] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[1] (remote-exec): 0% [Working]
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): 0% [Working]
aws_instance.example[1] (remote-exec): 0% [7 Commands-amd64 store 0 B]
aws_instance.example[1] (remote-exec): 0% [Working]
aws_instance.example[1] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[1] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:23 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/main amd64 c-n-f Metadata [112 B]
aws_instance.example[1] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:24 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/restricted amd64 c-n-f Metadata [116 B]
aws_instance.example[1] (remote-exec): Get:25 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe amd64 Packages [2792 B]
aws_instance.example[1] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[1] (remote-exec): Get:26 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe Translation-en [1280 B]
aws_instance.example[1] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[1] (remote-exec): Get:27 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe amd64 c-n-f Metadata [188 B]
aws_instance.example[1] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[1] (remote-exec): Get:28 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/multiverse amd64 c-n-f Metadata [116 B]
aws_instance.example[1] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[1] (remote-exec): 92% [8 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:29 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages [50.1 kB]
aws_instance.example[1] (remote-exec): 92% [8 Packages store 0 B] [29 Packages
aws_instance.example[1] (remote-exec): 93% [8 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:30 http://security.ubuntu.com/ubuntu focal-security/main Translation-en [18.5 kB]
aws_instance.example[1] (remote-exec): 93% [8 Packages store 0 B] [30 Translat
aws_instance.example[1] (remote-exec): Get:31 http://security.ubuntu.com/ubuntu focal-security/main amd64 c-n-f Metadata [1352 B]
aws_instance.example[1] (remote-exec): 93% [8 Packages store 0 B] [Waiting for
aws_instance.example[1] (remote-exec): Get:32 http://security.ubuntu.com/ubuntu focal-security/restricted amd64 Packages [4180 B]
aws_instance.example[1] (remote-exec): 93% [8 Packages store 0 B] [32 Packages
aws_instance.example[1] (remote-exec): Get:33 http://security.ubuntu.com/ubuntu focal-security/restricted Translation-en [1360 B]
aws_instance.example[1] (remote-exec): 93% [8 Packages store 0 B] [33 Translat
aws_instance.example[1] (remote-exec): Get:34 http://security.ubuntu.com/ubuntu focal-security/universe amd64 Packages [7548 B]
aws_instance.example[1] (remote-exec): 93% [8 Packages store 0 B] [34 Packages
aws_instance.example[1] (remote-exec): Get:35 http://security.ubuntu.com/ubuntu focal-security/universe Translation-en [5636 B]
aws_instance.example[1] (remote-exec): 93% [8 Packages store 0 B] [35 Translat
aws_instance.example[1] (remote-exec): Get:36 http://security.ubuntu.com/ubuntu focal-security/universe amd64 c-n-f Metadata [608 B]
aws_instance.example[1] (remote-exec): Get:37 http://security.ubuntu.com/ubuntu focal-security/multiverse amd64 c-n-f Metadata [116 B]
aws_instance.example[1] (remote-exec): 93% [8 Packages store 0 B]
aws_instance.example[1] (remote-exec): 93% [8 Packages store 0 B]
aws_instance.example[1] (remote-exec): 93% [Working]
aws_instance.example[1] (remote-exec): 93% [9 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): 0% [Working]
aws_instance.example[2] (remote-exec): Get:1 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal InRelease [265 kB]
aws_instance.example[2] (remote-exec): 0% [1 InRelease 0 B/265 kB 0%] [Connect
aws_instance.example[2] (remote-exec): 0% [Waiting for headers]
aws_instance.example[2] (remote-exec): Get:2 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates InRelease [107 kB]

aws_instance.example[1] (remote-exec): 93% [9 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): Get:3 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports InRelease [98.3 kB]
aws_instance.example[2] (remote-exec): 0% [Waiting for headers]
aws_instance.example[2] (remote-exec): 0% [Waiting for headers]
aws_instance.example[2] (remote-exec): Get:4 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 Packages [970 kB]
aws_instance.example[2] (remote-exec): 0% [4 Packages 47.6 kB/970 kB 5%] [Wait
aws_instance.example[2] (remote-exec): 0% [Waiting for headers]
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B] [Waiting for
aws_instance.example[2] (remote-exec): Get:5 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main Translation-en [506 kB]
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B] [5 Translatio
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B] [Waiting for
aws_instance.example[2] (remote-exec): Get:6 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 c-n-f Metadata [29.5 kB]
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B] [6 Commands-a
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B] [Waiting for
aws_instance.example[2] (remote-exec): Get:7 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe amd64 Packages [8628 kB]
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B] [7 Packages 0
aws_instance.example[2] (remote-exec): Get:8 http://security.ubuntu.com/ubuntu focal-security InRelease [107 kB]
aws_instance.example[1] (remote-exec): 93% [Working]
aws_instance.example[1] (remote-exec): 93% [10 Commands-amd64 store 0 B]
aws_instance.example[1] (remote-exec): 94% [Working]
aws_instance.example[1] (remote-exec): 94% [11 Packages store 0 B]
aws_instance.example[1] (remote-exec): 94% [Working]
aws_instance.example[1] (remote-exec): 94% [12 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): 94% [Working]
aws_instance.example[1] (remote-exec): 94% [13 Commands-amd64 store 0 B]
aws_instance.example[1] (remote-exec): 94% [Working]
aws_instance.example[1] (remote-exec): 94% [14 Packages store 0 B]
aws_instance.example[1] (remote-exec): 95% [Working]
aws_instance.example[1] (remote-exec): 95% [15 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): 95% [Working]
aws_instance.example[1] (remote-exec): 95% [16 Commands-amd64 store 0 B]
aws_instance.example[1] (remote-exec): 95% [Working]
aws_instance.example[1] (remote-exec): 95% [17 Packages store 0 B]
aws_instance.example[1] (remote-exec): 95% [Working]
aws_instance.example[1] (remote-exec): 95% [18 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): 95% [Working]
aws_instance.example[1] (remote-exec): 95% [19 Packages store 0 B]
aws_instance.example[1] (remote-exec): 96% [Working]
aws_instance.example[1] (remote-exec): 96% [20 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): 96% [Working]
aws_instance.example[1] (remote-exec): 96% [21 Commands-amd64 store 0 B]
aws_instance.example[1] (remote-exec): 96% [Working]
aws_instance.example[1] (remote-exec): 96% [22 Commands-amd64 store 0 B]
aws_instance.example[1] (remote-exec): 96% [Working]
aws_instance.example[1] (remote-exec): 96% [23 Commands-amd64 store 0 B]
aws_instance.example[1] (remote-exec): 97% [Working]
aws_instance.example[1] (remote-exec): 97% [24 Commands-amd64 store 0 B]
aws_instance.example[1] (remote-exec): 97% [Working]
aws_instance.example[1] (remote-exec): 97% [25 Packages store 0 B]
aws_instance.example[1] (remote-exec): 97% [Working]
aws_instance.example[1] (remote-exec): 97% [26 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): 97% [Working]
aws_instance.example[1] (remote-exec): 97% [27 Commands-amd64 store 0 B]
aws_instance.example[1] (remote-exec): 98% [Working]
aws_instance.example[1] (remote-exec): 98% [28 Commands-amd64 store 0 B]
aws_instance.example[1] (remote-exec): 98% [Working]
aws_instance.example[1] (remote-exec): 98% [29 Packages store 0 B]
aws_instance.example[1] (remote-exec): 98% [Working]
aws_instance.example[1] (remote-exec): 98% [30 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): 98% [Working]
aws_instance.example[1] (remote-exec): 98% [31 Commands-amd64 store 0 B]
aws_instance.example[1] (remote-exec): 99% [Working]
aws_instance.example[1] (remote-exec): 99% [32 Packages store 0 B]
aws_instance.example[1] (remote-exec): 99% [Working]
aws_instance.example[1] (remote-exec): 99% [33 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): 99% [Working]
aws_instance.example[1] (remote-exec): 99% [34 Packages store 0 B]
aws_instance.example[1] (remote-exec): 99% [Working]
aws_instance.example[1] (remote-exec): 99% [35 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): 100% [Working]
aws_instance.example[1] (remote-exec): 100% [36 Commands-amd64 store 0 B]
aws_instance.example[1] (remote-exec): 100% [Working]
aws_instance.example[1] (remote-exec): 100% [37 Commands-amd64 store 0 B]
aws_instance.example[1] (remote-exec): 100% [Working]
aws_instance.example[1] (remote-exec): Fetched 16.6 MB in 3s (5805 kB/s)
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B] [7 Packages 4
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B] [7 Packages 6
aws_instance.example[2] (remote-exec): Get:9 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe Translation-en [5124 kB]
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B] [9 Translatio
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B] [9 Translatio
aws_instance.example[2] (remote-exec): Get:10 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe amd64 c-n-f Metadata [265 kB]
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B] [10 Commands-
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:11 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse amd64 Packages [144 kB]
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B] [11 Packages
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:12 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse Translation-en [104 kB]
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B] [12 Translati
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:13 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse amd64 c-n-f Metadata [9136 B]
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B] [13 Commands-
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:14 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [84.4 kB]
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B] [14 Packages
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:15 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main Translation-en [30.2 kB]
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B] [15 Translati
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:16 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main amd64 c-n-f Metadata [1940 B]
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B] [16 Commands-
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:17 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/restricted amd64 Packages [4180 B]
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B] [17 Packages
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:18 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/restricted Translation-en [1360 B]
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B] [18 Translati
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:19 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [27.2 kB]
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B] [19 Packages
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:20 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe Translation-en [13.3 kB]
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B] [20 Translati
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:21 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe amd64 c-n-f Metadata [1132 B]
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B] [21 Commands-
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:22 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 c-n-f Metadata [116 B]
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B] [22 Commands-
aws_instance.example[2] (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example[2] (remote-exec): 0% [Working]
aws_instance.example[2] (remote-exec): 0% [5 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): Reading package lists... 0%
aws_instance.example[0] (remote-exec): Reading package lists... 0%
aws_instance.example[0] (remote-exec): Reading package lists... 0%
aws_instance.example[0] (remote-exec): Reading package lists... 6%
aws_instance.example[0] (remote-exec): Reading package lists... 6%
aws_instance.example[0] (remote-exec): Reading package lists... 9%
aws_instance.example[0] (remote-exec): Reading package lists... 9%
aws_instance.example[0] (remote-exec): Reading package lists... 10%
aws_instance.example[0] (remote-exec): Reading package lists... 10%
aws_instance.example[0] (remote-exec): Reading package lists... 10%
aws_instance.example[2] (remote-exec): 0% [Working]
aws_instance.example[2] (remote-exec): 0% [6 Commands-amd64 store 0 B]
aws_instance.example[2] (remote-exec): 0% [Working]
aws_instance.example[2] (remote-exec): 0% [7 Packages store 0 B]
aws_instance.example[2] (remote-exec): 0% [7 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:23 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/main amd64 c-n-f Metadata [112 B]
aws_instance.example[2] (remote-exec): 0% [7 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:24 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/restricted amd64 c-n-f Metadata [116 B]
aws_instance.example[2] (remote-exec): 0% [7 Packages store 0 B] [Waiting for
aws_instance.example[2] (remote-exec): Get:25 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe amd64 Packages [2792 B]
aws_instance.example[2] (remote-exec): 0% [7 Packages store 0 B] [Waiting for
aws_instance.example[2] (remote-exec): Get:26 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe Translation-en [1280 B]
aws_instance.example[2] (remote-exec): 0% [7 Packages store 0 B] [Waiting for
aws_instance.example[2] (remote-exec): Get:27 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe amd64 c-n-f Metadata [188 B]
aws_instance.example[2] (remote-exec): 0% [7 Packages store 0 B] [Waiting for
aws_instance.example[2] (remote-exec): Get:28 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/multiverse amd64 c-n-f Metadata [116 B]
aws_instance.example[3] (remote-exec): 0% [Working]
aws_instance.example[3] (remote-exec): Get:1 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal InRelease [265 kB]
aws_instance.example[2] (remote-exec): 0% [7 Packages store 0 B]
aws_instance.example[3] (remote-exec): 0% [1 InRelease 0 B/265 kB 0%] [Connect
aws_instance.example[3] (remote-exec): 0% [Connecting to security.ubuntu.com (
aws_instance.example[3] (remote-exec): Get:2 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates InRelease [107 kB]
aws_instance.example[0] (remote-exec): Reading package lists... 10%
aws_instance.example[2] (remote-exec): 92% [7 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:29 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages [50.1 kB]
aws_instance.example[2] (remote-exec): 92% [7 Packages store 0 B] [29 Packages
aws_instance.example[2] (remote-exec): 93% [7 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:30 http://security.ubuntu.com/ubuntu focal-security/main Translation-en [18.5 kB]
aws_instance.example[2] (remote-exec): 93% [7 Packages store 0 B] [30 Translat
aws_instance.example[2] (remote-exec): Get:31 http://security.ubuntu.com/ubuntu focal-security/main amd64 c-n-f Metadata [1352 B]
aws_instance.example[2] (remote-exec): Get:32 http://security.ubuntu.com/ubuntu focal-security/restricted amd64 Packages [4180 B]
aws_instance.example[2] (remote-exec): Get:33 http://security.ubuntu.com/ubuntu focal-security/restricted Translation-en [1360 B]
aws_instance.example[2] (remote-exec): Get:34 http://security.ubuntu.com/ubuntu focal-security/universe amd64 Packages [7548 B]
aws_instance.example[2] (remote-exec): 93% [7 Packages store 0 B] [34 Packages
aws_instance.example[2] (remote-exec): Get:35 http://security.ubuntu.com/ubuntu focal-security/universe Translation-en [5636 B]
aws_instance.example[2] (remote-exec): Get:36 http://security.ubuntu.com/ubuntu focal-security/universe amd64 c-n-f Metadata [608 B]
aws_instance.example[2] (remote-exec): Get:37 http://security.ubuntu.com/ubuntu focal-security/multiverse amd64 c-n-f Metadata [116 B]
aws_instance.example[2] (remote-exec): 93% [7 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:3 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports InRelease [98.3 kB]
aws_instance.example[3] (remote-exec): 0% [Waiting for headers]
aws_instance.example[3] (remote-exec): Get:4 http://security.ubuntu.com/ubuntu focal-security InRelease [107 kB]
aws_instance.example[3] (remote-exec): 0% [4 InRelease 2588 B/107 kB 2%]
aws_instance.example[3] (remote-exec): 0% [4 InRelease 59.1 kB/107 kB 55%]
aws_instance.example[3] (remote-exec): Get:5 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 Packages [970 kB]
aws_instance.example[3] (remote-exec): 0% [5 Packages 26.6 kB/970 kB 3%] [4 In
aws_instance.example[3] (remote-exec): 0% [5 Packages 232 kB/970 kB 24%]
aws_instance.example[3] (remote-exec): 0% [Working]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [Waiting for
aws_instance.example[3] (remote-exec): Get:6 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main Translation-en [506 kB]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [6 Translatio
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:7 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 c-n-f Metadata [29.5 kB]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [7 Commands-a
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:8 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe amd64 Packages [8628 kB]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [8 Packages 0
aws_instance.example[3] (remote-exec): Get:9 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe Translation-en [5124 kB]
aws_instance.example[0] (remote-exec): Reading package lists... 66%
aws_instance.example[0] (remote-exec): Reading package lists... 66%
aws_instance.example[0] (remote-exec): Reading package lists... 96%
aws_instance.example[0] (remote-exec): Reading package lists... 96%
aws_instance.example[0] (remote-exec): Reading package lists... 97%
aws_instance.example[0] (remote-exec): Reading package lists... 97%
aws_instance.example[0] (remote-exec): Reading package lists... 97%
aws_instance.example[0] (remote-exec): Reading package lists... 97%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 99%
aws_instance.example[0] (remote-exec): Reading package lists... 99%
aws_instance.example[0] (remote-exec): Reading package lists... 99%
aws_instance.example[0] (remote-exec): Reading package lists... 99%
aws_instance.example[0] (remote-exec): Reading package lists... 99%
aws_instance.example[0] (remote-exec): Reading package lists... 99%
aws_instance.example[0] (remote-exec): Reading package lists... 99%
aws_instance.example[0] (remote-exec): Reading package lists... 99%
aws_instance.example[0] (remote-exec): Reading package lists... 99%
aws_instance.example[0] (remote-exec): Reading package lists... 99%
aws_instance.example[0] (remote-exec): Reading package lists... 99%
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [9 Translatio
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [9 Translatio
aws_instance.example[3] (remote-exec): Get:10 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe amd64 c-n-f Metadata [265 kB]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [10 Commands-
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:11 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse amd64 Packages [144 kB]
aws_instance.example[0] (remote-exec): Reading package lists... 99%
aws_instance.example[0] (remote-exec): Reading package lists... Done
aws_instance.example[0] (remote-exec): Reading package lists... 0%
aws_instance.example[0] (remote-exec): Reading package lists... 100%
aws_instance.example[0] (remote-exec): Reading package lists... Done
aws_instance.example[0] (remote-exec): Building dependency tree... 0%
aws_instance.example[0] (remote-exec): Building dependency tree... 0%
aws_instance.example[0] (remote-exec): Building dependency tree... 50%
aws_instance.example[0] (remote-exec): Building dependency tree... 50%
aws_instance.example[0] (remote-exec): Building dependency tree
aws_instance.example[0] (remote-exec): Reading state information... 0%
aws_instance.example[0] (remote-exec): Reading state information... 0%
aws_instance.example[0] (remote-exec): Reading state information... Done
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [11 Packages
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:12 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse Translation-en [104 kB]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [12 Translati
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:13 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse amd64 c-n-f Metadata [9136 B]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [13 Commands-
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:14 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [84.4 kB]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [14 Packages
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:15 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main Translation-en [30.2 kB]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [15 Translati
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:16 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main amd64 c-n-f Metadata [1940 B]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [16 Commands-
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:17 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/restricted amd64 Packages [4180 B]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [17 Packages
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:18 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/restricted Translation-en [1360 B]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [18 Translati
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:19 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [27.2 kB]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [19 Packages
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:20 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe Translation-en [13.3 kB]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [20 Translati
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:21 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe amd64 c-n-f Metadata [1132 B]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [21 Commands-
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:22 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 c-n-f Metadata [116 B]
aws_instance.example[0] (remote-exec): The following additional packages will be installed:
aws_instance.example[0] (remote-exec):   fontconfig-config fonts-dejavu-core
aws_instance.example[0] (remote-exec):   libfontconfig1 libgd3 libjbig0
aws_instance.example[0] (remote-exec):   libjpeg-turbo8 libjpeg8
aws_instance.example[0] (remote-exec):   libnginx-mod-http-image-filter
aws_instance.example[0] (remote-exec):   libnginx-mod-http-xslt-filter
aws_instance.example[0] (remote-exec):   libnginx-mod-mail
aws_instance.example[0] (remote-exec):   libnginx-mod-stream libtiff5
aws_instance.example[0] (remote-exec):   libwebp6 libxpm4 nginx-common
aws_instance.example[0] (remote-exec):   nginx-core
aws_instance.example[0] (remote-exec): Suggested packages:
aws_instance.example[0] (remote-exec):   libgd-tools fcgiwrap nginx-doc
aws_instance.example[0] (remote-exec):   ssl-cert
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [22 Commands-
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[3] (remote-exec): 0% [Working]
aws_instance.example[3] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[3] (remote-exec): 0% [Working]
aws_instance.example[3] (remote-exec): 0% [7 Commands-amd64 store 0 B]
aws_instance.example[3] (remote-exec): 0% [Working]
aws_instance.example[3] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[3] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:23 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/main amd64 c-n-f Metadata [112 B]
aws_instance.example[3] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:24 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/restricted amd64 c-n-f Metadata [116 B]
aws_instance.example[2] (remote-exec): 93% [7 Packages store 0 B]
aws_instance.example[0] (remote-exec): The following NEW packages will be installed:
aws_instance.example[0] (remote-exec):   fontconfig-config fonts-dejavu-core
aws_instance.example[0] (remote-exec):   libfontconfig1 libgd3 libjbig0
aws_instance.example[0] (remote-exec):   libjpeg-turbo8 libjpeg8
aws_instance.example[0] (remote-exec):   libnginx-mod-http-image-filter
aws_instance.example[0] (remote-exec):   libnginx-mod-http-xslt-filter
aws_instance.example[0] (remote-exec):   libnginx-mod-mail
aws_instance.example[0] (remote-exec):   libnginx-mod-stream libtiff5
aws_instance.example[0] (remote-exec):   libwebp6 libxpm4 nginx nginx-common
aws_instance.example[3] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[3] (remote-exec): Get:25 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe amd64 Packages [2792 B]
aws_instance.example[3] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[3] (remote-exec): Get:26 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe Translation-en [1280 B]
aws_instance.example[3] (remote-exec): 0% [8 Packages store 0 B] [26 Translati
aws_instance.example[3] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[3] (remote-exec): Get:27 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe amd64 c-n-f Metadata [188 B]
aws_instance.example[3] (remote-exec): Get:28 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/multiverse amd64 c-n-f Metadata [116 B]
aws_instance.example[0] (remote-exec):   nginx-core
aws_instance.example[0] (remote-exec): 0 upgraded, 17 newly installed, 0 to remove and 21 not upgraded.
aws_instance.example[0] (remote-exec): Need to get 2431 kB of archives.
aws_instance.example[0] (remote-exec): After this operation, 7891 kB of additional disk space will be used.
aws_instance.example[0] (remote-exec): 0% [Working]
aws_instance.example[0] (remote-exec): Get:1 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 fonts-dejavu-core all 2.37-1 [1041 kB]
aws_instance.example[0] (remote-exec): 0% [1 fonts-dejavu-core 0 B/1041 kB 0%]
aws_instance.example[0] (remote-exec): 35% [Working]
aws_instance.example[0] (remote-exec): Get:2 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 fontconfig-config all 2.13.1-2ubuntu3 [28.8 kB]
aws_instance.example[3] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[0] (remote-exec): 35% [2 fontconfig-config 0 B/28.8 kB 0%
aws_instance.example[0] (remote-exec): 38% [Working]
aws_instance.example[0] (remote-exec): Get:3 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libfontconfig1 amd64 2.13.1-2ubuntu3 [114 kB]
aws_instance.example[0] (remote-exec): 38% [3 libfontconfig1 0 B/114 kB 0%]
aws_instance.example[0] (remote-exec): 42% [Working]
aws_instance.example[0] (remote-exec): Get:4 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjpeg-turbo8 amd64 2.0.3-0ubuntu1 [118 kB]
aws_instance.example[0] (remote-exec): 42% [4 libjpeg-turbo8 0 B/118 kB 0%]
aws_instance.example[0] (remote-exec): 48% [Working]
aws_instance.example[0] (remote-exec): Get:5 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjpeg8 amd64 8c-2ubuntu8 [2194 B]
aws_instance.example[0] (remote-exec): 48% [5 libjpeg8 0 B/2194 B 0%]
aws_instance.example[0] (remote-exec): 49% [Working]
aws_instance.example[0] (remote-exec): Get:6 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjbig0 amd64 2.1-3.1build1 [26.7 kB]
aws_instance.example[0] (remote-exec): 49% [6 libjbig0 0 B/26.7 kB 0%]
aws_instance.example[0] (remote-exec): 51% [Working]
aws_instance.example[0] (remote-exec): Get:7 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libwebp6 amd64 0.6.1-2 [185 kB]
aws_instance.example[0] (remote-exec): 51% [7 libwebp6 0 B/185 kB 0%]
aws_instance.example[0] (remote-exec): 58% [Working]
aws_instance.example[0] (remote-exec): Get:8 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libtiff5 amd64 4.1.0+git191117-2build1 [161 kB]
aws_instance.example[0] (remote-exec): 58% [8 libtiff5 0 B/161 kB 0%]
aws_instance.example[0] (remote-exec): 65% [Working]
aws_instance.example[0] (remote-exec): Get:9 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libxpm4 amd64 1:3.5.12-1 [34.0 kB]
aws_instance.example[0] (remote-exec): 65% [9 libxpm4 0 B/34.0 kB 0%]
aws_instance.example[0] (remote-exec): 67% [Working]
aws_instance.example[0] (remote-exec): Get:10 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libgd3 amd64 2.2.5-5.2ubuntu2 [118 kB]
aws_instance.example[0] (remote-exec): 67% [10 libgd3 0 B/118 kB 0%]
aws_instance.example[0] (remote-exec): 72% [Working]
aws_instance.example[0] (remote-exec): Get:11 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx-common all 1.17.10-0ubuntu1 [37.3 kB]
aws_instance.example[0] (remote-exec): 72% [11 nginx-common 0 B/37.3 kB 0%]
aws_instance.example[0] (remote-exec): 74% [Working]
aws_instance.example[0] (remote-exec): Get:12 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-http-image-filter amd64 1.17.10-0ubuntu1 [14.3 kB]
aws_instance.example[0] (remote-exec): 74% [12 libnginx-mod-http-image-filter
aws_instance.example[0] (remote-exec): 76% [Working]
aws_instance.example[0] (remote-exec): Get:13 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-http-xslt-filter amd64 1.17.10-0ubuntu1 [12.5 kB]
aws_instance.example[0] (remote-exec): 76% [13 libnginx-mod-http-xslt-filter 0
aws_instance.example[0] (remote-exec): 78% [Working]
aws_instance.example[0] (remote-exec): Get:14 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-mail amd64 1.17.10-0ubuntu1 [42.3 kB]
aws_instance.example[0] (remote-exec): 78% [14 libnginx-mod-mail 0 B/42.3 kB 0
aws_instance.example[0] (remote-exec): 80% [Working]
aws_instance.example[0] (remote-exec): Get:15 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-stream amd64 1.17.10-0ubuntu1 [66.9 kB]
aws_instance.example[0] (remote-exec): 80% [15 libnginx-mod-stream 0 B/66.9 kB
aws_instance.example[0] (remote-exec): 84% [Working]
aws_instance.example[0] (remote-exec): Get:16 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx-core amd64 1.17.10-0ubuntu1 [425 kB]
aws_instance.example[0] (remote-exec): 84% [16 nginx-core 0 B/425 kB 0%]
aws_instance.example[0] (remote-exec): 99% [Working]
aws_instance.example[0] (remote-exec): Get:17 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx all 1.17.10-0ubuntu1 [3616 B]
aws_instance.example[0] (remote-exec): 99% [17 nginx 0 B/3616 B 0%]
aws_instance.example[0] (remote-exec): 100% [Working]
aws_instance.example[0] (remote-exec): Fetched 2431 kB in 0s (36.2 MB/s)
aws_instance.example[3] (remote-exec): 92% [8 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:29 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages [50.1 kB]
aws_instance.example[3] (remote-exec): 92% [8 Packages store 0 B] [29 Packages
aws_instance.example[3] (remote-exec): 93% [8 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:30 http://security.ubuntu.com/ubuntu focal-security/main Translation-en [18.5 kB]
aws_instance.example[3] (remote-exec): 93% [8 Packages store 0 B] [30 Translat
aws_instance.example[3] (remote-exec): Get:31 http://security.ubuntu.com/ubuntu focal-security/main amd64 c-n-f Metadata [1352 B]
aws_instance.example[3] (remote-exec): Get:32 http://security.ubuntu.com/ubuntu focal-security/restricted amd64 Packages [4180 B]
aws_instance.example[3] (remote-exec): 93% [8 Packages store 0 B] [32 Packages
aws_instance.example[3] (remote-exec): Get:33 http://security.ubuntu.com/ubuntu focal-security/restricted Translation-en [1360 B]
aws_instance.example[3] (remote-exec): Get:34 http://security.ubuntu.com/ubuntu focal-security/universe amd64 Packages [7548 B]
aws_instance.example[3] (remote-exec): Get:35 http://security.ubuntu.com/ubuntu focal-security/universe Translation-en [5636 B]
aws_instance.example[3] (remote-exec): Get:36 http://security.ubuntu.com/ubuntu focal-security/universe amd64 c-n-f Metadata [608 B]
aws_instance.example[3] (remote-exec): Get:37 http://security.ubuntu.com/ubuntu focal-security/multiverse amd64 c-n-f Metadata [116 B]
aws_instance.example[0] (remote-exec): Preconfiguring packages ...
aws_instance.example[3] (remote-exec): 93% [8 Packages store 0 B]
aws_instance.example[2] (remote-exec): 93% [Working]
aws_instance.example[2] (remote-exec): 93% [9 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): Selecting previously unselected package fonts-dejavu-core.
aws_instance.example[0] (remote-exec): (Reading database ...
aws_instance.example[0] (remote-exec): (Reading database ... 5%
aws_instance.example[0] (remote-exec): (Reading database ... 10%
aws_instance.example[0] (remote-exec): (Reading database ... 15%
aws_instance.example[0] (remote-exec): (Reading database ... 20%
aws_instance.example[0] (remote-exec): (Reading database ... 25%
aws_instance.example[0] (remote-exec): (Reading database ... 30%
aws_instance.example[0] (remote-exec): (Reading database ... 35%
aws_instance.example[0] (remote-exec): (Reading database ... 40%
aws_instance.example[0] (remote-exec): (Reading database ... 45%
aws_instance.example[0] (remote-exec): (Reading database ... 50%
aws_instance.example[0] (remote-exec): (Reading database ... 55%
aws_instance.example[0] (remote-exec): (Reading database ... 60%
aws_instance.example[0] (remote-exec): (Reading database ... 65%
aws_instance.example[0] (remote-exec): (Reading database ... 70%
aws_instance.example[0] (remote-exec): (Reading database ... 75%
aws_instance.example[0] (remote-exec): (Reading database ... 80%
aws_instance.example[0] (remote-exec): (Reading database ... 85%
aws_instance.example[0] (remote-exec): (Reading database ... 90%
aws_instance.example[0] (remote-exec): (Reading database ... 95%
aws_instance.example[0] (remote-exec): (Reading database ... 100%
aws_instance.example[0] (remote-exec): (Reading database ... 59604 files and directories currently installed.)
aws_instance.example[0] (remote-exec): Preparing to unpack .../00-fonts-dejavu-core_2.37-1_all.deb ...
aws_instance.example[0] (remote-exec): Unpacking fonts-dejavu-core (2.37-1) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package fontconfig-config.
aws_instance.example[0] (remote-exec): Preparing to unpack .../01-fontconfig-config_2.13.1-2ubuntu3_all.deb ...
aws_instance.example[0] (remote-exec): Unpacking fontconfig-config (2.13.1-2ubuntu3) ...
aws_instance.example[3] (remote-exec): 93% [8 Packages store 0 B]
aws_instance.example[2] (remote-exec): 93% [9 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): Selecting previously unselected package libfontconfig1:amd64.
aws_instance.example[0] (remote-exec): Preparing to unpack .../02-libfontconfig1_2.13.1-2ubuntu3_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libfontconfig1:amd64 (2.13.1-2ubuntu3) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package libjpeg-turbo8:amd64.
aws_instance.example[0] (remote-exec): Preparing to unpack .../03-libjpeg-turbo8_2.0.3-0ubuntu1_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libjpeg-turbo8:amd64 (2.0.3-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package libjpeg8:amd64.
aws_instance.example[0] (remote-exec): Preparing to unpack .../04-libjpeg8_8c-2ubuntu8_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libjpeg8:amd64 (8c-2ubuntu8) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package libjbig0:amd64.
aws_instance.example[0] (remote-exec): Preparing to unpack .../05-libjbig0_2.1-3.1build1_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libjbig0:amd64 (2.1-3.1build1) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package libwebp6:amd64.
aws_instance.example[0] (remote-exec): Preparing to unpack .../06-libwebp6_0.6.1-2_amd64.deb ...
aws_instance.example[2] (remote-exec): 93% [Working]
aws_instance.example[2] (remote-exec): 93% [10 Commands-amd64 store 0 B]
aws_instance.example[2] (remote-exec): 94% [Working]
aws_instance.example[2] (remote-exec): 94% [11 Packages store 0 B]
aws_instance.example[2] (remote-exec): 94% [Working]
aws_instance.example[2] (remote-exec): 94% [12 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): 94% [Working]
aws_instance.example[2] (remote-exec): 94% [13 Commands-amd64 store 0 B]
aws_instance.example[2] (remote-exec): 94% [Working]
aws_instance.example[2] (remote-exec): 94% [14 Packages store 0 B]
aws_instance.example[2] (remote-exec): 95% [Working]
aws_instance.example[2] (remote-exec): 95% [15 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): 95% [Working]
aws_instance.example[2] (remote-exec): 95% [16 Commands-amd64 store 0 B]
aws_instance.example[2] (remote-exec): 95% [Working]
aws_instance.example[2] (remote-exec): 95% [17 Packages store 0 B]
aws_instance.example[2] (remote-exec): 95% [Working]
aws_instance.example[2] (remote-exec): 95% [18 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): 95% [Working]
aws_instance.example[2] (remote-exec): 95% [19 Packages store 0 B]
aws_instance.example[2] (remote-exec): 96% [Working]
aws_instance.example[2] (remote-exec): 96% [20 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): 96% [Working]
aws_instance.example[2] (remote-exec): 96% [21 Commands-amd64 store 0 B]
aws_instance.example[2] (remote-exec): 96% [Working]
aws_instance.example[2] (remote-exec): 96% [22 Commands-amd64 store 0 B]
aws_instance.example[2] (remote-exec): 96% [Working]
aws_instance.example[0] (remote-exec): Unpacking libwebp6:amd64 (0.6.1-2) ...
aws_instance.example[3] (remote-exec): 93% [Working]
aws_instance.example[3] (remote-exec): 93% [9 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): 96% [23 Commands-amd64 store 0 B]
aws_instance.example[2] (remote-exec): 97% [Working]
aws_instance.example[2] (remote-exec): 97% [24 Commands-amd64 store 0 B]
aws_instance.example[2] (remote-exec): 97% [Working]
aws_instance.example[2] (remote-exec): 97% [25 Packages store 0 B]
aws_instance.example[2] (remote-exec): 97% [Working]
aws_instance.example[2] (remote-exec): 97% [26 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): 97% [Working]
aws_instance.example[2] (remote-exec): 97% [27 Commands-amd64 store 0 B]
aws_instance.example[2] (remote-exec): 98% [Working]
aws_instance.example[2] (remote-exec): 98% [28 Commands-amd64 store 0 B]
aws_instance.example[2] (remote-exec): 98% [Working]
aws_instance.example[2] (remote-exec): 98% [29 Packages store 0 B]
aws_instance.example[2] (remote-exec): 98% [Working]
aws_instance.example[2] (remote-exec): 98% [30 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): 98% [Working]
aws_instance.example[2] (remote-exec): 98% [31 Commands-amd64 store 0 B]
aws_instance.example[2] (remote-exec): 99% [Working]
aws_instance.example[2] (remote-exec): 99% [32 Packages store 0 B]
aws_instance.example[2] (remote-exec): 99% [Working]
aws_instance.example[2] (remote-exec): 99% [33 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): 99% [Working]
aws_instance.example[2] (remote-exec): 99% [34 Packages store 0 B]
aws_instance.example[2] (remote-exec): 99% [Working]
aws_instance.example[2] (remote-exec): 99% [35 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): 100% [Working]
aws_instance.example[2] (remote-exec): 100% [36 Commands-amd64 store 0 B]
aws_instance.example[2] (remote-exec): 100% [Working]
aws_instance.example[2] (remote-exec): 100% [37 Commands-amd64 store 0 B]
aws_instance.example[2] (remote-exec): 100% [Working]
aws_instance.example[2] (remote-exec): Fetched 16.6 MB in 3s (5783 kB/s)
aws_instance.example[0] (remote-exec): Selecting previously unselected package libtiff5:amd64.
aws_instance.example[0] (remote-exec): Preparing to unpack .../07-libtiff5_4.1.0+git191117-2build1_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libtiff5:amd64 (4.1.0+git191117-2build1) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package libxpm4:amd64.
aws_instance.example[0] (remote-exec): Preparing to unpack .../08-libxpm4_1%3a3.5.12-1_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libxpm4:amd64 (1:3.5.12-1) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package libgd3:amd64.
aws_instance.example[0] (remote-exec): Preparing to unpack .../09-libgd3_2.2.5-5.2ubuntu2_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libgd3:amd64 (2.2.5-5.2ubuntu2) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package nginx-common.
aws_instance.example[0] (remote-exec): Preparing to unpack .../10-nginx-common_1.17.10-0ubuntu1_all.deb ...
aws_instance.example[0] (remote-exec): Unpacking nginx-common (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package libnginx-mod-http-image-filter.
aws_instance.example[0] (remote-exec): Preparing to unpack .../11-libnginx-mod-http-image-filter_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libnginx-mod-http-image-filter (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package libnginx-mod-http-xslt-filter.
aws_instance.example[0] (remote-exec): Preparing to unpack .../12-libnginx-mod-http-xslt-filter_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libnginx-mod-http-xslt-filter (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package libnginx-mod-mail.
aws_instance.example[0] (remote-exec): Preparing to unpack .../13-libnginx-mod-mail_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libnginx-mod-mail (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package libnginx-mod-stream.
aws_instance.example[0] (remote-exec): Preparing to unpack .../14-libnginx-mod-stream_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libnginx-mod-stream (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package nginx-core.
aws_instance.example[0] (remote-exec): Preparing to unpack .../15-nginx-core_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking nginx-core (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package nginx.
aws_instance.example[0] (remote-exec): Preparing to unpack .../16-nginx_1.17.10-0ubuntu1_all.deb ...
aws_instance.example[0] (remote-exec): Unpacking nginx (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): 93% [9 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): Setting up libxpm4:amd64 (1:3.5.12-1) ...
aws_instance.example[0] (remote-exec): Setting up nginx-common (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): 93% [Working]
aws_instance.example[3] (remote-exec): 93% [10 Commands-amd64 store 0 B]
aws_instance.example[3] (remote-exec): 94% [Working]
aws_instance.example[3] (remote-exec): 94% [11 Packages store 0 B]
aws_instance.example[3] (remote-exec): 94% [Working]
aws_instance.example[3] (remote-exec): 94% [12 Translation-en store 0 B]
aws_instance.example[3] (remote-exec): 94% [Working]
aws_instance.example[3] (remote-exec): 94% [13 Commands-amd64 store 0 B]
aws_instance.example[3] (remote-exec): 94% [Working]
aws_instance.example[3] (remote-exec): 94% [14 Packages store 0 B]
aws_instance.example[3] (remote-exec): 95% [Working]
aws_instance.example[3] (remote-exec): 95% [15 Translation-en store 0 B]
aws_instance.example[3] (remote-exec): 95% [Working]
aws_instance.example[3] (remote-exec): 95% [16 Commands-amd64 store 0 B]
aws_instance.example[3] (remote-exec): 95% [Working]
aws_instance.example[3] (remote-exec): 95% [17 Packages store 0 B]
aws_instance.example[3] (remote-exec): 95% [Working]
aws_instance.example[3] (remote-exec): 95% [18 Translation-en store 0 B]
aws_instance.example[3] (remote-exec): 95% [Working]
aws_instance.example[3] (remote-exec): 95% [19 Packages store 0 B]
aws_instance.example[3] (remote-exec): 96% [Working]
aws_instance.example[3] (remote-exec): 96% [20 Translation-en store 0 B]
aws_instance.example[3] (remote-exec): 96% [Working]
aws_instance.example[3] (remote-exec): 96% [21 Commands-amd64 store 0 B]
aws_instance.example[3] (remote-exec): 96% [Working]
aws_instance.example[3] (remote-exec): 96% [22 Commands-amd64 store 0 B]
aws_instance.example[3] (remote-exec): 96% [Working]
aws_instance.example[3] (remote-exec): 96% [23 Commands-amd64 store 0 B]
aws_instance.example[3] (remote-exec): 97% [Working]
aws_instance.example[3] (remote-exec): 97% [24 Commands-amd64 store 0 B]
aws_instance.example[3] (remote-exec): 97% [Working]
aws_instance.example[3] (remote-exec): 97% [25 Packages store 0 B]
aws_instance.example[0] (remote-exec): Created symlink /etc/systemd/system/multi-user.target.wants/nginx.service → /lib/systemd/system/nginx.service.
aws_instance.example[3] (remote-exec): 97% [Working]
aws_instance.example[3] (remote-exec): 97% [26 Translation-en store 0 B]
aws_instance.example[3] (remote-exec): 97% [Working]
aws_instance.example[3] (remote-exec): 97% [27 Commands-amd64 store 0 B]
aws_instance.example[3] (remote-exec): 98% [Working]
aws_instance.example[3] (remote-exec): 98% [28 Commands-amd64 store 0 B]
aws_instance.example[3] (remote-exec): 98% [Working]
aws_instance.example[3] (remote-exec): 98% [29 Packages store 0 B]
aws_instance.example[3] (remote-exec): 98% [Working]
aws_instance.example[3] (remote-exec): 98% [30 Translation-en store 0 B]
aws_instance.example[3] (remote-exec): 98% [Working]
aws_instance.example[3] (remote-exec): 98% [31 Commands-amd64 store 0 B]
aws_instance.example[3] (remote-exec): 99% [Working]
aws_instance.example[3] (remote-exec): 99% [32 Packages store 0 B]
aws_instance.example[3] (remote-exec): 99% [Working]
aws_instance.example[3] (remote-exec): 99% [33 Translation-en store 0 B]
aws_instance.example[3] (remote-exec): 99% [Working]
aws_instance.example[3] (remote-exec): 99% [34 Packages store 0 B]
aws_instance.example[3] (remote-exec): 99% [Working]
aws_instance.example[3] (remote-exec): 99% [35 Translation-en store 0 B]
aws_instance.example[3] (remote-exec): 100% [Working]
aws_instance.example[3] (remote-exec): 100% [36 Commands-amd64 store 0 B]
aws_instance.example[3] (remote-exec): 100% [Working]
aws_instance.example[3] (remote-exec): 100% [37 Commands-amd64 store 0 B]
aws_instance.example[3] (remote-exec): 100% [Working]
aws_instance.example[3] (remote-exec): Fetched 16.6 MB in 3s (5831 kB/s)
aws_instance.example[0] (remote-exec): Setting up libjbig0:amd64 (2.1-3.1build1) ...
aws_instance.example[0] (remote-exec): Setting up libnginx-mod-http-xslt-filter (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Setting up libwebp6:amd64 (0.6.1-2) ...
aws_instance.example[0] (remote-exec): Setting up fonts-dejavu-core (2.37-1) ...
aws_instance.example[0] (remote-exec): Setting up libjpeg-turbo8:amd64 (2.0.3-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Setting up libjpeg8:amd64 (8c-2ubuntu8) ...
aws_instance.example[0] (remote-exec): Setting up libnginx-mod-mail (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Setting up fontconfig-config (2.13.1-2ubuntu3) ...
aws_instance.example[1] (remote-exec): Reading package lists... 0%
aws_instance.example[1] (remote-exec): Reading package lists... 0%
aws_instance.example[1] (remote-exec): Reading package lists... 0%
aws_instance.example[1] (remote-exec): Reading package lists... 6%
aws_instance.example[1] (remote-exec): Reading package lists... 6%
aws_instance.example[1] (remote-exec): Reading package lists... 9%
aws_instance.example[1] (remote-exec): Reading package lists... 9%
aws_instance.example[1] (remote-exec): Reading package lists... 10%
aws_instance.example[1] (remote-exec): Reading package lists... 10%
aws_instance.example[1] (remote-exec): Reading package lists... 10%
aws_instance.example[0] (remote-exec): Setting up libnginx-mod-stream (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Setting up libtiff5:amd64 (4.1.0+git191117-2build1) ...
aws_instance.example[0] (remote-exec): Setting up libfontconfig1:amd64 (2.13.1-2ubuntu3) ...
aws_instance.example[0] (remote-exec): Setting up libgd3:amd64 (2.2.5-5.2ubuntu2) ...
aws_instance.example[0] (remote-exec): Setting up libnginx-mod-http-image-filter (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Setting up nginx-core (1.17.10-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Reading package lists... 10%
aws_instance.example[0] (remote-exec): Setting up nginx (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Processing triggers for ufw (0.36-6) ...
aws_instance.example[1] (remote-exec): Reading package lists... 66%
aws_instance.example[1] (remote-exec): Reading package lists... 66%
aws_instance.example[1] (remote-exec): Reading package lists... 96%
aws_instance.example[1] (remote-exec): Reading package lists... 96%
aws_instance.example[1] (remote-exec): Reading package lists... 97%
aws_instance.example[1] (remote-exec): Reading package lists... 97%
aws_instance.example[1] (remote-exec): Reading package lists... 97%
aws_instance.example[1] (remote-exec): Reading package lists... 97%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 99%
aws_instance.example[1] (remote-exec): Reading package lists... 99%
aws_instance.example[1] (remote-exec): Reading package lists... 99%
aws_instance.example[1] (remote-exec): Reading package lists... 99%
aws_instance.example[1] (remote-exec): Reading package lists... 99%
aws_instance.example[1] (remote-exec): Reading package lists... 99%
aws_instance.example[1] (remote-exec): Reading package lists... 99%
aws_instance.example[1] (remote-exec): Reading package lists... 99%
aws_instance.example[1] (remote-exec): Reading package lists... 99%
aws_instance.example[1] (remote-exec): Reading package lists... 99%
aws_instance.example[1] (remote-exec): Reading package lists... 99%
aws_instance.example[1] (remote-exec): Reading package lists... 99%
aws_instance.example[1] (remote-exec): Reading package lists... Done
aws_instance.example[0] (remote-exec): Processing triggers for systemd (245.4-4ubuntu3) ...
aws_instance.example[1] (remote-exec): Reading package lists... 0%
aws_instance.example[1] (remote-exec): Reading package lists... 100%
aws_instance.example[1] (remote-exec): Reading package lists... Done
aws_instance.example[1] (remote-exec): Building dependency tree... 0%
aws_instance.example[1] (remote-exec): Building dependency tree... 0%
aws_instance.example[1] (remote-exec): Building dependency tree... 50%
aws_instance.example[1] (remote-exec): Building dependency tree... 50%
aws_instance.example[1] (remote-exec): Building dependency tree
aws_instance.example[1] (remote-exec): Reading state information... 0%
aws_instance.example[1] (remote-exec): Reading state information... 0%
aws_instance.example[1] (remote-exec): Reading state information... Done
aws_instance.example[0] (remote-exec): Processing triggers for man-db (2.9.1-1) ...
aws_instance.example[1] (remote-exec): The following additional packages will be installed:
aws_instance.example[1] (remote-exec):   fontconfig-config fonts-dejavu-core
aws_instance.example[1] (remote-exec):   libfontconfig1 libgd3 libjbig0
aws_instance.example[1] (remote-exec):   libjpeg-turbo8 libjpeg8
aws_instance.example[1] (remote-exec):   libnginx-mod-http-image-filter
aws_instance.example[1] (remote-exec):   libnginx-mod-http-xslt-filter
aws_instance.example[1] (remote-exec):   libnginx-mod-mail
aws_instance.example[1] (remote-exec):   libnginx-mod-stream libtiff5
aws_instance.example[1] (remote-exec):   libwebp6 libxpm4 nginx-common
aws_instance.example[1] (remote-exec):   nginx-core
aws_instance.example[1] (remote-exec): Suggested packages:
aws_instance.example[1] (remote-exec):   libgd-tools fcgiwrap nginx-doc
aws_instance.example[1] (remote-exec):   ssl-cert
aws_instance.example[1] (remote-exec): The following NEW packages will be installed:
aws_instance.example[1] (remote-exec):   fontconfig-config fonts-dejavu-core
aws_instance.example[1] (remote-exec):   libfontconfig1 libgd3 libjbig0
aws_instance.example[1] (remote-exec):   libjpeg-turbo8 libjpeg8
aws_instance.example[1] (remote-exec):   libnginx-mod-http-image-filter
aws_instance.example[1] (remote-exec):   libnginx-mod-http-xslt-filter
aws_instance.example[1] (remote-exec):   libnginx-mod-mail
aws_instance.example[1] (remote-exec):   libnginx-mod-stream libtiff5
aws_instance.example[1] (remote-exec):   libwebp6 libxpm4 nginx nginx-common
aws_instance.example[1] (remote-exec):   nginx-core
aws_instance.example[1] (remote-exec): 0 upgraded, 17 newly installed, 0 to remove and 21 not upgraded.
aws_instance.example[1] (remote-exec): Need to get 2431 kB of archives.
aws_instance.example[1] (remote-exec): After this operation, 7891 kB of additional disk space will be used.
aws_instance.example[1] (remote-exec): 0% [Working]
aws_instance.example[1] (remote-exec): Get:1 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 fonts-dejavu-core all 2.37-1 [1041 kB]
aws_instance.example[1] (remote-exec): 0% [1 fonts-dejavu-core 0 B/1041 kB 0%]
aws_instance.example[1] (remote-exec): 35% [Working]
aws_instance.example[1] (remote-exec): Get:2 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 fontconfig-config all 2.13.1-2ubuntu3 [28.8 kB]
aws_instance.example[1] (remote-exec): 35% [2 fontconfig-config 0 B/28.8 kB 0%
aws_instance.example[1] (remote-exec): 38% [Working]
aws_instance.example[1] (remote-exec): Get:3 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libfontconfig1 amd64 2.13.1-2ubuntu3 [114 kB]
aws_instance.example[1] (remote-exec): 38% [3 libfontconfig1 0 B/114 kB 0%]
aws_instance.example[1] (remote-exec): 42% [Working]
aws_instance.example[1] (remote-exec): Get:4 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjpeg-turbo8 amd64 2.0.3-0ubuntu1 [118 kB]
aws_instance.example[1] (remote-exec): 42% [4 libjpeg-turbo8 0 B/118 kB 0%]
aws_instance.example[1] (remote-exec): 48% [Working]
aws_instance.example[1] (remote-exec): Get:5 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjpeg8 amd64 8c-2ubuntu8 [2194 B]
aws_instance.example[1] (remote-exec): 48% [5 libjpeg8 0 B/2194 B 0%]
aws_instance.example[1] (remote-exec): 49% [Working]
aws_instance.example[1] (remote-exec): Get:6 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjbig0 amd64 2.1-3.1build1 [26.7 kB]
aws_instance.example[1] (remote-exec): 49% [6 libjbig0 0 B/26.7 kB 0%]
aws_instance.example[1] (remote-exec): 51% [Working]
aws_instance.example[1] (remote-exec): Get:7 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libwebp6 amd64 0.6.1-2 [185 kB]
aws_instance.example[1] (remote-exec): 51% [7 libwebp6 0 B/185 kB 0%]
aws_instance.example[1] (remote-exec): 58% [Working]
aws_instance.example[1] (remote-exec): Get:8 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libtiff5 amd64 4.1.0+git191117-2build1 [161 kB]
aws_instance.example[1] (remote-exec): 58% [8 libtiff5 0 B/161 kB 0%]
aws_instance.example[1] (remote-exec): 65% [Working]
aws_instance.example[1] (remote-exec): Get:9 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libxpm4 amd64 1:3.5.12-1 [34.0 kB]
aws_instance.example[1] (remote-exec): 65% [9 libxpm4 0 B/34.0 kB 0%]
aws_instance.example[1] (remote-exec): 67% [Working]
aws_instance.example[1] (remote-exec): Get:10 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libgd3 amd64 2.2.5-5.2ubuntu2 [118 kB]
aws_instance.example[1] (remote-exec): 67% [10 libgd3 0 B/118 kB 0%]
aws_instance.example[1] (remote-exec): 72% [Working]
aws_instance.example[1] (remote-exec): Get:11 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx-common all 1.17.10-0ubuntu1 [37.3 kB]
aws_instance.example[1] (remote-exec): 72% [11 nginx-common 0 B/37.3 kB 0%]
aws_instance.example[1] (remote-exec): 74% [Working]
aws_instance.example[1] (remote-exec): Get:12 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-http-image-filter amd64 1.17.10-0ubuntu1 [14.3 kB]
aws_instance.example[1] (remote-exec): 74% [12 libnginx-mod-http-image-filter
aws_instance.example[1] (remote-exec): 76% [Working]
aws_instance.example[1] (remote-exec): Get:13 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-http-xslt-filter amd64 1.17.10-0ubuntu1 [12.5 kB]
aws_instance.example[1] (remote-exec): 76% [13 libnginx-mod-http-xslt-filter 0
aws_instance.example[1] (remote-exec): 78% [Working]
aws_instance.example[1] (remote-exec): Get:14 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-mail amd64 1.17.10-0ubuntu1 [42.3 kB]
aws_instance.example[1] (remote-exec): 78% [14 libnginx-mod-mail 0 B/42.3 kB 0
aws_instance.example[1] (remote-exec): 80% [Working]
aws_instance.example[1] (remote-exec): Get:15 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-stream amd64 1.17.10-0ubuntu1 [66.9 kB]
aws_instance.example[1] (remote-exec): 80% [15 libnginx-mod-stream 0 B/66.9 kB
aws_instance.example[1] (remote-exec): 84% [Working]
aws_instance.example[1] (remote-exec): Get:16 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx-core amd64 1.17.10-0ubuntu1 [425 kB]
aws_instance.example[1] (remote-exec): 84% [16 nginx-core 0 B/425 kB 0%]
aws_instance.example[1] (remote-exec): 99% [Working]
aws_instance.example[1] (remote-exec): Get:17 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx all 1.17.10-0ubuntu1 [3616 B]
aws_instance.example[1] (remote-exec): 99% [17 nginx 0 B/3616 B 0%]
aws_instance.example[1] (remote-exec): 100% [Working]
aws_instance.example[1] (remote-exec): Fetched 2431 kB in 0s (35.0 MB/s)
aws_instance.example[0] (remote-exec): Processing triggers for libc-bin (2.31-0ubuntu9) ...
aws_instance.example[1] (remote-exec): Preconfiguring packages ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package fonts-dejavu-core.
aws_instance.example[1] (remote-exec): (Reading database ...
aws_instance.example[1] (remote-exec): (Reading database ... 5%
aws_instance.example[1] (remote-exec): (Reading database ... 10%
aws_instance.example[1] (remote-exec): (Reading database ... 15%
aws_instance.example[1] (remote-exec): (Reading database ... 20%
aws_instance.example[1] (remote-exec): (Reading database ... 25%
aws_instance.example[1] (remote-exec): (Reading database ... 30%
aws_instance.example[1] (remote-exec): (Reading database ... 35%
aws_instance.example[1] (remote-exec): (Reading database ... 40%
aws_instance.example[1] (remote-exec): (Reading database ... 45%
aws_instance.example[1] (remote-exec): (Reading database ... 50%
aws_instance.example[1] (remote-exec): (Reading database ... 55%
aws_instance.example[1] (remote-exec): (Reading database ... 60%
aws_instance.example[1] (remote-exec): (Reading database ... 65%
aws_instance.example[1] (remote-exec): (Reading database ... 70%
aws_instance.example[1] (remote-exec): (Reading database ... 75%
aws_instance.example[1] (remote-exec): (Reading database ... 80%
aws_instance.example[1] (remote-exec): (Reading database ... 85%
aws_instance.example[1] (remote-exec): (Reading database ... 90%
aws_instance.example[1] (remote-exec): (Reading database ... 95%
aws_instance.example[1] (remote-exec): (Reading database ... 100%
aws_instance.example[1] (remote-exec): (Reading database ... 59604 files and directories currently installed.)
aws_instance.example[1] (remote-exec): Preparing to unpack .../00-fonts-dejavu-core_2.37-1_all.deb ...
aws_instance.example[1] (remote-exec): Unpacking fonts-dejavu-core (2.37-1) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package fontconfig-config.
aws_instance.example[1] (remote-exec): Preparing to unpack .../01-fontconfig-config_2.13.1-2ubuntu3_all.deb ...
aws_instance.example[1] (remote-exec): Unpacking fontconfig-config (2.13.1-2ubuntu3) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package libfontconfig1:amd64.
aws_instance.example[1] (remote-exec): Preparing to unpack .../02-libfontconfig1_2.13.1-2ubuntu3_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking libfontconfig1:amd64 (2.13.1-2ubuntu3) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package libjpeg-turbo8:amd64.
aws_instance.example[1] (remote-exec): Preparing to unpack .../03-libjpeg-turbo8_2.0.3-0ubuntu1_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking libjpeg-turbo8:amd64 (2.0.3-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package libjpeg8:amd64.
aws_instance.example[1] (remote-exec): Preparing to unpack .../04-libjpeg8_8c-2ubuntu8_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking libjpeg8:amd64 (8c-2ubuntu8) ...
aws_instance.example[2] (remote-exec): Reading package lists... 0%
aws_instance.example[2] (remote-exec): Reading package lists... 0%
aws_instance.example[2] (remote-exec): Reading package lists... 0%
aws_instance.example[1] (remote-exec): Selecting previously unselected package libjbig0:amd64.
aws_instance.example[1] (remote-exec): Preparing to unpack .../05-libjbig0_2.1-3.1build1_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking libjbig0:amd64 (2.1-3.1build1) ...
aws_instance.example[0]: Still creating... [1m10s elapsed]
aws_instance.example[2]: Still creating... [1m10s elapsed]
aws_instance.example[1]: Still creating... [1m10s elapsed]
aws_instance.example[3]: Still creating... [1m10s elapsed]
aws_instance.example[1] (remote-exec): Selecting previously unselected package libwebp6:amd64.
aws_instance.example[1] (remote-exec): Preparing to unpack .../06-libwebp6_0.6.1-2_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking libwebp6:amd64 (0.6.1-2) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package libtiff5:amd64.
aws_instance.example[1] (remote-exec): Preparing to unpack .../07-libtiff5_4.1.0+git191117-2build1_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking libtiff5:amd64 (4.1.0+git191117-2build1) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package libxpm4:amd64.
aws_instance.example[1] (remote-exec): Preparing to unpack .../08-libxpm4_1%3a3.5.12-1_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking libxpm4:amd64 (1:3.5.12-1) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package libgd3:amd64.
aws_instance.example[1] (remote-exec): Preparing to unpack .../09-libgd3_2.2.5-5.2ubuntu2_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking libgd3:amd64 (2.2.5-5.2ubuntu2) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package nginx-common.
aws_instance.example[1] (remote-exec): Preparing to unpack .../10-nginx-common_1.17.10-0ubuntu1_all.deb ...
aws_instance.example[1] (remote-exec): Unpacking nginx-common (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Reading package lists... 6%
aws_instance.example[2] (remote-exec): Reading package lists... 6%
aws_instance.example[2] (remote-exec): Reading package lists... 9%
aws_instance.example[2] (remote-exec): Reading package lists... 9%
aws_instance.example[2] (remote-exec): Reading package lists... 10%
aws_instance.example[2] (remote-exec): Reading package lists... 10%
aws_instance.example[1] (remote-exec): Selecting previously unselected package libnginx-mod-http-image-filter.
aws_instance.example[1] (remote-exec): Preparing to unpack .../11-libnginx-mod-http-image-filter_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking libnginx-mod-http-image-filter (1.17.10-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package libnginx-mod-http-xslt-filter.
aws_instance.example[1] (remote-exec): Preparing to unpack .../12-libnginx-mod-http-xslt-filter_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking libnginx-mod-http-xslt-filter (1.17.10-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package libnginx-mod-mail.
aws_instance.example[1] (remote-exec): Preparing to unpack .../13-libnginx-mod-mail_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking libnginx-mod-mail (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Reading package lists... 10%
aws_instance.example[2] (remote-exec): Reading package lists... 10%
aws_instance.example[2] (remote-exec): Reading package lists... 66%
aws_instance.example[2] (remote-exec): Reading package lists... 66%
aws_instance.example[2] (remote-exec): Reading package lists... 96%
aws_instance.example[2] (remote-exec): Reading package lists... 96%
aws_instance.example[2] (remote-exec): Reading package lists... 97%
aws_instance.example[2] (remote-exec): Reading package lists... 97%
aws_instance.example[2] (remote-exec): Reading package lists... 97%
aws_instance.example[2] (remote-exec): Reading package lists... 97%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 99%
aws_instance.example[2] (remote-exec): Reading package lists... 99%
aws_instance.example[2] (remote-exec): Reading package lists... 99%
aws_instance.example[2] (remote-exec): Reading package lists... 99%
aws_instance.example[2] (remote-exec): Reading package lists... 99%
aws_instance.example[2] (remote-exec): Reading package lists... 99%
aws_instance.example[2] (remote-exec): Reading package lists... 99%
aws_instance.example[2] (remote-exec): Reading package lists... 99%
aws_instance.example[2] (remote-exec): Reading package lists... 99%
aws_instance.example[2] (remote-exec): Reading package lists... 99%
aws_instance.example[2] (remote-exec): Reading package lists... 99%
aws_instance.example[2] (remote-exec): Reading package lists... 99%
aws_instance.example[2] (remote-exec): Reading package lists... Done
aws_instance.example[1] (remote-exec): Selecting previously unselected package libnginx-mod-stream.
aws_instance.example[1] (remote-exec): Preparing to unpack .../14-libnginx-mod-stream_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking libnginx-mod-stream (1.17.10-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package nginx-core.
aws_instance.example[1] (remote-exec): Preparing to unpack .../15-nginx-core_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking nginx-core (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Reading package lists... 0%
aws_instance.example[2] (remote-exec): Reading package lists... 100%
aws_instance.example[2] (remote-exec): Reading package lists... Done
aws_instance.example[1] (remote-exec): Selecting previously unselected package nginx.
aws_instance.example[1] (remote-exec): Preparing to unpack .../16-nginx_1.17.10-0ubuntu1_all.deb ...
aws_instance.example[1] (remote-exec): Unpacking nginx (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Building dependency tree... 0%
aws_instance.example[2] (remote-exec): Building dependency tree... 0%
aws_instance.example[3] (remote-exec): Reading package lists... 0%
aws_instance.example[3] (remote-exec): Reading package lists... 0%
aws_instance.example[3] (remote-exec): Reading package lists... 0%
aws_instance.example[3] (remote-exec): Reading package lists... 6%
aws_instance.example[3] (remote-exec): Reading package lists... 6%
aws_instance.example[3] (remote-exec): Reading package lists... 9%
aws_instance.example[3] (remote-exec): Reading package lists... 9%
aws_instance.example[3] (remote-exec): Reading package lists... 10%
aws_instance.example[3] (remote-exec): Reading package lists... 10%
aws_instance.example[3] (remote-exec): Reading package lists... 10%
aws_instance.example[2] (remote-exec): Building dependency tree... 50%
aws_instance.example[2] (remote-exec): Building dependency tree... 50%
aws_instance.example[2] (remote-exec): Building dependency tree
aws_instance.example[1] (remote-exec): Setting up libxpm4:amd64 (1:3.5.12-1) ...
aws_instance.example[1] (remote-exec): Setting up nginx-common (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Reading state information... 0%
aws_instance.example[2] (remote-exec): Reading state information... 0%
aws_instance.example[2] (remote-exec): Reading state information... Done
aws_instance.example[2] (remote-exec): The following additional packages will be installed:
aws_instance.example[2] (remote-exec):   fontconfig-config fonts-dejavu-core
aws_instance.example[2] (remote-exec):   libfontconfig1 libgd3 libjbig0
aws_instance.example[2] (remote-exec):   libjpeg-turbo8 libjpeg8
aws_instance.example[2] (remote-exec):   libnginx-mod-http-image-filter
aws_instance.example[2] (remote-exec):   libnginx-mod-http-xslt-filter
aws_instance.example[2] (remote-exec):   libnginx-mod-mail
aws_instance.example[2] (remote-exec):   libnginx-mod-stream libtiff5
aws_instance.example[2] (remote-exec):   libwebp6 libxpm4 nginx-common
aws_instance.example[2] (remote-exec):   nginx-core
aws_instance.example[2] (remote-exec): Suggested packages:
aws_instance.example[2] (remote-exec):   libgd-tools fcgiwrap nginx-doc
aws_instance.example[2] (remote-exec):   ssl-cert
aws_instance.example[2] (remote-exec): The following NEW packages will be installed:
aws_instance.example[3] (remote-exec): Reading package lists... 10%
aws_instance.example[2] (remote-exec):   fontconfig-config fonts-dejavu-core
aws_instance.example[2] (remote-exec):   libfontconfig1 libgd3 libjbig0
aws_instance.example[2] (remote-exec):   libjpeg-turbo8 libjpeg8
aws_instance.example[2] (remote-exec):   libnginx-mod-http-image-filter
aws_instance.example[2] (remote-exec):   libnginx-mod-http-xslt-filter
aws_instance.example[2] (remote-exec):   libnginx-mod-mail
aws_instance.example[2] (remote-exec):   libnginx-mod-stream libtiff5
aws_instance.example[2] (remote-exec):   libwebp6 libxpm4 nginx nginx-common
aws_instance.example[2] (remote-exec):   nginx-core
aws_instance.example[2] (remote-exec): 0 upgraded, 17 newly installed, 0 to remove and 21 not upgraded.
aws_instance.example[2] (remote-exec): Need to get 2431 kB of archives.
aws_instance.example[2] (remote-exec): After this operation, 7891 kB of additional disk space will be used.
aws_instance.example[2] (remote-exec): 0% [Working]
aws_instance.example[2] (remote-exec): Get:1 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 fonts-dejavu-core all 2.37-1 [1041 kB]
aws_instance.example[2] (remote-exec): 0% [1 fonts-dejavu-core 0 B/1041 kB 0%]
aws_instance.example[2] (remote-exec): 35% [Working]
aws_instance.example[2] (remote-exec): Get:2 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 fontconfig-config all 2.13.1-2ubuntu3 [28.8 kB]
aws_instance.example[2] (remote-exec): 35% [2 fontconfig-config 0 B/28.8 kB 0%
aws_instance.example[2] (remote-exec): 38% [Working]
aws_instance.example[2] (remote-exec): Get:3 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libfontconfig1 amd64 2.13.1-2ubuntu3 [114 kB]
aws_instance.example[2] (remote-exec): 38% [3 libfontconfig1 0 B/114 kB 0%]
aws_instance.example[2] (remote-exec): 42% [Working]
aws_instance.example[2] (remote-exec): Get:4 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjpeg-turbo8 amd64 2.0.3-0ubuntu1 [118 kB]
aws_instance.example[2] (remote-exec): 42% [4 libjpeg-turbo8 0 B/118 kB 0%]
aws_instance.example[2] (remote-exec): 48% [Working]
aws_instance.example[2] (remote-exec): Get:5 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjpeg8 amd64 8c-2ubuntu8 [2194 B]
aws_instance.example[2] (remote-exec): 48% [5 libjpeg8 0 B/2194 B 0%]
aws_instance.example[2] (remote-exec): 49% [Working]
aws_instance.example[2] (remote-exec): Get:6 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjbig0 amd64 2.1-3.1build1 [26.7 kB]
aws_instance.example[2] (remote-exec): 49% [6 libjbig0 0 B/26.7 kB 0%]
aws_instance.example[2] (remote-exec): 51% [Working]
aws_instance.example[2] (remote-exec): Get:7 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libwebp6 amd64 0.6.1-2 [185 kB]
aws_instance.example[2] (remote-exec): 51% [7 libwebp6 0 B/185 kB 0%]
aws_instance.example[2] (remote-exec): 58% [Working]
aws_instance.example[2] (remote-exec): Get:8 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libtiff5 amd64 4.1.0+git191117-2build1 [161 kB]
aws_instance.example[2] (remote-exec): 58% [8 libtiff5 0 B/161 kB 0%]
aws_instance.example[2] (remote-exec): 65% [Working]
aws_instance.example[2] (remote-exec): Get:9 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libxpm4 amd64 1:3.5.12-1 [34.0 kB]
aws_instance.example[2] (remote-exec): 65% [9 libxpm4 0 B/34.0 kB 0%]
aws_instance.example[2] (remote-exec): 67% [Working]
aws_instance.example[2] (remote-exec): Get:10 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libgd3 amd64 2.2.5-5.2ubuntu2 [118 kB]
aws_instance.example[2] (remote-exec): 67% [10 libgd3 0 B/118 kB 0%]
aws_instance.example[2] (remote-exec): 72% [Working]
aws_instance.example[2] (remote-exec): Get:11 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx-common all 1.17.10-0ubuntu1 [37.3 kB]
aws_instance.example[2] (remote-exec): 72% [11 nginx-common 0 B/37.3 kB 0%]
aws_instance.example[2] (remote-exec): 74% [Working]
aws_instance.example[2] (remote-exec): Get:12 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-http-image-filter amd64 1.17.10-0ubuntu1 [14.3 kB]
aws_instance.example[2] (remote-exec): 74% [12 libnginx-mod-http-image-filter
aws_instance.example[2] (remote-exec): 76% [Working]
aws_instance.example[2] (remote-exec): Get:13 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-http-xslt-filter amd64 1.17.10-0ubuntu1 [12.5 kB]
aws_instance.example[2] (remote-exec): 76% [13 libnginx-mod-http-xslt-filter 0
aws_instance.example[2] (remote-exec): 78% [Working]
aws_instance.example[2] (remote-exec): Get:14 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-mail amd64 1.17.10-0ubuntu1 [42.3 kB]
aws_instance.example[2] (remote-exec): 78% [14 libnginx-mod-mail 0 B/42.3 kB 0
aws_instance.example[2] (remote-exec): 80% [Working]
aws_instance.example[2] (remote-exec): Get:15 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-stream amd64 1.17.10-0ubuntu1 [66.9 kB]
aws_instance.example[2] (remote-exec): 80% [15 libnginx-mod-stream 0 B/66.9 kB
aws_instance.example[2] (remote-exec): 84% [Working]
aws_instance.example[2] (remote-exec): Get:16 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx-core amd64 1.17.10-0ubuntu1 [425 kB]
aws_instance.example[2] (remote-exec): 84% [16 nginx-core 0 B/425 kB 0%]
aws_instance.example[2] (remote-exec): 99% [Working]
aws_instance.example[2] (remote-exec): Get:17 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx all 1.17.10-0ubuntu1 [3616 B]
aws_instance.example[2] (remote-exec): 99% [17 nginx 0 B/3616 B 0%]
aws_instance.example[2] (remote-exec): 100% [Working]
aws_instance.example[2] (remote-exec): Fetched 2431 kB in 0s (25.8 MB/s)
aws_instance.example[1] (remote-exec): Created symlink /etc/systemd/system/multi-user.target.wants/nginx.service → /lib/systemd/system/nginx.service.
aws_instance.example[2] (remote-exec): Preconfiguring packages ...
aws_instance.example[3] (remote-exec): Reading package lists... 66%
aws_instance.example[3] (remote-exec): Reading package lists... 66%
aws_instance.example[3] (remote-exec): Reading package lists... 96%
aws_instance.example[3] (remote-exec): Reading package lists... 96%
aws_instance.example[3] (remote-exec): Reading package lists... 97%
aws_instance.example[3] (remote-exec): Reading package lists... 97%
aws_instance.example[3] (remote-exec): Reading package lists... 97%
aws_instance.example[3] (remote-exec): Reading package lists... 97%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 99%
aws_instance.example[3] (remote-exec): Reading package lists... 99%
aws_instance.example[3] (remote-exec): Reading package lists... 99%
aws_instance.example[3] (remote-exec): Reading package lists... 99%
aws_instance.example[3] (remote-exec): Reading package lists... 99%
aws_instance.example[3] (remote-exec): Reading package lists... 99%
aws_instance.example[3] (remote-exec): Reading package lists... 99%
aws_instance.example[3] (remote-exec): Reading package lists... 99%
aws_instance.example[3] (remote-exec): Reading package lists... 99%
aws_instance.example[3] (remote-exec): Reading package lists... 99%
aws_instance.example[3] (remote-exec): Reading package lists... 99%
aws_instance.example[3] (remote-exec): Reading package lists... 99%
aws_instance.example[3] (remote-exec): Reading package lists... Done
aws_instance.example[2] (remote-exec): Selecting previously unselected package fonts-dejavu-core.

aws_instance.example[3] (remote-exec): Reading package lists... 0%
aws_instance.example[3] (remote-exec): Reading package lists... 100%
aws_instance.example[3] (remote-exec): Reading package lists... Done
aws_instance.example[3] (remote-exec): Building dependency tree... 0%
aws_instance.example[3] (remote-exec): Building dependency tree... 0%
aws_instance.example[3] (remote-exec): Building dependency tree... 50%
aws_instance.example[3] (remote-exec): Building dependency tree... 50%
aws_instance.example[3] (remote-exec): Building dependency tree
aws_instance.example[3] (remote-exec): Reading state information... 0%
aws_instance.example[3] (remote-exec): Reading state information... 0%
aws_instance.example[3] (remote-exec): Reading state information... Done
aws_instance.example[2] (remote-exec): (Reading database ...
aws_instance.example[2] (remote-exec): (Reading database ... 5%
aws_instance.example[2] (remote-exec): (Reading database ... 10%
aws_instance.example[2] (remote-exec): (Reading database ... 15%
aws_instance.example[2] (remote-exec): (Reading database ... 20%
aws_instance.example[2] (remote-exec): (Reading database ... 25%
aws_instance.example[2] (remote-exec): (Reading database ... 30%
aws_instance.example[2] (remote-exec): (Reading database ... 35%
aws_instance.example[2] (remote-exec): (Reading database ... 40%
aws_instance.example[2] (remote-exec): (Reading database ... 45%
aws_instance.example[3] (remote-exec): The following additional packages will be installed:
aws_instance.example[3] (remote-exec):   fontconfig-config fonts-dejavu-core
aws_instance.example[3] (remote-exec):   libfontconfig1 libgd3 libjbig0
aws_instance.example[3] (remote-exec):   libjpeg-turbo8 libjpeg8
aws_instance.example[3] (remote-exec):   libnginx-mod-http-image-filter
aws_instance.example[3] (remote-exec):   libnginx-mod-http-xslt-filter
aws_instance.example[3] (remote-exec):   libnginx-mod-mail
aws_instance.example[3] (remote-exec):   libnginx-mod-stream libtiff5
aws_instance.example[3] (remote-exec):   libwebp6 libxpm4 nginx-common
aws_instance.example[3] (remote-exec):   nginx-core
aws_instance.example[3] (remote-exec): Suggested packages:
aws_instance.example[3] (remote-exec):   libgd-tools fcgiwrap nginx-doc
aws_instance.example[3] (remote-exec):   ssl-cert
aws_instance.example[3] (remote-exec): The following NEW packages will be installed:
aws_instance.example[3] (remote-exec):   fontconfig-config fonts-dejavu-core
aws_instance.example[3] (remote-exec):   libfontconfig1 libgd3 libjbig0
aws_instance.example[3] (remote-exec):   libjpeg-turbo8 libjpeg8
aws_instance.example[3] (remote-exec):   libnginx-mod-http-image-filter
aws_instance.example[3] (remote-exec):   libnginx-mod-http-xslt-filter
aws_instance.example[3] (remote-exec):   libnginx-mod-mail
aws_instance.example[3] (remote-exec):   libnginx-mod-stream libtiff5
aws_instance.example[3] (remote-exec):   libwebp6 libxpm4 nginx nginx-common
aws_instance.example[2] (remote-exec): (Reading database ... 50%
aws_instance.example[2] (remote-exec): (Reading database ... 55%
aws_instance.example[2] (remote-exec): (Reading database ... 60%
aws_instance.example[2] (remote-exec): (Reading database ... 65%
aws_instance.example[2] (remote-exec): (Reading database ... 70%
aws_instance.example[2] (remote-exec): (Reading database ... 75%
aws_instance.example[2] (remote-exec): (Reading database ... 80%
aws_instance.example[2] (remote-exec): (Reading database ... 85%
aws_instance.example[1] (remote-exec): Setting up libjbig0:amd64 (2.1-3.1build1) ...
aws_instance.example[2] (remote-exec): (Reading database ... 90%
aws_instance.example[2] (remote-exec): (Reading database ... 95%
aws_instance.example[2] (remote-exec): (Reading database ... 100%
aws_instance.example[2] (remote-exec): (Reading database ... 59604 files and directories currently installed.)
aws_instance.example[2] (remote-exec): Preparing to unpack .../00-fonts-dejavu-core_2.37-1_all.deb ...
aws_instance.example[2] (remote-exec): Unpacking fonts-dejavu-core (2.37-1) ...
aws_instance.example[1] (remote-exec): Setting up libnginx-mod-http-xslt-filter (1.17.10-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Setting up libwebp6:amd64 (0.6.1-2) ...
aws_instance.example[1] (remote-exec): Setting up fonts-dejavu-core (2.37-1) ...
aws_instance.example[3] (remote-exec):   nginx-core
aws_instance.example[3] (remote-exec): 0 upgraded, 17 newly installed, 0 to remove and 21 not upgraded.
aws_instance.example[3] (remote-exec): Need to get 2431 kB of archives.
aws_instance.example[3] (remote-exec): After this operation, 7891 kB of additional disk space will be used.
aws_instance.example[3] (remote-exec): 0% [Working]
aws_instance.example[3] (remote-exec): Get:1 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 fonts-dejavu-core all 2.37-1 [1041 kB]
aws_instance.example[3] (remote-exec): 0% [1 fonts-dejavu-core 0 B/1041 kB 0%]
aws_instance.example[3] (remote-exec): 35% [Working]
aws_instance.example[3] (remote-exec): Get:2 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 fontconfig-config all 2.13.1-2ubuntu3 [28.8 kB]
aws_instance.example[3] (remote-exec): 35% [2 fontconfig-config 0 B/28.8 kB 0%
aws_instance.example[3] (remote-exec): 38% [Working]
aws_instance.example[3] (remote-exec): Get:3 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libfontconfig1 amd64 2.13.1-2ubuntu3 [114 kB]
aws_instance.example[3] (remote-exec): 38% [3 libfontconfig1 0 B/114 kB 0%]
aws_instance.example[3] (remote-exec): 42% [Working]
aws_instance.example[3] (remote-exec): Get:4 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjpeg-turbo8 amd64 2.0.3-0ubuntu1 [118 kB]
aws_instance.example[3] (remote-exec): 42% [4 libjpeg-turbo8 0 B/118 kB 0%]
aws_instance.example[3] (remote-exec): 48% [Working]
aws_instance.example[3] (remote-exec): Get:5 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjpeg8 amd64 8c-2ubuntu8 [2194 B]
aws_instance.example[1] (remote-exec): Setting up libjpeg-turbo8:amd64 (2.0.3-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Setting up libjpeg8:amd64 (8c-2ubuntu8) ...
aws_instance.example[1] (remote-exec): Setting up libnginx-mod-mail (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): 48% [5 libjpeg8 0 B/2194 B 0%]
aws_instance.example[3] (remote-exec): 49% [Working]
aws_instance.example[3] (remote-exec): Get:6 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjbig0 amd64 2.1-3.1build1 [26.7 kB]
aws_instance.example[3] (remote-exec): 49% [6 libjbig0 0 B/26.7 kB 0%]
aws_instance.example[3] (remote-exec): 51% [Working]
aws_instance.example[3] (remote-exec): Get:7 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libwebp6 amd64 0.6.1-2 [185 kB]
aws_instance.example[3] (remote-exec): 51% [7 libwebp6 0 B/185 kB 0%]
aws_instance.example[3] (remote-exec): 58% [Working]
aws_instance.example[3] (remote-exec): Get:8 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libtiff5 amd64 4.1.0+git191117-2build1 [161 kB]
aws_instance.example[3] (remote-exec): 58% [8 libtiff5 0 B/161 kB 0%]
aws_instance.example[3] (remote-exec): 65% [Working]
aws_instance.example[3] (remote-exec): Get:9 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libxpm4 amd64 1:3.5.12-1 [34.0 kB]
aws_instance.example[3] (remote-exec): 65% [9 libxpm4 0 B/34.0 kB 0%]
aws_instance.example[3] (remote-exec): 67% [Working]
aws_instance.example[3] (remote-exec): Get:10 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libgd3 amd64 2.2.5-5.2ubuntu2 [118 kB]
aws_instance.example[3] (remote-exec): 67% [10 libgd3 0 B/118 kB 0%]
aws_instance.example[3] (remote-exec): 72% [Working]
aws_instance.example[3] (remote-exec): Get:11 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx-common all 1.17.10-0ubuntu1 [37.3 kB]
aws_instance.example[3] (remote-exec): 72% [11 nginx-common 0 B/37.3 kB 0%]
aws_instance.example[3] (remote-exec): 74% [Working]
aws_instance.example[3] (remote-exec): Get:12 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-http-image-filter amd64 1.17.10-0ubuntu1 [14.3 kB]
aws_instance.example[3] (remote-exec): 74% [12 libnginx-mod-http-image-filter
aws_instance.example[3] (remote-exec): 76% [Working]
aws_instance.example[3] (remote-exec): Get:13 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-http-xslt-filter amd64 1.17.10-0ubuntu1 [12.5 kB]
aws_instance.example[3] (remote-exec): 76% [13 libnginx-mod-http-xslt-filter 0
aws_instance.example[3] (remote-exec): 78% [Working]
aws_instance.example[3] (remote-exec): Get:14 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-mail amd64 1.17.10-0ubuntu1 [42.3 kB]
aws_instance.example[3] (remote-exec): 78% [14 libnginx-mod-mail 0 B/42.3 kB 0
aws_instance.example[3] (remote-exec): 80% [Working]
aws_instance.example[3] (remote-exec): Get:15 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-stream amd64 1.17.10-0ubuntu1 [66.9 kB]
aws_instance.example[3] (remote-exec): 80% [15 libnginx-mod-stream 0 B/66.9 kB
aws_instance.example[3] (remote-exec): 84% [Working]
aws_instance.example[3] (remote-exec): Get:16 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx-core amd64 1.17.10-0ubuntu1 [425 kB]
aws_instance.example[3] (remote-exec): 84% [16 nginx-core 0 B/425 kB 0%]
aws_instance.example[3] (remote-exec): 99% [Working]
aws_instance.example[3] (remote-exec): Get:17 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx all 1.17.10-0ubuntu1 [3616 B]
aws_instance.example[3] (remote-exec): 99% [17 nginx 0 B/3616 B 0%]
aws_instance.example[3] (remote-exec): 100% [Working]
aws_instance.example[3] (remote-exec): Fetched 2431 kB in 0s (31.6 MB/s)
aws_instance.example[1] (remote-exec): Setting up fontconfig-config (2.13.1-2ubuntu3) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package fontconfig-config.
aws_instance.example[2] (remote-exec): Preparing to unpack .../01-fontconfig-config_2.13.1-2ubuntu3_all.deb ...
aws_instance.example[2] (remote-exec): Unpacking fontconfig-config (2.13.1-2ubuntu3) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package libfontconfig1:amd64.
aws_instance.example[2] (remote-exec): Preparing to unpack .../02-libfontconfig1_2.13.1-2ubuntu3_amd64.deb ...
aws_instance.example[2] (remote-exec): Unpacking libfontconfig1:amd64 (2.13.1-2ubuntu3) ...
aws_instance.example[1] (remote-exec): Setting up libnginx-mod-stream (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package libjpeg-turbo8:amd64.
aws_instance.example[2] (remote-exec): Preparing to unpack .../03-libjpeg-turbo8_2.0.3-0ubuntu1_amd64.deb ...
aws_instance.example[2] (remote-exec): Unpacking libjpeg-turbo8:amd64 (2.0.3-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Setting up libtiff5:amd64 (4.1.0+git191117-2build1) ...
aws_instance.example[1] (remote-exec): Setting up libfontconfig1:amd64 (2.13.1-2ubuntu3) ...
aws_instance.example[3] (remote-exec): Preconfiguring packages ...
aws_instance.example[1] (remote-exec): Setting up libgd3:amd64 (2.2.5-5.2ubuntu2) ...
aws_instance.example[1] (remote-exec): Setting up libnginx-mod-http-image-filter (1.17.10-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Setting up nginx-core (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package fonts-dejavu-core.
aws_instance.example[2] (remote-exec): Selecting previously unselected package libjpeg8:amd64.
aws_instance.example[2] (remote-exec): Preparing to unpack .../04-libjpeg8_8c-2ubuntu8_amd64.deb ...
aws_instance.example[2] (remote-exec): Unpacking libjpeg8:amd64 (8c-2ubuntu8) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package libjbig0:amd64.
aws_instance.example[2] (remote-exec): Preparing to unpack .../05-libjbig0_2.1-3.1build1_amd64.deb ...
aws_instance.example[2] (remote-exec): Unpacking libjbig0:amd64 (2.1-3.1build1) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package libwebp6:amd64.
aws_instance.example[2] (remote-exec): Preparing to unpack .../06-libwebp6_0.6.1-2_amd64.deb ...
aws_instance.example[2] (remote-exec): Unpacking libwebp6:amd64 (0.6.1-2) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package libtiff5:amd64.
aws_instance.example[2] (remote-exec): Preparing to unpack .../07-libtiff5_4.1.0+git191117-2build1_amd64.deb ...
aws_instance.example[2] (remote-exec): Unpacking libtiff5:amd64 (4.1.0+git191117-2build1) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package libxpm4:amd64.
aws_instance.example[2] (remote-exec): Preparing to unpack .../08-libxpm4_1%3a3.5.12-1_amd64.deb ...
aws_instance.example[2] (remote-exec): Unpacking libxpm4:amd64 (1:3.5.12-1) ...
aws_instance.example[3] (remote-exec): (Reading database ...
aws_instance.example[3] (remote-exec): (Reading database ... 5%
aws_instance.example[3] (remote-exec): (Reading database ... 10%
aws_instance.example[3] (remote-exec): (Reading database ... 15%
aws_instance.example[3] (remote-exec): (Reading database ... 20%
aws_instance.example[3] (remote-exec): (Reading database ... 25%
aws_instance.example[3] (remote-exec): (Reading database ... 30%
aws_instance.example[3] (remote-exec): (Reading database ... 35%
aws_instance.example[3] (remote-exec): (Reading database ... 40%
aws_instance.example[3] (remote-exec): (Reading database ... 45%
aws_instance.example[3] (remote-exec): (Reading database ... 50%
aws_instance.example[3] (remote-exec): (Reading database ... 55%
aws_instance.example[3] (remote-exec): (Reading database ... 60%
aws_instance.example[3] (remote-exec): (Reading database ... 65%
aws_instance.example[3] (remote-exec): (Reading database ... 70%
aws_instance.example[3] (remote-exec): (Reading database ... 75%
aws_instance.example[3] (remote-exec): (Reading database ... 80%
aws_instance.example[3] (remote-exec): (Reading database ... 85%
aws_instance.example[3] (remote-exec): (Reading database ... 90%
aws_instance.example[3] (remote-exec): (Reading database ... 95%
aws_instance.example[3] (remote-exec): (Reading database ... 100%
aws_instance.example[3] (remote-exec): (Reading database ... 59604 files and directories currently installed.)
aws_instance.example[3] (remote-exec): Preparing to unpack .../00-fonts-dejavu-core_2.37-1_all.deb ...
aws_instance.example[3] (remote-exec): Unpacking fonts-dejavu-core (2.37-1) ...
aws_instance.example[1] (remote-exec): Setting up nginx (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package libgd3:amd64.
aws_instance.example[2] (remote-exec): Preparing to unpack .../09-libgd3_2.2.5-5.2ubuntu2_amd64.deb ...
aws_instance.example[2] (remote-exec): Unpacking libgd3:amd64 (2.2.5-5.2ubuntu2) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package nginx-common.
aws_instance.example[2] (remote-exec): Preparing to unpack .../10-nginx-common_1.17.10-0ubuntu1_all.deb ...
aws_instance.example[2] (remote-exec): Unpacking nginx-common (1.17.10-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Processing triggers for ufw (0.36-6) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package libnginx-mod-http-image-filter.
aws_instance.example[3] (remote-exec): Selecting previously unselected package fontconfig-config.
aws_instance.example[3] (remote-exec): Preparing to unpack .../01-fontconfig-config_2.13.1-2ubuntu3_all.deb ...
aws_instance.example[3] (remote-exec): Unpacking fontconfig-config (2.13.1-2ubuntu3) ...
aws_instance.example[2] (remote-exec): Preparing to unpack .../11-libnginx-mod-http-image-filter_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[2] (remote-exec): Unpacking libnginx-mod-http-image-filter (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package libnginx-mod-http-xslt-filter.
aws_instance.example[2] (remote-exec): Preparing to unpack .../12-libnginx-mod-http-xslt-filter_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package libfontconfig1:amd64.
aws_instance.example[3] (remote-exec): Preparing to unpack .../02-libfontconfig1_2.13.1-2ubuntu3_amd64.deb ...
aws_instance.example[1] (remote-exec): Processing triggers for systemd (245.4-4ubuntu3) ...
aws_instance.example[3] (remote-exec): Unpacking libfontconfig1:amd64 (2.13.1-2ubuntu3) ...
aws_instance.example[2] (remote-exec): Unpacking libnginx-mod-http-xslt-filter (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package libnginx-mod-mail.
aws_instance.example[2] (remote-exec): Preparing to unpack .../13-libnginx-mod-mail_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package libjpeg-turbo8:amd64.
aws_instance.example[3] (remote-exec): Preparing to unpack .../03-libjpeg-turbo8_2.0.3-0ubuntu1_amd64.deb ...
aws_instance.example[3] (remote-exec): Unpacking libjpeg-turbo8:amd64 (2.0.3-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Unpacking libnginx-mod-mail (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package libjpeg8:amd64.
aws_instance.example[3] (remote-exec): Preparing to unpack .../04-libjpeg8_8c-2ubuntu8_amd64.deb ...
aws_instance.example[3] (remote-exec): Unpacking libjpeg8:amd64 (8c-2ubuntu8) ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package libjbig0:amd64.
aws_instance.example[3] (remote-exec): Preparing to unpack .../05-libjbig0_2.1-3.1build1_amd64.deb ...
aws_instance.example[3] (remote-exec): Unpacking libjbig0:amd64 (2.1-3.1build1) ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package libwebp6:amd64.
aws_instance.example[3] (remote-exec): Preparing to unpack .../06-libwebp6_0.6.1-2_amd64.deb ...
aws_instance.example[3] (remote-exec): Unpacking libwebp6:amd64 (0.6.1-2) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package libnginx-mod-stream.
aws_instance.example[2] (remote-exec): Preparing to unpack .../14-libnginx-mod-stream_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[2] (remote-exec): Unpacking libnginx-mod-stream (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package nginx-core.
aws_instance.example[2] (remote-exec): Preparing to unpack .../15-nginx-core_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[2] (remote-exec): Unpacking nginx-core (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package nginx.
aws_instance.example[2] (remote-exec): Preparing to unpack .../16-nginx_1.17.10-0ubuntu1_all.deb ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package libtiff5:amd64.
aws_instance.example[3] (remote-exec): Preparing to unpack .../07-libtiff5_4.1.0+git191117-2build1_amd64.deb ...
aws_instance.example[3] (remote-exec): Unpacking libtiff5:amd64 (4.1.0+git191117-2build1) ...
aws_instance.example[2] (remote-exec): Unpacking nginx (1.17.10-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Processing triggers for man-db (2.9.1-1) ...
aws_instance.example[2] (remote-exec): Setting up libxpm4:amd64 (1:3.5.12-1) ...
aws_instance.example[2] (remote-exec): Setting up nginx-common (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package libxpm4:amd64.
aws_instance.example[3] (remote-exec): Preparing to unpack .../08-libxpm4_1%3a3.5.12-1_amd64.deb ...
aws_instance.example[3] (remote-exec): Unpacking libxpm4:amd64 (1:3.5.12-1) ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package libgd3:amd64.
aws_instance.example[3] (remote-exec): Preparing to unpack .../09-libgd3_2.2.5-5.2ubuntu2_amd64.deb ...
aws_instance.example[3] (remote-exec): Unpacking libgd3:amd64 (2.2.5-5.2ubuntu2) ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package nginx-common.
aws_instance.example[3] (remote-exec): Preparing to unpack .../10-nginx-common_1.17.10-0ubuntu1_all.deb ...
aws_instance.example[3] (remote-exec): Unpacking nginx-common (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package libnginx-mod-http-image-filter.
aws_instance.example[3] (remote-exec): Preparing to unpack .../11-libnginx-mod-http-image-filter_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[3] (remote-exec): Unpacking libnginx-mod-http-image-filter (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package libnginx-mod-http-xslt-filter.
aws_instance.example[3] (remote-exec): Preparing to unpack .../12-libnginx-mod-http-xslt-filter_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[3] (remote-exec): Unpacking libnginx-mod-http-xslt-filter (1.17.10-0ubuntu1) ...
aws_instance.example[0]: Creation complete after 1m14s [id=i-01f45219dbbccaac1]
aws_instance.example[1] (remote-exec): Processing triggers for libc-bin (2.31-0ubuntu9) ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package libnginx-mod-mail.
aws_instance.example[3] (remote-exec): Preparing to unpack .../13-libnginx-mod-mail_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[3] (remote-exec): Unpacking libnginx-mod-mail (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package libnginx-mod-stream.
aws_instance.example[3] (remote-exec): Preparing to unpack .../14-libnginx-mod-stream_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[3] (remote-exec): Unpacking libnginx-mod-stream (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Created symlink /etc/systemd/system/multi-user.target.wants/nginx.service → /lib/systemd/system/nginx.service.
aws_instance.example[3] (remote-exec): Selecting previously unselected package nginx-core.
aws_instance.example[3] (remote-exec): Preparing to unpack .../15-nginx-core_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[3] (remote-exec): Unpacking nginx-core (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package nginx.
aws_instance.example[3] (remote-exec): Preparing to unpack .../16-nginx_1.17.10-0ubuntu1_all.deb ...
aws_instance.example[3] (remote-exec): Unpacking nginx (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Setting up libxpm4:amd64 (1:3.5.12-1) ...
aws_instance.example[3] (remote-exec): Setting up nginx-common (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Created symlink /etc/systemd/system/multi-user.target.wants/nginx.service → /lib/systemd/system/nginx.service.
aws_instance.example[2] (remote-exec): Setting up libjbig0:amd64 (2.1-3.1build1) ...
aws_instance.example[2] (remote-exec): Setting up libnginx-mod-http-xslt-filter (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Setting up libwebp6:amd64 (0.6.1-2) ...
aws_instance.example[2] (remote-exec): Setting up fonts-dejavu-core (2.37-1) ...
aws_instance.example[2] (remote-exec): Setting up libjpeg-turbo8:amd64 (2.0.3-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Setting up libjpeg8:amd64 (8c-2ubuntu8) ...
aws_instance.example[2] (remote-exec): Setting up libnginx-mod-mail (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Setting up fontconfig-config (2.13.1-2ubuntu3) ...
aws_instance.example[2] (remote-exec): Setting up libnginx-mod-stream (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Setting up libtiff5:amd64 (4.1.0+git191117-2build1) ...
aws_instance.example[2] (remote-exec): Setting up libfontconfig1:amd64 (2.13.1-2ubuntu3) ...
aws_instance.example[2] (remote-exec): Setting up libgd3:amd64 (2.2.5-5.2ubuntu2) ...
aws_instance.example[2] (remote-exec): Setting up libnginx-mod-http-image-filter (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Setting up nginx-core (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Setting up libjbig0:amd64 (2.1-3.1build1) ...
aws_instance.example[3] (remote-exec): Setting up libnginx-mod-http-xslt-filter (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Setting up libwebp6:amd64 (0.6.1-2) ...
aws_instance.example[3] (remote-exec): Setting up fonts-dejavu-core (2.37-1) ...
aws_instance.example[3] (remote-exec): Setting up libjpeg-turbo8:amd64 (2.0.3-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Setting up libjpeg8:amd64 (8c-2ubuntu8) ...
aws_instance.example[3] (remote-exec): Setting up libnginx-mod-mail (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Setting up fontconfig-config (2.13.1-2ubuntu3) ...
aws_instance.example[2] (remote-exec): Setting up nginx (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Processing triggers for ufw (0.36-6) ...
aws_instance.example[3] (remote-exec): Setting up libnginx-mod-stream (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Setting up libtiff5:amd64 (4.1.0+git191117-2build1) ...
aws_instance.example[3] (remote-exec): Setting up libfontconfig1:amd64 (2.13.1-2ubuntu3) ...
aws_instance.example[2] (remote-exec): Processing triggers for systemd (245.4-4ubuntu3) ...
aws_instance.example[3] (remote-exec): Setting up libgd3:amd64 (2.2.5-5.2ubuntu2) ...
aws_instance.example[3] (remote-exec): Setting up libnginx-mod-http-image-filter (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Setting up nginx-core (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Processing triggers for man-db (2.9.1-1) ...
aws_instance.example[3] (remote-exec): Setting up nginx (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Processing triggers for ufw (0.36-6) ...
aws_instance.example[3] (remote-exec): Processing triggers for systemd (245.4-4ubuntu3) ...
aws_instance.example[2] (remote-exec): Processing triggers for libc-bin (2.31-0ubuntu9) ...
aws_instance.example[3] (remote-exec): Processing triggers for man-db (2.9.1-1) ...
aws_instance.example[3] (remote-exec): Processing triggers for libc-bin (2.31-0ubuntu9) ...
aws_instance.example[1]: Creation complete after 1m18s [id=i-0da62c59bcb5aafd1]
aws_instance.example[2]: Creation complete after 1m20s [id=i-042c29ef42628547a]
aws_instance.example[3]: Still creating... [1m20s elapsed]
aws_instance.example[3]: Creation complete after 1m21s [id=i-0622d13dc3215d78e]

Apply complete! Resources: 5 added, 0 changed, 0 destroyed.
            "public_ip": "18.203.100.225",
            "public_ip": "3.250.148.103",
            "public_ip": "3.249.187.15",
            "public_ip": "34.241.193.25",

```


#테라폼 삭제
```
aws_key_pair.mykey: Refreshing state... [id=mykey]
aws_instance.example[0]: Refreshing state... [id=i-01f45219dbbccaac1]
aws_instance.example[1]: Refreshing state... [id=i-0da62c59bcb5aafd1]
aws_instance.example[2]: Refreshing state... [id=i-042c29ef42628547a]
aws_instance.example[3]: Refreshing state... [id=i-0622d13dc3215d78e]
aws_instance.example[0]: Destroying... [id=i-01f45219dbbccaac1]
aws_instance.example[2]: Destroying... [id=i-042c29ef42628547a]
aws_instance.example[1]: Destroying... [id=i-0da62c59bcb5aafd1]
aws_instance.example[3]: Destroying... [id=i-0622d13dc3215d78e]
aws_instance.example[0]: Still destroying... [id=i-01f45219dbbccaac1, 10s elapsed]
aws_instance.example[1]: Still destroying... [id=i-0da62c59bcb5aafd1, 10s elapsed]
aws_instance.example[2]: Still destroying... [id=i-042c29ef42628547a, 10s elapsed]
aws_instance.example[3]: Still destroying... [id=i-0622d13dc3215d78e, 10s elapsed]
aws_instance.example[1]: Still destroying... [id=i-0da62c59bcb5aafd1, 20s elapsed]
aws_instance.example[0]: Still destroying... [id=i-01f45219dbbccaac1, 20s elapsed]
aws_instance.example[2]: Still destroying... [id=i-042c29ef42628547a, 20s elapsed]
aws_instance.example[3]: Still destroying... [id=i-0622d13dc3215d78e, 20s elapsed]
aws_instance.example[2]: Destruction complete after 27s
aws_instance.example[1]: Destruction complete after 27s
aws_instance.example[3]: Still destroying... [id=i-0622d13dc3215d78e, 30s elapsed]
aws_instance.example[0]: Still destroying... [id=i-01f45219dbbccaac1, 30s elapsed]
aws_instance.example[0]: Destruction complete after 39s
aws_instance.example[3]: Still destroying... [id=i-0622d13dc3215d78e, 40s elapsed]
aws_instance.example[3]: Still destroying... [id=i-0622d13dc3215d78e, 50s elapsed]
aws_instance.example[3]: Still destroying... [id=i-0622d13dc3215d78e, 1m0s elapsed]
aws_instance.example[3]: Destruction complete after 1m4s
aws_key_pair.mykey: Destroying... [id=mykey]
aws_key_pair.mykey: Destruction complete after 1s

Destroy complete! Resources: 5 destroyed.

```
