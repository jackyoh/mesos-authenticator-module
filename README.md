Build module command

```
# g++ -std=gnu++11 -lmesos -fpic -c test_authentication_modules.cpp test_http_authenticator_module.cpp

# g++ -shared -o libauthen.so.1.0.0 test_authentication_modules.o test_http_authenticator_module.o
```
