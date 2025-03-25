How to bootstrap vlang (March 2025) on s390x:

```
Host system:
1. patch -p1 < bootstrap.patch
2. recompile vlang
3. ./v -o /tmp/v.c -cross cmd/v
4. transfer v.c, cheaders.v, comptime.v files to s390x's /tmp
5. go to s390x machine

alpine linux s390x:
6. apk add alpine-sdk gc gc-dev
7. export VFLAGS='-cc gcc -d dynamic_boehm'
8. cp /tmp/v.c to vlang's vc/ dir
9. cp /tmp/cheaders.v to vlib/v/gen/c
10. cp /tmp/comptime.v to vlib/v/gen/c
11. cd to vlang's dir
12. gcc -std=gnu11 -w -o v1 vc/v.c -lm -lpthread
13. ./v1 -version -v
14. no crash? good
15. ./v1 -no-parallel -o v2 cmd/v
16. ./v2 -o v cmd/v
17. rm -rf v1 v2
18. ./v -version -v
19. ./v
20. repl works? good
21. finish
```
