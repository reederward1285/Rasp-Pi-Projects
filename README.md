# Package install scripts for Raspbian and Ubuntu OS
If you want to automate the installation of packages, write a bash script. :)
Simply make a file on terminal
```nano name_of_file```
Then, write the packages to install in the file. For example:
```sudo apt-get -y install bison flex git```
Make the bash script an executable file:
```sudo chmod +x name_of_file```
and run the file!
```./name_of_file```

# Generate package list if needed:
```dpkg-query -f '${binary:Package}\n' -W > pkglist.txt```
install from pkglist.txt:
```sudo apt-get install $(cat pkglist.txt | awk '{print $1}') && sudo apt-get update && sudo apt-get upgrade```

```for i in $(cat pkglist.txt | awk ‘{print $1}’); do sudo apt-get install -y $i && sudo apt-get update && sudo apt-get upgrade; done```

# But first, set the rasp pi screen to stay on when plugged in, or, don’t check for updates:
```for i in $(cat pkglist.txt | awk '{print $1}'); do sudo apt-get install -y $i; done```
