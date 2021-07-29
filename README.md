# Dev Tools

## How to build
```bash
echo "src-git devtools https://github.com/lazywalker/devtools-feeds" >> feeds.conf

./scripts/feeds update -a
./scripts/feeds install -p devtools
make menuconfig

#Select packages from Dev Tools catagory, then
make package/oled-tool/compile V=sc

# if you want libaruipioled
make package/libaruipioled/compile V=sc

```
