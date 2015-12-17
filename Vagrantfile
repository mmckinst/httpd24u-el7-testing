Vagrant.configure(2) do |config|
  config.vm.box = "bento/centos-7.1"

  config.vm.provision "shell", inline: <<-SHELL
    wget -nv -P /etc/yum.repos.d/ 'https://copr.fedoraproject.org/coprs/mmckinst/apr15u/repo/epel-7/mmckinst-apr15u-epel-7.repo'
    wget -nv -P /etc/yum.repos.d/ 'https://copr.fedoraproject.org/coprs/mmckinst/apr15u-util/repo/epel-7/mmckinst-apr15u-util-epel-7.repo'
    wget -nv -P /etc/yum.repos.d/ 'https://copr.fedoraproject.org/coprs/mmckinst/httpd24u/repo/epel-7/mmckinst-httpd24u-epel-7.repo'
    yum -y install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
    yum -y install httpd24u

    echo 'Protocols h2 http/1.1' >> /etc/httpd/conf/httpd.conf
    echo 'Protocols h2c http/1.1' >> /etc/httpd/conf/httpd.conf

    systemctl enable httpd
    systemctl start httpd
  SHELL

  config.vm.network "forwarded_port", guest: 80, host: 8080

end
