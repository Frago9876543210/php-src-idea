# php-src-idea

Based on [using CLion with php-src](https://dev.to/ramsey/using-clion-with-php-src-4me0)

```bash
# change it to "~/php-master" if you want
WORKING_DIR=/mnt/tmpfs

mkdir -p $WORKING_DIR
cd $WORKING_DIR
pip3 install compiledb

git clone --depth=1 https://github.com/Frago9876543210/php-src-idea.git

git clone --depth=1 https://github.com/php/php-src.git
cd php-src
./buildconf
./configure \
    --prefix=$WORKING_DIR/builds/php \
    --disable-all \
    --disable-cgi \
    --enable-debug \
    --enable-zts

compiledb make -j8
./sapi/cli/php -v

echo "compile_commands.json" >> .git/info/exclude
echo ".idea" >> .git/info/exclude

cp -r ../php-src-idea/.idea .
```
