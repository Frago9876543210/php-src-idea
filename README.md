# php-src-idea

Based on [using CLion with php-src](https://dev.to/ramsey/using-clion-with-php-src-4me0)

```bash
cd /mnt/tmpfs
pip3 install compiledb

git clone --depth=1 https://github.com/php/php-src.git
cd php-src
./buildconf
./configure \
    --prefix=/mnt/tmpfs/builds/php/8.1.0-dev \
    --disable-all \
    --disable-cgi \
    --enable-debug \
    --enable-zts

compiledb make -j8
./sapi/cli/php -v

echo "compile_commands.json" >> .git/info/exclude
echo ".idea" >> .git/info/exclude
```
