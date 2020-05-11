1. https://github.com/mogi240/test0511.git 생성 및 clone
2. ~/.bashrc export TF_VAR_AWS_REGION="ap-northeast-2"
3. 서울 리전에 기본 VPC설정
4. 테라폼적용
   ta
   terraform init
   terraform plan
   terraform apply -auto-approve
5.보안그룹에서 http 80포트 인바운드 허용

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
aws_instance.example: Creating...
aws_instance.example: Still creating... [10s elapsed]
aws_instance.example: Still creating... [20s elapsed]
aws_instance.example: Still creating... [30s elapsed]
aws_instance.example: Still creating... [40s elapsed]
aws_instance.example: Provisioning with 'file'...
aws_instance.example: Provisioning with 'remote-exec'...
aws_instance.example (remote-exec): Connecting to remote host via SSH...
aws_instance.example (remote-exec):   Host: 54.229.49.63
aws_instance.example (remote-exec):   User: ubuntu
aws_instance.example (remote-exec):   Password: false
aws_instance.example (remote-exec):   Private key: true
aws_instance.example (remote-exec):   Certificate: false
aws_instance.example (remote-exec):   SSH Agent: false
aws_instance.example (remote-exec):   Checking Host Key: false
aws_instance.example: Still creating... [50s elapsed]
aws_instance.example (remote-exec): Connected!
aws_instance.example (remote-exec): 0% [Working]
aws_instance.example (remote-exec): Get:1 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal InRelease [265 kB]
aws_instance.example (remote-exec): 0% [1 InRelease 0 B/265 kB 0%] [Connect
aws_instance.example (remote-exec): 0% [Connecting to security.ubuntu.com (
aws_instance.example (remote-exec): Get:2 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates InRelease [107 kB]
aws_instance.example (remote-exec): Get:3 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports InRelease [98.3 kB]
aws_instance.example (remote-exec): 0% [Connecting to security.ubuntu.com (
aws_instance.example (remote-exec): 0% [Waiting for headers]
aws_instance.example (remote-exec): Get:4 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 Packages [970 kB]
aws_instance.example (remote-exec): 0% [4 Packages 26.6 kB/970 kB 3%] [Wait
aws_instance.example (remote-exec): 0% [Waiting for headers]
aws_instance.example (remote-exec): Get:5 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main Translation-en [506 kB]
aws_instance.example (remote-exec): 0% [5 Translation-en 25.9 kB/506 kB 5%]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [5 Translatio
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [Waiting for
aws_instance.example (remote-exec): Get:6 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 c-n-f Metadata [29.5 kB]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [6 Commands-a
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [Waiting for
aws_instance.example (remote-exec): Get:7 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe amd64 Packages [8628 kB]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [7 Packages 0
aws_instance.example (remote-exec): Get:8 http://security.ubuntu.com/ubuntu focal-security InRelease [107 kB]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [7 Packages 3
aws_instance.example (remote-exec): Get:9 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe Translation-en [5124 kB]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [9 Translatio
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [9 Translatio
aws_instance.example (remote-exec): Get:10 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe amd64 c-n-f Metadata [265 kB]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [10 Commands-
aws_instance.example (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example (remote-exec): Get:11 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse amd64 Packages [144 kB]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [11 Packages
aws_instance.example (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example (remote-exec): Get:12 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse Translation-en [104 kB]
aws_instance.example (remote-exec): Get:13 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse amd64 c-n-f Metadata [9136 B]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example (remote-exec): Get:14 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [84.4 kB]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [14 Packages
aws_instance.example (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example (remote-exec): Get:15 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main Translation-en [30.2 kB]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [15 Translati
aws_instance.example (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example (remote-exec): Get:16 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main amd64 c-n-f Metadata [1940 B]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [16 Commands-
aws_instance.example (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example (remote-exec): Get:17 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/restricted amd64 Packages [4180 B]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [17 Packages
aws_instance.example (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example (remote-exec): Get:18 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/restricted Translation-en [1360 B]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [18 Translati
aws_instance.example (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example (remote-exec): Get:19 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [27.2 kB]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [19 Packages
aws_instance.example (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example (remote-exec): Get:20 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe Translation-en [13.3 kB]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [20 Translati
aws_instance.example (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example (remote-exec): Get:21 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe amd64 c-n-f Metadata [1132 B]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [21 Commands-
aws_instance.example (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example (remote-exec): Get:22 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 c-n-f Metadata [116 B]
aws_instance.example (remote-exec): 0% [4 Packages store 5827 kB] [22 Comma
aws_instance.example (remote-exec): 0% [4 Packages store 5827 kB]
aws_instance.example (remote-exec): 0% [Working]
aws_instance.example (remote-exec): 0% [5 Translation-en store 0 B]
aws_instance.example (remote-exec): 0% [Working]
aws_instance.example (remote-exec): 0% [6 Commands-amd64 store 0 B]
aws_instance.example (remote-exec): 0% [Working]
aws_instance.example (remote-exec): 0% [7 Packages store 0 B]
aws_instance.example (remote-exec): 0% [7 Packages store 0 B]
aws_instance.example (remote-exec): Get:23 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/main amd64 c-n-f Metadata [112 B]
aws_instance.example (remote-exec): 0% [7 Packages store 0 B]
aws_instance.example (remote-exec): Get:24 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/restricted amd64 c-n-f Metadata [116 B]
aws_instance.example (remote-exec): 0% [7 Packages store 0 B] [Waiting for
aws_instance.example (remote-exec): Get:25 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe amd64 Packages [2792 B]
aws_instance.example (remote-exec): 0% [7 Packages store 0 B] [Waiting for
aws_instance.example (remote-exec): Get:26 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe Translation-en [1280 B]
aws_instance.example (remote-exec): 0% [7 Packages store 0 B] [Waiting for
aws_instance.example (remote-exec): Get:27 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe amd64 c-n-f Metadata [188 B]
aws_instance.example (remote-exec): 0% [7 Packages store 0 B] [Waiting for
aws_instance.example (remote-exec): Get:28 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/multiverse amd64 c-n-f Metadata [116 B]
aws_instance.example (remote-exec): 0% [7 Packages store 0 B]
aws_instance.example (remote-exec): 92% [7 Packages store 0 B]
aws_instance.example (remote-exec): Get:29 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages [50.1 kB]
aws_instance.example (remote-exec): 92% [7 Packages store 0 B] [29 Packages
aws_instance.example (remote-exec): 93% [7 Packages store 0 B]
aws_instance.example (remote-exec): Get:30 http://security.ubuntu.com/ubuntu focal-security/main Translation-en [18.5 kB]
aws_instance.example (remote-exec): 93% [7 Packages store 0 B] [30 Translat
aws_instance.example (remote-exec): Get:31 http://security.ubuntu.com/ubuntu focal-security/main amd64 c-n-f Metadata [1352 B]
aws_instance.example (remote-exec): 93% [7 Packages store 0 B] [Waiting for
aws_instance.example (remote-exec): Get:32 http://security.ubuntu.com/ubuntu focal-security/restricted amd64 Packages [4180 B]
aws_instance.example (remote-exec): 93% [7 Packages store 0 B] [32 Packages
aws_instance.example (remote-exec): Get:33 http://security.ubuntu.com/ubuntu focal-security/restricted Translation-en [1360 B]
aws_instance.example (remote-exec): 93% [7 Packages store 0 B] [33 Translat
aws_instance.example (remote-exec): Get:34 http://security.ubuntu.com/ubuntu focal-security/universe amd64 Packages [7548 B]
aws_instance.example (remote-exec): 93% [7 Packages store 0 B] [34 Packages
aws_instance.example (remote-exec): Get:35 http://security.ubuntu.com/ubuntu focal-security/universe Translation-en [5636 B]
aws_instance.example (remote-exec): 93% [7 Packages store 0 B] [35 Translat
aws_instance.example (remote-exec): Get:36 http://security.ubuntu.com/ubuntu focal-security/universe amd64 c-n-f Metadata [608 B]
aws_instance.example (remote-exec): Get:37 http://security.ubuntu.com/ubuntu focal-security/multiverse amd64 c-n-f Metadata [116 B]
aws_instance.example (remote-exec): 93% [7 Packages store 0 B]
aws_instance.example (remote-exec): 93% [7 Packages store 0 B]
aws_instance.example (remote-exec): 93% [Working]
aws_instance.example (remote-exec): 93% [9 Translation-en store 0 B]
aws_instance.example (remote-exec): 93% [9 Translation-en store 0 B]
aws_instance.example (remote-exec): 93% [Working]
aws_instance.example (remote-exec): 93% [10 Commands-amd64 store 0 B]
aws_instance.example (remote-exec): 94% [Working]
aws_instance.example (remote-exec): 94% [11 Packages store 0 B]
aws_instance.example (remote-exec): 94% [Working]
aws_instance.example (remote-exec): 94% [12 Translation-en store 0 B]
aws_instance.example (remote-exec): 94% [Working]
aws_instance.example (remote-exec): 94% [13 Commands-amd64 store 0 B]
aws_instance.example (remote-exec): 94% [Working]
aws_instance.example (remote-exec): 94% [14 Packages store 0 B]
aws_instance.example (remote-exec): 95% [Working]
aws_instance.example (remote-exec): 95% [15 Translation-en store 0 B]
aws_instance.example (remote-exec): 95% [Working]
aws_instance.example (remote-exec): 95% [16 Commands-amd64 store 0 B]
aws_instance.example (remote-exec): 95% [Working]
aws_instance.example (remote-exec): 95% [17 Packages store 0 B]
aws_instance.example (remote-exec): 95% [Working]
aws_instance.example (remote-exec): 95% [18 Translation-en store 0 B]
aws_instance.example (remote-exec): 95% [Working]
aws_instance.example (remote-exec): 95% [19 Packages store 0 B]
aws_instance.example (remote-exec): 96% [Working]
aws_instance.example (remote-exec): 96% [20 Translation-en store 0 B]
aws_instance.example (remote-exec): 96% [Working]
aws_instance.example (remote-exec): 96% [21 Commands-amd64 store 0 B]
aws_instance.example (remote-exec): 96% [Working]
aws_instance.example (remote-exec): 96% [22 Commands-amd64 store 0 B]
aws_instance.example (remote-exec): 96% [Working]
aws_instance.example (remote-exec): 96% [23 Commands-amd64 store 0 B]
aws_instance.example (remote-exec): 97% [Working]
aws_instance.example (remote-exec): 97% [24 Commands-amd64 store 0 B]
aws_instance.example (remote-exec): 97% [Working]
aws_instance.example (remote-exec): 97% [25 Packages store 0 B]
aws_instance.example (remote-exec): 97% [Working]
aws_instance.example (remote-exec): 97% [26 Translation-en store 0 B]
aws_instance.example (remote-exec): 97% [Working]
aws_instance.example (remote-exec): 97% [27 Commands-amd64 store 0 B]
aws_instance.example (remote-exec): 98% [Working]
aws_instance.example (remote-exec): 98% [28 Commands-amd64 store 0 B]
aws_instance.example (remote-exec): 98% [Working]
aws_instance.example (remote-exec): 98% [29 Packages store 0 B]
aws_instance.example (remote-exec): 98% [Working]
aws_instance.example (remote-exec): 98% [30 Translation-en store 0 B]
aws_instance.example (remote-exec): 98% [Working]
aws_instance.example (remote-exec): 98% [31 Commands-amd64 store 0 B]
aws_instance.example (remote-exec): 99% [Working]
aws_instance.example (remote-exec): 99% [32 Packages store 0 B]
aws_instance.example (remote-exec): 99% [Working]
aws_instance.example (remote-exec): 99% [33 Translation-en store 0 B]
aws_instance.example (remote-exec): 99% [Working]
aws_instance.example (remote-exec): 99% [34 Packages store 0 B]
aws_instance.example (remote-exec): 99% [Working]
aws_instance.example (remote-exec): 99% [35 Translation-en store 0 B]
aws_instance.example (remote-exec): 100% [Working]
aws_instance.example (remote-exec): 100% [36 Commands-amd64 store 0 B]
aws_instance.example (remote-exec): 100% [Working]
aws_instance.example (remote-exec): 100% [37 Commands-amd64 store 0 B]
aws_instance.example (remote-exec): 100% [Working]
aws_instance.example (remote-exec): Fetched 16.6 MB in 3s (5914 kB/s)
aws_instance.example: Still creating... [1m0s elapsed]
aws_instance.example (remote-exec): Reading package lists... 0%
aws_instance.example (remote-exec): Reading package lists... 0%
aws_instance.example (remote-exec): Reading package lists... 0%
aws_instance.example (remote-exec): Reading package lists... 6%
aws_instance.example (remote-exec): Reading package lists... 6%
aws_instance.example (remote-exec): Reading package lists... 9%
aws_instance.example (remote-exec): Reading package lists... 9%
aws_instance.example (remote-exec): Reading package lists... 10%
aws_instance.example (remote-exec): Reading package lists... 10%
aws_instance.example (remote-exec): Reading package lists... 10%
aws_instance.example (remote-exec): Reading package lists... 10%
aws_instance.example (remote-exec): Reading package lists... 66%
aws_instance.example (remote-exec): Reading package lists... 66%
aws_instance.example (remote-exec): Reading package lists... 96%
aws_instance.example (remote-exec): Reading package lists... 96%
aws_instance.example (remote-exec): Reading package lists... 97%
aws_instance.example (remote-exec): Reading package lists... 97%
aws_instance.example (remote-exec): Reading package lists... 97%
aws_instance.example (remote-exec): Reading package lists... 97%
aws_instance.example (remote-exec): Reading package lists... 98%
aws_instance.example (remote-exec): Reading package lists... 98%
aws_instance.example (remote-exec): Reading package lists... 98%
aws_instance.example (remote-exec): Reading package lists... 98%
aws_instance.example (remote-exec): Reading package lists... 98%
aws_instance.example (remote-exec): Reading package lists... 98%
aws_instance.example (remote-exec): Reading package lists... 98%
aws_instance.example (remote-exec): Reading package lists... 98%
aws_instance.example (remote-exec): Reading package lists... 98%
aws_instance.example (remote-exec): Reading package lists... 98%
aws_instance.example (remote-exec): Reading package lists... 98%
aws_instance.example (remote-exec): Reading package lists... 98%
aws_instance.example (remote-exec): Reading package lists... 98%
aws_instance.example (remote-exec): Reading package lists... 98%
aws_instance.example (remote-exec): Reading package lists... 98%
aws_instance.example (remote-exec): Reading package lists... 98%
aws_instance.example (remote-exec): Reading package lists... 99%
aws_instance.example (remote-exec): Reading package lists... 99%
aws_instance.example (remote-exec): Reading package lists... 99%
aws_instance.example (remote-exec): Reading package lists... 99%
aws_instance.example (remote-exec): Reading package lists... 99%
aws_instance.example (remote-exec): Reading package lists... 99%
aws_instance.example (remote-exec): Reading package lists... 99%
aws_instance.example (remote-exec): Reading package lists... 99%
aws_instance.example (remote-exec): Reading package lists... 99%
aws_instance.example (remote-exec): Reading package lists... 99%
aws_instance.example (remote-exec): Reading package lists... 99%
aws_instance.example (remote-exec): Reading package lists... 99%
aws_instance.example (remote-exec): Reading package lists... Done
aws_instance.example (remote-exec): Reading package lists... 0%
aws_instance.example (remote-exec): Reading package lists... 100%
aws_instance.example (remote-exec): Reading package lists... Done
aws_instance.example (remote-exec): Building dependency tree... 0%
aws_instance.example (remote-exec): Building dependency tree... 0%
aws_instance.example (remote-exec): Building dependency tree... 50%
aws_instance.example (remote-exec): Building dependency tree... 50%
aws_instance.example (remote-exec): Building dependency tree
aws_instance.example (remote-exec): Reading state information... 0%
aws_instance.example (remote-exec): Reading state information... 0%
aws_instance.example (remote-exec): Reading state information... Done
aws_instance.example (remote-exec): The following additional packages will be installed:
aws_instance.example (remote-exec):   fontconfig-config fonts-dejavu-core
aws_instance.example (remote-exec):   libfontconfig1 libgd3 libjbig0
aws_instance.example (remote-exec):   libjpeg-turbo8 libjpeg8
aws_instance.example (remote-exec):   libnginx-mod-http-image-filter
aws_instance.example (remote-exec):   libnginx-mod-http-xslt-filter
aws_instance.example (remote-exec):   libnginx-mod-mail
aws_instance.example (remote-exec):   libnginx-mod-stream libtiff5
aws_instance.example (remote-exec):   libwebp6 libxpm4 nginx-common
aws_instance.example (remote-exec):   nginx-core
aws_instance.example (remote-exec): Suggested packages:
aws_instance.example (remote-exec):   libgd-tools fcgiwrap nginx-doc
aws_instance.example (remote-exec):   ssl-cert
aws_instance.example (remote-exec): The following NEW packages will be installed:
aws_instance.example (remote-exec):   fontconfig-config fonts-dejavu-core
aws_instance.example (remote-exec):   libfontconfig1 libgd3 libjbig0
aws_instance.example (remote-exec):   libjpeg-turbo8 libjpeg8
aws_instance.example (remote-exec):   libnginx-mod-http-image-filter
aws_instance.example (remote-exec):   libnginx-mod-http-xslt-filter
aws_instance.example (remote-exec):   libnginx-mod-mail
aws_instance.example (remote-exec):   libnginx-mod-stream libtiff5
aws_instance.example (remote-exec):   libwebp6 libxpm4 nginx nginx-common
aws_instance.example (remote-exec):   nginx-core

aws_instance.example (remote-exec): 0 upgraded, 17 newly installed, 0 to remove and 21 not upgraded.
aws_instance.example (remote-exec): Need to get 2431 kB of archives.
aws_instance.example (remote-exec): After this operation, 7891 kB of additional disk space will be used.
aws_instance.example (remote-exec): 0% [Working]
aws_instance.example (remote-exec): Get:1 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 fonts-dejavu-core all 2.37-1 [1041 kB]
aws_instance.example (remote-exec): 0% [1 fonts-dejavu-core 0 B/1041 kB 0%]
aws_instance.example (remote-exec): 35% [Working]
aws_instance.example (remote-exec): Get:2 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 fontconfig-config all 2.13.1-2ubuntu3 [28.8 kB]
aws_instance.example (remote-exec): 35% [2 fontconfig-config 0 B/28.8 kB 0%
aws_instance.example (remote-exec): 38% [Working]
aws_instance.example (remote-exec): Get:3 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libfontconfig1 amd64 2.13.1-2ubuntu3 [114 kB]
aws_instance.example (remote-exec): 38% [3 libfontconfig1 0 B/114 kB 0%]
aws_instance.example (remote-exec): 42% [Working]
aws_instance.example (remote-exec): Get:4 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjpeg-turbo8 amd64 2.0.3-0ubuntu1 [118 kB]
aws_instance.example (remote-exec): 42% [4 libjpeg-turbo8 0 B/118 kB 0%]
aws_instance.example (remote-exec): 48% [Working]
aws_instance.example (remote-exec): Get:5 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjpeg8 amd64 8c-2ubuntu8 [2194 B]
aws_instance.example (remote-exec): 48% [5 libjpeg8 0 B/2194 B 0%]
aws_instance.example (remote-exec): 49% [Working]
aws_instance.example (remote-exec): Get:6 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjbig0 amd64 2.1-3.1build1 [26.7 kB]
aws_instance.example (remote-exec): 49% [6 libjbig0 0 B/26.7 kB 0%]
aws_instance.example (remote-exec): 51% [Working]
aws_instance.example (remote-exec): Get:7 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libwebp6 amd64 0.6.1-2 [185 kB]
aws_instance.example (remote-exec): 51% [7 libwebp6 0 B/185 kB 0%]
aws_instance.example (remote-exec): 58% [Working]
aws_instance.example (remote-exec): Get:8 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libtiff5 amd64 4.1.0+git191117-2build1 [161 kB]
aws_instance.example (remote-exec): 58% [8 libtiff5 0 B/161 kB 0%]
aws_instance.example (remote-exec): 65% [Working]
aws_instance.example (remote-exec): Get:9 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libxpm4 amd64 1:3.5.12-1 [34.0 kB]
aws_instance.example (remote-exec): 65% [9 libxpm4 0 B/34.0 kB 0%]
aws_instance.example (remote-exec): 67% [Working]
aws_instance.example (remote-exec): Get:10 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libgd3 amd64 2.2.5-5.2ubuntu2 [118 kB]
aws_instance.example (remote-exec): 67% [10 libgd3 0 B/118 kB 0%]
aws_instance.example (remote-exec): 72% [Working]
aws_instance.example (remote-exec): Get:11 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx-common all 1.17.10-0ubuntu1 [37.3 kB]
aws_instance.example (remote-exec): 72% [11 nginx-common 0 B/37.3 kB 0%]
aws_instance.example (remote-exec): 74% [Working]
aws_instance.example (remote-exec): Get:12 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-http-image-filter amd64 1.17.10-0ubuntu1 [14.3 kB]
aws_instance.example (remote-exec): 74% [12 libnginx-mod-http-image-filter
aws_instance.example (remote-exec): 76% [Working]
aws_instance.example (remote-exec): Get:13 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-http-xslt-filter amd64 1.17.10-0ubuntu1 [12.5 kB]
aws_instance.example (remote-exec): 76% [13 libnginx-mod-http-xslt-filter 0
aws_instance.example (remote-exec): 78% [Working]
aws_instance.example (remote-exec): Get:14 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-mail amd64 1.17.10-0ubuntu1 [42.3 kB]
aws_instance.example (remote-exec): 78% [14 libnginx-mod-mail 0 B/42.3 kB 0
aws_instance.example (remote-exec): 80% [Working]
aws_instance.example (remote-exec): Get:15 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-stream amd64 1.17.10-0ubuntu1 [66.9 kB]
aws_instance.example (remote-exec): 80% [15 libnginx-mod-stream 0 B/66.9 kB
aws_instance.example (remote-exec): 84% [Working]
aws_instance.example (remote-exec): Get:16 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx-core amd64 1.17.10-0ubuntu1 [425 kB]
aws_instance.example (remote-exec): 84% [16 nginx-core 0 B/425 kB 0%]
aws_instance.example (remote-exec): 99% [Working]
aws_instance.example (remote-exec): Get:17 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx all 1.17.10-0ubuntu1 [3616 B]
aws_instance.example (remote-exec): 99% [17 nginx 0 B/3616 B 0%]
aws_instance.example (remote-exec): 100% [Working]
aws_instance.example (remote-exec): Fetched 2431 kB in 0s (33.7 MB/s)
aws_instance.example (remote-exec): Preconfiguring packages ...
aws_instance.example (remote-exec): Selecting previously unselected package fonts-dejavu-core.
aws_instance.example (remote-exec): (Reading database ...
aws_instance.example (remote-exec): (Reading database ... 5%
aws_instance.example (remote-exec): (Reading database ... 10%
aws_instance.example (remote-exec): (Reading database ... 15%
aws_instance.example (remote-exec): (Reading database ... 20%
aws_instance.example (remote-exec): (Reading database ... 25%
aws_instance.example (remote-exec): (Reading database ... 30%
aws_instance.example (remote-exec): (Reading database ... 35%
aws_instance.example (remote-exec): (Reading database ... 40%
aws_instance.example (remote-exec): (Reading database ... 45%
aws_instance.example (remote-exec): (Reading database ... 50%
aws_instance.example (remote-exec): (Reading database ... 55%
aws_instance.example (remote-exec): (Reading database ... 60%
aws_instance.example (remote-exec): (Reading database ... 65%
aws_instance.example (remote-exec): (Reading database ... 70%
aws_instance.example (remote-exec): (Reading database ... 75%
aws_instance.example (remote-exec): (Reading database ... 80%
aws_instance.example (remote-exec): (Reading database ... 85%
aws_instance.example (remote-exec): (Reading database ... 90%
aws_instance.example (remote-exec): (Reading database ... 95%
aws_instance.example (remote-exec): (Reading database ... 100%
aws_instance.example (remote-exec): (Reading database ... 59604 files and directories currently installed.)
aws_instance.example (remote-exec): Preparing to unpack .../00-fonts-dejavu-core_2.37-1_all.deb ...
aws_instance.example (remote-exec): Unpacking fonts-dejavu-core (2.37-1) ...
aws_instance.example (remote-exec): Selecting previously unselected package fontconfig-config.
aws_instance.example (remote-exec): Preparing to unpack .../01-fontconfig-config_2.13.1-2ubuntu3_all.deb ...
aws_instance.example (remote-exec): Unpacking fontconfig-config (2.13.1-2ubuntu3) ...
aws_instance.example (remote-exec): Selecting previously unselected package libfontconfig1:amd64.
aws_instance.example (remote-exec): Preparing to unpack .../02-libfontconfig1_2.13.1-2ubuntu3_amd64.deb ...
aws_instance.example (remote-exec): Unpacking libfontconfig1:amd64 (2.13.1-2ubuntu3) ...
aws_instance.example (remote-exec): Selecting previously unselected package libjpeg-turbo8:amd64.
aws_instance.example (remote-exec): Preparing to unpack .../03-libjpeg-turbo8_2.0.3-0ubuntu1_amd64.deb ...
aws_instance.example (remote-exec): Unpacking libjpeg-turbo8:amd64 (2.0.3-0ubuntu1) ...
aws_instance.example (remote-exec): Selecting previously unselected package libjpeg8:amd64.
aws_instance.example (remote-exec): Preparing to unpack .../04-libjpeg8_8c-2ubuntu8_amd64.deb ...
aws_instance.example (remote-exec): Unpacking libjpeg8:amd64 (8c-2ubuntu8) ...
aws_instance.example (remote-exec): Selecting previously unselected package libjbig0:amd64.
aws_instance.example (remote-exec): Preparing to unpack .../05-libjbig0_2.1-3.1build1_amd64.deb ...
aws_instance.example (remote-exec): Unpacking libjbig0:amd64 (2.1-3.1build1) ...
aws_instance.example (remote-exec): Selecting previously unselected package libwebp6:amd64.
aws_instance.example (remote-exec): Preparing to unpack .../06-libwebp6_0.6.1-2_amd64.deb ...
aws_instance.example (remote-exec): Unpacking libwebp6:amd64 (0.6.1-2) ...
aws_instance.example (remote-exec): Selecting previously unselected package libtiff5:amd64.
aws_instance.example (remote-exec): Preparing to unpack .../07-libtiff5_4.1.0+git191117-2build1_amd64.deb ...
aws_instance.example (remote-exec): Unpacking libtiff5:amd64 (4.1.0+git191117-2build1) ...
aws_instance.example (remote-exec): Selecting previously unselected package libxpm4:amd64.
aws_instance.example (remote-exec): Preparing to unpack .../08-libxpm4_1%3a3.5.12-1_amd64.deb ...
aws_instance.example (remote-exec): Unpacking libxpm4:amd64 (1:3.5.12-1) ...
aws_instance.example (remote-exec): Selecting previously unselected package libgd3:amd64.
aws_instance.example (remote-exec): Preparing to unpack .../09-libgd3_2.2.5-5.2ubuntu2_amd64.deb ...
aws_instance.example (remote-exec): Unpacking libgd3:amd64 (2.2.5-5.2ubuntu2) ...
aws_instance.example (remote-exec): Selecting previously unselected package nginx-common.
aws_instance.example (remote-exec): Preparing to unpack .../10-nginx-common_1.17.10-0ubuntu1_all.deb ...
aws_instance.example (remote-exec): Unpacking nginx-common (1.17.10-0ubuntu1) ...
aws_instance.example (remote-exec): Selecting previously unselected package libnginx-mod-http-image-filter.
aws_instance.example (remote-exec): Preparing to unpack .../11-libnginx-mod-http-image-filter_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example (remote-exec): Unpacking libnginx-mod-http-image-filter (1.17.10-0ubuntu1) ...
aws_instance.example (remote-exec): Selecting previously unselected package libnginx-mod-http-xslt-filter.
aws_instance.example (remote-exec): Preparing to unpack .../12-libnginx-mod-http-xslt-filter_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example (remote-exec): Unpacking libnginx-mod-http-xslt-filter (1.17.10-0ubuntu1) ...
aws_instance.example (remote-exec): Selecting previously unselected package libnginx-mod-mail.
aws_instance.example (remote-exec): Preparing to unpack .../13-libnginx-mod-mail_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example (remote-exec): Unpacking libnginx-mod-mail (1.17.10-0ubuntu1) ...
aws_instance.example (remote-exec): Selecting previously unselected package libnginx-mod-stream.
aws_instance.example (remote-exec): Preparing to unpack .../14-libnginx-mod-stream_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example (remote-exec): Unpacking libnginx-mod-stream (1.17.10-0ubuntu1) ...
aws_instance.example (remote-exec): Selecting previously unselected package nginx-core.
aws_instance.example (remote-exec): Preparing to unpack .../15-nginx-core_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example (remote-exec): Unpacking nginx-core (1.17.10-0ubuntu1) ...
aws_instance.example (remote-exec): Selecting previously unselected package nginx.
aws_instance.example (remote-exec): Preparing to unpack .../16-nginx_1.17.10-0ubuntu1_all.deb ...
aws_instance.example (remote-exec): Unpacking nginx (1.17.10-0ubuntu1) ...
aws_instance.example (remote-exec): Setting up libxpm4:amd64 (1:3.5.12-1) ...
aws_instance.example (remote-exec): Setting up nginx-common (1.17.10-0ubuntu1) ...
aws_instance.example (remote-exec): Created symlink /etc/systemd/system/multi-user.target.wants/nginx.service → /lib/systemd/system/nginx.service.
aws_instance.example (remote-exec): Setting up libjbig0:amd64 (2.1-3.1build1) ...
aws_instance.example (remote-exec): Setting up libnginx-mod-http-xslt-filter (1.17.10-0ubuntu1) ...
aws_instance.example (remote-exec): Setting up libwebp6:amd64 (0.6.1-2) ...
aws_instance.example (remote-exec): Setting up fonts-dejavu-core (2.37-1) ...
aws_instance.example (remote-exec): Setting up libjpeg-turbo8:amd64 (2.0.3-0ubuntu1) ...
aws_instance.example (remote-exec): Setting up libjpeg8:amd64 (8c-2ubuntu8) ...
aws_instance.example (remote-exec): Setting up libnginx-mod-mail (1.17.10-0ubuntu1) ...
aws_instance.example (remote-exec): Setting up fontconfig-config (2.13.1-2ubuntu3) ...
aws_instance.example (remote-exec): Setting up libnginx-mod-stream (1.17.10-0ubuntu1) ...
aws_instance.example (remote-exec): Setting up libtiff5:amd64 (4.1.0+git191117-2build1) ...
aws_instance.example (remote-exec): Setting up libfontconfig1:amd64 (2.13.1-2ubuntu3) ...
aws_instance.example (remote-exec): Setting up libgd3:amd64 (2.2.5-5.2ubuntu2) ...
aws_instance.example (remote-exec): Setting up libnginx-mod-http-image-filter (1.17.10-0ubuntu1) ...
aws_instance.example (remote-exec): Setting up nginx-core (1.17.10-0ubuntu1) ...
aws_instance.example (remote-exec): Setting up nginx (1.17.10-0ubuntu1) ...
aws_instance.example (remote-exec): Processing triggers for ufw (0.36-6) ...
aws_instance.example (remote-exec): Processing triggers for systemd (245.4-4ubuntu3) ...
aws_instance.example (remote-exec): Processing triggers for man-db (2.9.1-1) ...
aws_instance.example (remote-exec): Processing triggers for libc-bin (2.31-0ubuntu9) ...
aws_instance.example: Still creating... [1m10s elapsed]
aws_instance.example: Creation complete after 1m14s [id=i-0af60ba249b89ad70]

Apply complete! Resources: 2 added, 0 changed, 0 destroyed.
            "public_ip": "54.229.49.63",

```
#테라폼 삭제
```
```
