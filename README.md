How to bootstrap vlang (March 2025) on s390x:

Host system:
1. apply bootstrap patch
2. recompile vlang
3. ./v -o /tmp/v.c -cross cmd/v
4. transfer v.c, cheaders.v, comp file to s390x's /tmp

alpine linux s390x:
5. apk add alpine-sdk gc gc-dev
6. export VFLAGS='-cc gcc -d dynamic_boehm'
7. cp /tmp/v.c to vlang's vc/ dir
8. cd to vlang's dir
9. gcc -std=gnu11 -w -o v1 vc/v.c -lm -lpthread
10. ./v1 -version -v
11. no crash? good
12. ./v1 -no-parallel -o v2 cmd/v
13. ./v2 -o v cmd/v
14. rm -rf v1 v2
15. ./v -version -v
16. ./v
17. repl works? good
18. finish
