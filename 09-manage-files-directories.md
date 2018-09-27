# Manage Files and Directories

## How to Manage Files and Folders on Raspberry Pi 3 Model B+

#### Create Directory
---
```console
pi@raspberry:~ $ sudo mkdir NEW-DIRECTORY-NAME
```

---
#### Change Directory
---
```console
pi@raspberry:~ $ cd DIRECTORY-NAME
pi@raspberry:~ $ cd ..
pi@raspberry:~ $ cd ~/
```

---
#### Rename File or Directory
---
```console
pi@raspberry:~ $ sudo mv OLD-DIRECTORY-NAME NEW-DIRECTORY-NAME
```
```console
pi@raspberry:~ $ sudo mv OLD-FILE-NAME.EXT NEW-FILE-NAME.EXT
```

---
#### Copy/Rename File or Directory
---
```console
pi@raspberry:~ $ sudo cp OLD-DIRECTORY-NAME NEW-DIRECTORY-NAME
```
```console
pi@raspberry:~ $ sudo cp OLD-FILE-NAME.EXT NEW-FILE-NAME.EXT
```

---
#### Create File
---
```console
pi@raspberry:~ $ sudo touch FILE-NAME.EXT
```
```console
pi@raspberry:~ $ sudo nano FILE-NAME.EXT
```

---
#### Edit File
---
```console
pi@raspberry:~ $ sudo nano FILE-NAME.EXT
```

---
#### Find File
---
```console
pi@raspberry:~ $ sudo find / -name 'FILENAME.EXT'
```

---
#### Delete File or Directory
---
```console
pi@raspberry:~ $ sudo rm -rf DIRECTORY-NAME/
```
```console
pi@raspberry:~ $ sudo rm -rf FILE-NAME.EXT
```
