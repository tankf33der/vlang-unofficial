How to bootstrap vlang (March 2025) on s390x:

Host system:
1. apply bootstrap patch
2. recompile vlang
3. ./v -o /tmp/v.c -cross cmd/v
4. copy v.c file to s390x's /tmp

s390x:
5.