generate package list if needed: dpkg-query -f '${binary:Package}\n' -W > pkglist.txt
install from pkglist.txt: sudo apt-get install $(cat pkglist.txt | awk '{print $1}') && sudo apt-get update && sudo apt-get upgrade

for i in $(cat pkglist.txt | awk ‘{print $1}’); do sudo apt-get install -y $i && sudo apt-get update && sudo apt-get upgrade; done

But first, set the rasp pi screen to stay on when plugged in
Or, don’t check for updates:
for i in $(cat pkglist.txt | awk '{print $1}'); do sudo apt-get install -y $i; done