# Linux / shell basic commands

## compiling using tar
tar -czvf archive.tar.gz directory => compile
tar -xzvf archive.tar.gz => extracts

## compile using zip
zip -9 -r archive.zip archive => compile
unzip archive.zip => extracts

## reseting permissions
sudo chown -R user:user <file_or_directory>
chmod -R u+rwx <file_or_directory>

## creating a file with some content on it
echo "some nice content" >> /path/to/archive/archive.txt

## setting wsl arch environment
[some powerfull link here](https://gist.github.com/ld100/3376435a4bb62ca0906b0cff9de4f94b#install-docker)
