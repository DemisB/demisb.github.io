# Tips & tricks


- Create ssh key with 4096 something

`ssh-keygen -C "docker-build-read-only" -t rsa -b 4096`

- Repeating key MacOS (useful to know for IdeaVim)
https://stackoverflow.com/questions/39606031/intellij-key-repeating-idea-vim

- cmake
```bash
cmake -DBUILD_TESTS=ON -DBUILD_PYTHON_BINDINGS=OFF -DUSE_MULTITHREAD=OFF ..
cmake --build .
```

- linux package installed files
```bash
dpkg -L $package
```
cf https://serverfault.com/questions/96964/list-of-files-installed-from-apt-package

- find delete file with gith
```bash
git log --diff-filter=D --summary
```
cf. https://stackoverflow.com/questions/6017987/how-can-i-list-all-the-deleted-files-in-a-git-repository

- String manipulation in bash (parameter expansion, etc.)

```bash
> smth="/path/to/something"
> echo ${smth##*/}
something

> echo $smth | sed "s/^.*\///gi"
something

> echo $smth | grep -oE "[^/]*$"
something
```

cf. https://mywiki.wooledge.org/BashFAQ/100, https://stackoverflow.com/questions/22727107/how-to-find-the-last-field-using-cut

- Clipboard

cf. https://stackoverflow.com/questions/749544/pipe-to-from-the-clipboard-in-a-bash-script#comment54347773_749544

- Boto3 tip

https://stackoverflow.com/questions/33549254/how-to-generate-url-from-boto3-in-amazon-web-services
https://github.com/boto/boto3/issues/110