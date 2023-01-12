# Replace Specific Line in SQL files

This script uses the `glob`, `os`, and `fileinput` modules in Python to replace a specific line in multiple SQL files in a folder. 

## Usage

1. Set the directory path where your SQL files are located in the `directory` variable.
2. Set the line that you want to replace in `old_line` variable and the replacement line in `new_line` variable.
3. Run the script.

## Note
- This script will replace the line in place, meaning the original files will be modified.
- Please make sure to make a backup of your files before making any changes.
- This script only works with SQL files, it will not replace the line in any other type of file.
- The script uses `glob` library to get the list of files and then uses `fileinput` module to do the inplace replacement of the line.

## Example
```python
import glob
import os
import fileinput

# Set the directory you want to work with
directory = '/path/to/files'

# Set the line you want to replace and the replacement line
old_line = "old_line"
new_line = "new_line"

# Use glob.glob() to get a list of all the files in the directory
for filepath in glob.glob(os.path.join(directory, '*.sql')):
    if os.path.isfile(filepath):
        for line in fileinput.FileInput(filepath, inplace=True):
            print(line.replace(old_line, new_line), end='')
