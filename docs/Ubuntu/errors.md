## Convert files to encoding

If you have problems withs files encoding

Install `convmv`: `sudo apt-get install convmv`

`convmv -r --notest -f windows-1251 -t UTF-8 *`

- `windows-1251` initial encoding
- `UTF-8` final encoding
- `*` all files