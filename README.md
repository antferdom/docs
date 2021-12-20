# Automatic markdown files rendering

The target file must be in the current working directory as the command will be relative to it.

```bash
$ ls *.md | entr -r pandoc <file_name>.md --pdf-engine=<compiler> -o <file_name>.<output_file_extension> 
```
