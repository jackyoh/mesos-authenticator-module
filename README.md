Protobuf use the 2.6.1

```
# yum install -y glog-devel gflags-devel
```
Build module command
```
# g++ -std=gnu++11 -lmesos -fpic -c test_authentication_modules.cpp
# g++ -shared -o libauthen.so.1.0.0 test_authentication_modules.o
```

Run mesos master command for load module
```
# mesos-master --ip=192.168.1.9 --work_dir=/tmp/mesos7 --acls=file:///home/user1/auth1/acl --authenticate_http_readonly --authenticate_agents --credentials=file:///home/user1/auth1/credentials --modules='{"libraries":[{"file":"/home/user1/module/libauthen.so.1.0.0", "modules":[{"name":"org_apache_mesos_TestCRAMMD5Authenticator"}]}]}' --authenticators=org_apache_mesos_TestCRAMMD5Authenticator

```
