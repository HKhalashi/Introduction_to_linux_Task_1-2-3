## Task 1: File Renamer Script

This script renames files by inserting a specified suffix before the file extension.

### Usage

```bash
./rename.sh [options] <suffix> [--] <file1> <file2> ...
```

### Options

- `-h`: Display the help message, including usage, syntax, and supported options.
- `-d`: Dry run mode. Prints the old and new file names without performing the renaming.
- `-v`: Verbose mode. Prints the old and new file names during the renaming process.
- `--`: Separator between options and the list of files.

### Example

```bash
./rename.sh -v sfx -- file1.txt file2.doc file3
```

- `file1.txt` -> `file1sfx.txt`
- `file2.doc` -> `file2sfx.doc`
- `file3` -> `file3sfx`

### Important Notes

- The script supports file names and suffixes that contain shell metacharacters, including wildcards and names starting with a hyphen (`-`).
- If the suffix or file names are not provided or incorrect options are used, the script will print an error message and exit with a non-zero status.

## Task 2: User Home Directory Finder Script

This script finds the home directory of a specified user by analyzing a system's configuration file.

### Usage

```bash
userhome [-f file] [login]
```

### Parameters

- `-f file`: Specify the configuration file to analyze. If not provided, `/etc/passwd` is used by default.
- `login`: Specify the user's login name. If not provided, the script returns the current user's home directory.

### Examples

Find the home directory of a specific user using a custom file:

```bash
userhome -f /mnt/sysroot/etc/passwd userlogin
```
Output: `/home/userlogin`

Find the current user's home directory using the default file:

```bash
userhome
```
Output: `/home/currentuser`

### Exit Status Codes

- `0`: Success, home directory found.
- `1`: Login not found.
- `2`: Specified file not found.

### Error Handling

- If the login is not found, an error message is printed to `stderr` and the script exits with status `1`.
- If the specified file does not exist, an error message is printed to `stderr` and the script exits with status `2`.

## Task 3: Top N Largest Files Finder Script

This script finds and lists the top N largest files larger than a specified size within a given directory and its subdirectories.

### Usage

```bash
topsize [--help] [-h] [-N] [-s minsize] [--] [dir]
```

### Parameters

- `--help`: Print help message and exit.
- `-N`: Number of files to display. If not specified, all files are listed.
- `-s minsize`: Minimum file size to include in the output. Default is 1 byte.
- `-h`: Display file sizes in human-readable format (e.g., KiB, MiB).
- `dir`: Directory to search. If not specified, the current directory is used.
- `--`: Separator for options and directory name, useful if the directory name starts with a hyphen (`-`).

### Examples

Find the top 10 largest files larger than 512 bytes in `/home/user`:

```bash
topsize -10 -s 512 /home/user
```

Find the top 5 largest files larger than 1 byte in a directory named `-10`:

```bash
topsize -5 -- -10
```

### Exit Status Codes

- `0`: Success.
- `1`: Directory not found.
- `2`: Invalid minimum size specified.
- `3`: Invalid option provided.

### Error Handling

- The script handles common errors, such as invalid options, missing directories, and invalid size values, by printing appropriate error messages and exiting with a non-zero status.

