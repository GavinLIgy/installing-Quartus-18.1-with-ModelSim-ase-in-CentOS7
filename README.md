# Installing-Quartus-18.1-with-ModelSim-ase-in-CentOS7(Not finish yet)

I am a starter for linux and it is my first time to have a project with Quartus 18.1. However, when installing Quartus 18.1 with ModelSim there are a lot of bugs. I am writting to take a log for record a possible solution on these bugs.

My environment: CentOS Linux 7 with VMware

The first guideline is https://tingzhili.wordpress.com/2016/03/31/install-notes-for-quartus-15-1-0-under-centos-7/. This guildline guides me installing the Quartus 18.1 successfully. However, when intalling the ModelSim, plently of bugs came.

The first problem is one of the 32 bit libraries cannot be found by yum. In the above guideline,

          9. In order to make ModelSim work properly in CentOS 7 64 bit, the following libraries need to be installed.
               $ sudo yum -y install glibc.i686
               $ sudo yum install libXft-2.3.2-2.el7.i686
               $ sudo yum install libXext-1.3.3-3.el7.i686
               $ sudo yum install ncurses-libs-5.9-13.20130511.el7.i686

First 3 libraries is fine, but the last one is error. The error output is : No package ncurses-libs-5.9-13.20130511.el7.i686 available.

My solution is downloading the package by myself. The ncurses-libs-5.9-13.20130511.el7.i686 can be downloaded from http://rpm.pbone.net/index.php3/stat/4/idpl/27386143/dir/scientific_linux_7/com/ncurses-libs-5.9-13.20130511.el7.i686.rpm.html.

However, our ncurses-libs-5.9-13.20130511.el7.i686 requires ncurses-base = 5.9-13.20130511.el7 library. This library you can also download from the above link.

Tips: if you have a .src.rpm package, please use rpmbuild tool to compile and install.

The second problem is : when I use ./bin/vsim, there is an error that "while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory."


