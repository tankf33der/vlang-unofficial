How to bootstrap vlang (March 2025) on s390x:

Host system:
1. apply bootstrap patch
2. recompile vlang
3. ./v -o /tmp/v.c -cross cmd/v
4. transfer v.c, cheaders.v, comp file to s390x's /tmp
5. go to s390x machine
6. apk add alpine-sdk gc gc-dev
7. export VFLAGS='-cc gcc -d dynamic_boehm'
8. cp /tmp/v.c to vlang's vc/ dir

9. cd to vlang's dir
10. gcc -std=gnu11 -w -o v1 vc/v.c -lm -lpthread
11. ./v1 -version -v
12. no crash? good
13. ./v1 -no-parallel -o v2 cmd/v
14. ./v2 -o v cmd/v
15. rm -rf v1 v2
16. ./v -version -v
17. ./v
18. repl works? good
19. finish
