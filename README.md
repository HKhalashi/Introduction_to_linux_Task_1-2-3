# Topsize
**topsize** prints top N largest (top size) files larger
than the specified size in the given directory and all its
subdirectories. the output contains file size and file path,
one file per line, descending order.

```
topsize [--help] [-h] [-N] [-s minsize] [--] [dir]
```

where
- --help - prints help and exit
- -N number of files (prints all files, if not given)
- -s minsize - minimal file size (1 byte, if not given)
- -h - prints human-readable size
- dir - lookup directory
- -- - option and non-option argument separator
