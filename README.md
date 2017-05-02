Proptobuf install command
```
#wget https://github.com/google/protobuf/releases/download/v2.6.1/protobuf-2.6.1.tar.gz
# tar zxvf protobuf-2.6.1.tar.gz
# cd protobuf-2.6.1
# ./configure
# make
# make install

```
Install 3rdparty command
```
# yum install -y glog-devel gflags-devel boost-devel
```

Build module command

```
# g++ -std=gnu++11 -lmesos -fpic -c test_authentication_modules.cpp test_http_authenticator_module.cpp
# g++ -shared -o libauthen.so.1.0.0 test_authentication_modules.o test_http_authenticator_module.o
```

RUN Mesos master command
```
# mesos-master --ip=192.168.1.80 --work_dir=/tmp/mesos1 --acls=file:///home/user1/auth/acl --authenticate_http_readonly --authenticate_agents --credentials=file:///home/user1/auth/credentials --modules=file:///home/user1/module/module.json --authenticators=org_apache_mesos_TestCRAMMD5Authenticator --http_authenticators=org_apache_mesos_TestHttpBasicAuthenticator

```

RUN Mesos agent command
```
# mesos-agent --master=192.168.1.80:5050 --work_dir=/tmp/mesos2 --credential=/home/user1/auth/agent_credential --authenticatee=org_apache_mesos_TestCRAMMD5Authenticatee --modules=file:///home/user1/module/module.json
```
