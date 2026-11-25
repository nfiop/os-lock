# os-lock

Cross-platform file locking. Uses `fcntl` on UNIX and
`LockFileEx`/`UnlockFileEx` on Windows.

Based on https://github.com/mohd-akram/os-lock codebase.

### API & Arguments

```
int lock(
        int fd, long long start, long long length, bool exclusive,
        bool immediate
);

int unlock(int fd, long long start, long long length);
```

- `fd` - File descriptor.
- `start` - Starting offset for lock.
- `length` - Number of bytes to lock. If 0, lock till end of file.
- `exclusive` - Acquire an exclusive lock (i.e. write lock).
- `immediate` - Throw if a conflicting lock is present instead of waiting.

An error thrown due to `immediate` will have its `code` property set to
`EACCES`, `EAGAIN` or `EBUSY`.



