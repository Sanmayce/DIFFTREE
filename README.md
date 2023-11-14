# DIFFTREE - In BASH, comparing two folders (or checking integrity of a folder), RECURSIVELY
Finally, thanks to Jean-Claude Jouffre and Sanmayce, here comes a simple script serving as a:
- Comparator of given two trees (given folders with their nested sub-folders) - useful to check decompression or backups;
- Integrity checker of a tree (a given folder with its nested sub-folders) - quite useful to monitor your SSDs' health.

Showcasing the first feature:
```
[sanmayce@djudjeto3 qb64]$ pwd
/home/sanmayce/qb64
[sanmayce@djudjeto3 qb64]$ DIFFTREE_BLAKE3.sh
Usage: DIFFTREE_BLAKE3.sh directory1 [directory2]
[sanmayce@djudjeto3 qb64]$ DIFFTREE_BLAKE3.sh ~/newstuff/ "/run/media/sanmayce/Samsung_512/Test folder"
Running DIFFTREE_BLAKE3.sh script revision 4++,
written originally by Jean-Claude Jouffre, modified by Kaze (suggestions for improvements on sanmayce@sanmayce.com).
Note1: The resultant table is dumped (also) in 'Snapshot_Tue Nov 14 11:24:07 PM EET 2023.txt' file.
Note2a: If both folders are the same then SHA1SUM column is added in order to have "integrity check" capability.
Note2b: If both folders are the same then 'REMOVE_DUPLETS.sh' script is created - it deletes DUPLETs on running.
Note2c: If both folders are the same then 'newstuff.sha1.txt' file is created - it contains the SHA1SUM snapshot of the tree.
Note2d: Once 'newstuff.sha1.txt' is created, it is compared against 'Snapshot_Tue Nov 14 11:24:07 PM EET 2023.txt', thus if identical then integrity is OK.
b3sum 1.5.0
Hasher in use: b3sum_linux_x64_bin
Comparing newstuff and Test folder folders RECURSIVELY...
Building lists of files...
Sorting...

MISSING IN /run/media/sanmayce/Samsung_512/Test folder :
Schizandra_r4.7z
Schizandra_r4_youtube.mkv

MISSING IN /home/sanmayce/newstuff :
misc/b3sum_linux_x64_bin
misc/b3sum_windows_x64_bin.exe
misc/Benchmark_Linus-Torvalds_SCALAR-VECTOR_2023-Nov-12.tar.bz2
misc/BLAKE3-1.5.0.tar.gz
misc/winlibs-x86_64-posix-seh-gcc-13.1.0-llvm-16.0.5-mingw-w64ucrt-11.0.0-r5.zip

+------------+---------+-------------------------------------+-------------------+----------
| Status     | Number  | Time of last data modification      | Filesize          | Filename 
+------------+---------+-------------------------------------+-------------------+----------
| OK         | 0000001 | 2021-09-14 22:16:45.000000000 +0300 | 0,000,000,007,322 | /home/sanmayce/newstuff/_MakeELF_Nakamichi_GCC.sh
| OK         | 0000002 | 2022-09-08 12:53:46.000000000 +0300 | 0,000,000,001,551 | /home/sanmayce/newstuff/_MakeEXE_Satanichi_CLANG.bat
| OK         | 0000003 | 2022-08-21 11:39:46.000000000 +0300 | 0,000,002,271,436 | /home/sanmayce/newstuff/Nakamichi_Ryuugan-ditto-1TB_btree.c
| OK         | 0000004 | 2023-10-26 02:41:15.540000000 +0300 | 0,000,000,000,112 | /home/sanmayce/newstuff/Satanichify.bat
| OK         | 0000005 | 2023-10-26 03:32:00.710000000 +0300 | 0,000,000,000,117 | /home/sanmayce/newstuff/Satanichify.sh
| OK         | 0000006 | 2023-04-02 12:03:54.000000000 +0300 | 0,000,016,414,175 | /home/sanmayce/newstuff/some audio/Blues & Rock Relax Ballads (2CD) (2023) - Joe Bonamassa - Prisoner.mp3
| OK         | 0000007 | 2023-10-19 20:55:55.740000000 +0300 | 0,000,022,493,632 | /home/sanmayce/newstuff/some audio/Sonya Belousova & Giona Ostinelli - The Witcher (2020) - Everytime You Leave.flac.wav
| OK         | 0000008 | 2023-10-16 20:42:49.640000000 +0300 | 0,000,021,205,676 | /home/sanmayce/newstuff/some audio/Sonya Belousova & Giona Ostinelli - The Witcher (2020) - Her Sweet Kiss.flac.wav
| OK         | 0000009 | 2023-10-19 20:58:56.680000000 +0300 | 0,000,033,537,372 | /home/sanmayce/newstuff/some audio/Sonya Belousova & Giona Ostinelli - The Witcher (2020) - Toss A Coin To Your Witcher.flac.wav
| OK         | 0000010 | 2023-08-20 20:55:45.820000000 +0300 | 0,000,421,437,484 | /home/sanmayce/newstuff/some audio/y2mate.com - The Psychology of The Fool_1080p.mp4.wav
| OK         | 0000011 | 2023-08-14 18:07:04.000000000 +0300 | 0,000,010,217,037 | /home/sanmayce/newstuff/some audio/y2mate.com - Милица Божинова и Илия Ангелов Скъпа моя скъпи мой 1987_480p.mp4
| OK         | 0000012 | 2023-10-26 03:25:44.190000000 +0300 | 0,000,461,977,600 | /home/sanmayce/newstuff/strstr_Berg_Blake_anonymous.tar
+------------+---------+-------------------------------------+-------------------+----------
Total number of files          : 12 (in 989563514 bytes)
Total number of different files: 0
[sanmayce@djudjeto3 qb64]$ 
```

Showcasing the second feature:
```
[sanmayce@djudjeto3 qb64]$ DIFFTREE_BLAKE3.sh ~/newstuff
Running DIFFTREE_BLAKE3.sh script revision 4++,
written originally by Jean-Claude Jouffre, modified by Kaze (suggestions for improvements on sanmayce@sanmayce.com).
Note1: The resultant table is dumped (also) in 'Snapshot_Tue Nov 14 11:24:36 PM EET 2023.txt' file.
Note2a: If both folders are the same then SHA1SUM column is added in order to have "integrity check" capability.
Note2b: If both folders are the same then 'REMOVE_DUPLETS.sh' script is created - it deletes DUPLETs on running.
Note2c: If both folders are the same then 'newstuff.sha1.txt' file is created - it contains the SHA1SUM snapshot of the tree.
Note2d: Once 'newstuff.sha1.txt' is created, it is compared against 'Snapshot_Tue Nov 14 11:24:36 PM EET 2023.txt', thus if identical then integrity is OK.
b3sum 1.5.0
Hasher in use: b3sum_linux_x64_bin
Adding SHA1SUM column...
Enforcing CHECK-INTEGRITY mode.
Building lists of files...
Sorting...

+------------+---------+-------------------------------------+-------------------+----------
| Status     | Number  | Time of last data modification      | Filesize          | Filename 
+------------+---------+-------------------------------------+-------------------+----------
| OK         | 0000001 | 2021-09-14 22:16:45.000000000 +0300 | 0,000,000,007,322 | /home/sanmayce/newstuff/_MakeELF_Nakamichi_GCC.sh
| OK         | 0000002 | 2022-09-08 12:53:46.000000000 +0300 | 0,000,000,001,551 | /home/sanmayce/newstuff/_MakeEXE_Satanichi_CLANG.bat
| OK         | 0000003 | 2022-08-21 11:39:46.000000000 +0300 | 0,000,002,271,436 | /home/sanmayce/newstuff/Nakamichi_Ryuugan-ditto-1TB_btree.c
| OK         | 0000004 | 2023-10-26 02:41:15.540000000 +0300 | 0,000,000,000,112 | /home/sanmayce/newstuff/Satanichify.bat
| OK         | 0000005 | 2023-10-26 03:32:00.710000000 +0300 | 0,000,000,000,117 | /home/sanmayce/newstuff/Satanichify.sh
| OK         | 0000006 | 2023-09-22 19:03:39.696850900 +0300 | 0,005,542,548,243 | /home/sanmayce/newstuff/Schizandra_r4.7z
| OK         | 0000007 | 2023-09-22 05:36:28.666484900 +0300 | 0,000,103,071,935 | /home/sanmayce/newstuff/Schizandra_r4_youtube.mkv
| OK         | 0000008 | 2023-04-02 12:03:54.000000000 +0300 | 0,000,016,414,175 | /home/sanmayce/newstuff/some audio/Blues & Rock Relax Ballads (2CD) (2023) - Joe Bonamassa - Prisoner.mp3
| OK         | 0000009 | 2023-10-19 20:55:55.740000000 +0300 | 0,000,022,493,632 | /home/sanmayce/newstuff/some audio/Sonya Belousova & Giona Ostinelli - The Witcher (2020) - Everytime You Leave.flac.wav
| OK         | 0000010 | 2023-10-16 20:42:49.640000000 +0300 | 0,000,021,205,676 | /home/sanmayce/newstuff/some audio/Sonya Belousova & Giona Ostinelli - The Witcher (2020) - Her Sweet Kiss.flac.wav
| OK         | 0000011 | 2023-10-19 20:58:56.680000000 +0300 | 0,000,033,537,372 | /home/sanmayce/newstuff/some audio/Sonya Belousova & Giona Ostinelli - The Witcher (2020) - Toss A Coin To Your Witcher.flac.wav
| OK         | 0000012 | 2023-08-20 20:55:45.820000000 +0300 | 0,000,421,437,484 | /home/sanmayce/newstuff/some audio/y2mate.com - The Psychology of The Fool_1080p.mp4.wav
| OK         | 0000013 | 2023-08-14 18:07:04.000000000 +0300 | 0,000,010,217,037 | /home/sanmayce/newstuff/some audio/y2mate.com - Милица Божинова и Илия Ангелов Скъпа моя скъпи мой 1987_480p.mp4
| OK         | 0000014 | 2023-10-26 03:25:44.190000000 +0300 | 0,000,461,977,600 | /home/sanmayce/newstuff/strstr_Berg_Blake_anonymous.tar
+------------+---------+-------------------------------------+-------------------+----------
Total number of files          : 14 (in 6635183692 bytes)
Total number of different files: 0
Total number of DUPLETs        : 0 (in 0 bytes)

File 'Snapshot_Tue Nov 14 11:24:36 PM EET 2023.txt' contains the DUPLETs (DUPLICATIVE files) in a roster.
Comparing 'newstuff.sha1.txt' with 'Snapshot_Tue Nov 14 11:24:36 PM EET 2023.txt' ...
diff: newstuff.sha1.txt: No such file or directory
The proper file 'newstuff.sha1.txt' exists not, run the script once more.
Updating 'newstuff.sha1.txt' with 'Snapshot_Tue Nov 14 11:24:36 PM EET 2023.txt' ...
Result: Problematic/Grmbl.
 __________                 ___.    .__                              __   .__               /\    ________                  ___.    .__    
 \______   \_______   ____  \_ |__  |  |    ____    _____  _____   _/  |_ |__|  ____       / /   /  _____/ _______   _____  \_ |__  |  |   
  |     ___/\_  __ \ /  _ \  | __ \ |  |  _/ __ \  /     \ \__  \  \   __\|  |_/ ___\     / /   /   \  ___ \_  __ \ /     \  | __ \ |  |   
  |    |     |  | \/(  <_> ) | \_\ \|  |__\  ___/ |  Y Y  \ / __ \_ |  |  |  |\  \___    / /    \    \_\  \ |  | \/|  Y Y  \ | \_\ \|  |__ 
  |____|     |__|    \____/  |___  /|____/ \___  >|__|_|  /(____  / |__|  |__| \___  >  / /      \______  / |__|   |__|_|  / |___  /|____/ 
                                 \/            \/       \/      \/                 \/   \/              \/               \/      \/        
[sanmayce@djudjeto3 qb64]$ DIFFTREE_BLAKE3.sh ~/newstuff
Running DIFFTREE_BLAKE3.sh script revision 4++,
written originally by Jean-Claude Jouffre, modified by Kaze (suggestions for improvements on sanmayce@sanmayce.com).
Note1: The resultant table is dumped (also) in 'Snapshot_Tue Nov 14 11:24:54 PM EET 2023.txt' file.
Note2a: If both folders are the same then SHA1SUM column is added in order to have "integrity check" capability.
Note2b: If both folders are the same then 'REMOVE_DUPLETS.sh' script is created - it deletes DUPLETs on running.
Note2c: If both folders are the same then 'newstuff.sha1.txt' file is created - it contains the SHA1SUM snapshot of the tree.
Note2d: Once 'newstuff.sha1.txt' is created, it is compared against 'Snapshot_Tue Nov 14 11:24:54 PM EET 2023.txt', thus if identical then integrity is OK.
b3sum 1.5.0
Hasher in use: b3sum_linux_x64_bin
Adding SHA1SUM column...
Enforcing CHECK-INTEGRITY mode.
Building lists of files...
Sorting...

+------------+---------+-------------------------------------+-------------------+----------
| Status     | Number  | Time of last data modification      | Filesize          | Filename 
+------------+---------+-------------------------------------+-------------------+----------
| OK         | 0000001 | 2021-09-14 22:16:45.000000000 +0300 | 0,000,000,007,322 | /home/sanmayce/newstuff/_MakeELF_Nakamichi_GCC.sh
| OK         | 0000002 | 2022-09-08 12:53:46.000000000 +0300 | 0,000,000,001,551 | /home/sanmayce/newstuff/_MakeEXE_Satanichi_CLANG.bat
| OK         | 0000003 | 2022-08-21 11:39:46.000000000 +0300 | 0,000,002,271,436 | /home/sanmayce/newstuff/Nakamichi_Ryuugan-ditto-1TB_btree.c
| OK         | 0000004 | 2023-10-26 02:41:15.540000000 +0300 | 0,000,000,000,112 | /home/sanmayce/newstuff/Satanichify.bat
| OK         | 0000005 | 2023-10-26 03:32:00.710000000 +0300 | 0,000,000,000,117 | /home/sanmayce/newstuff/Satanichify.sh
| OK         | 0000006 | 2023-09-22 19:03:39.696850900 +0300 | 0,005,542,548,243 | /home/sanmayce/newstuff/Schizandra_r4.7z
| OK         | 0000007 | 2023-09-22 05:36:28.666484900 +0300 | 0,000,103,071,935 | /home/sanmayce/newstuff/Schizandra_r4_youtube.mkv
| OK         | 0000008 | 2023-04-02 12:03:54.000000000 +0300 | 0,000,016,414,175 | /home/sanmayce/newstuff/some audio/Blues & Rock Relax Ballads (2CD) (2023) - Joe Bonamassa - Prisoner.mp3
| OK         | 0000009 | 2023-10-19 20:55:55.740000000 +0300 | 0,000,022,493,632 | /home/sanmayce/newstuff/some audio/Sonya Belousova & Giona Ostinelli - The Witcher (2020) - Everytime You Leave.flac.wav
| OK         | 0000010 | 2023-10-16 20:42:49.640000000 +0300 | 0,000,021,205,676 | /home/sanmayce/newstuff/some audio/Sonya Belousova & Giona Ostinelli - The Witcher (2020) - Her Sweet Kiss.flac.wav
| OK         | 0000011 | 2023-10-19 20:58:56.680000000 +0300 | 0,000,033,537,372 | /home/sanmayce/newstuff/some audio/Sonya Belousova & Giona Ostinelli - The Witcher (2020) - Toss A Coin To Your Witcher.flac.wav
| OK         | 0000012 | 2023-08-20 20:55:45.820000000 +0300 | 0,000,421,437,484 | /home/sanmayce/newstuff/some audio/y2mate.com - The Psychology of The Fool_1080p.mp4.wav
| OK         | 0000013 | 2023-08-14 18:07:04.000000000 +0300 | 0,000,010,217,037 | /home/sanmayce/newstuff/some audio/y2mate.com - Милица Божинова и Илия Ангелов Скъпа моя скъпи мой 1987_480p.mp4
| OK         | 0000014 | 2023-10-26 03:25:44.190000000 +0300 | 0,000,461,977,600 | /home/sanmayce/newstuff/strstr_Berg_Blake_anonymous.tar
+------------+---------+-------------------------------------+-------------------+----------
Total number of files          : 14 (in 6635183692 bytes)
Total number of different files: 0
Total number of DUPLETs        : 0 (in 0 bytes)

File 'Snapshot_Tue Nov 14 11:24:54 PM EET 2023.txt' contains the DUPLETs (DUPLICATIVE files) in a roster.
Comparing 'newstuff.sha1.txt' with 'Snapshot_Tue Nov 14 11:24:54 PM EET 2023.txt' ...
Result: Identical/OK.
  .___     .___                  __   .__                 .__         /\  ________    ____  __. 
  |   |  __| _/  ____    ____  _/  |_ |__|  ____  _____   |  |       / /  \_____  \  |    |/ _| 
  |   | / __ | _/ __ \  /    \ \   __\|  |_/ ___\ \__  \  |  |      / /    /   |   \ |      <   
  |   |/ /_/ | \  ___/ |   |  \ |  |  |  |\  \___  / __ \_|  |__   / /    /    |    \|    |  \  
  |___|\____ |  \___  >|___|  / |__|  |__| \___  >(____  /|____/  / /     \_______  /|____|__ \ 
            \/      \/      \/                 \/      \/         \/              \/         \/ 
[sanmayce@djudjeto3 qb64]$ 
```

Your snapshot/stamp is the name of the folder being checked, postfixed with ".sha1.txt", if BLAKE3 is missing then automatically sha1sum will be used:
```
[sanmayce@djudjeto3 qb64]$ cat newstuff.sha1.txt 
+--------+------------------------------------------------------------------+-------------------+----------
| Status | BLAKE3SUM                                                        | Filesize          | Filename 
+--------+------------------------------------------------------------------+-------------------+----------
|        | 147c3076bb988468388bbec923916c27247a670639bd46fb46a5166a2019c319 | 0,000,000,001,551 | /home/sanmayce/newstuff/_MakeEXE_Satanichi_CLANG.bat
|        | 2017993979e6e3613302c59d21d4976d415908e8d014f975dded67a0885ca110 | 0,000,021,205,676 | /home/sanmayce/newstuff/some audio/Sonya Belousova & Giona Ostinelli - The Witcher (2020) - Her Sweet Kiss.flac.wav
|        | 33cecbe0a05e7c7be657d7d8b99d99a0b86c1d0300af5aa430c3bef3971fe404 | 0,000,000,000,112 | /home/sanmayce/newstuff/Satanichify.bat
|        | 7dafc7f97b94dfa648bc91f2ab51084df47028aecf04dc9bbc7ea841a0e72afd | 0,000,022,493,632 | /home/sanmayce/newstuff/some audio/Sonya Belousova & Giona Ostinelli - The Witcher (2020) - Everytime You Leave.flac.wav
|        | 8116da282ca35b0aecb732008f12d4ec275450ac960b499e054dc39e24dd4879 | 0,000,000,000,117 | /home/sanmayce/newstuff/Satanichify.sh
|        | 8fedbb51eff7fb642358ae6e0cff0ea4ea7e4d1bba3ceaecffbe1c057c27ffee | 0,000,103,071,935 | /home/sanmayce/newstuff/Schizandra_r4_youtube.mkv
|        | 937ccf63328a20ac99696c08aca44dda7c76c6cafee3f1e8101991f2ddfc5c99 | 0,000,421,437,484 | /home/sanmayce/newstuff/some audio/y2mate.com - The Psychology of The Fool_1080p.mp4.wav
|        | afe3066a1d2660c7fdb223e0b8b11b5dc96a4be7b257daaea3a3518c70df0fee | 0,000,016,414,175 | /home/sanmayce/newstuff/some audio/Blues & Rock Relax Ballads (2CD) (2023) - Joe Bonamassa - Prisoner.mp3
|        | b923182384e4577a9c996803437aed72ddc4cf96eae70bd1d99599f99240b05f | 0,000,033,537,372 | /home/sanmayce/newstuff/some audio/Sonya Belousova & Giona Ostinelli - The Witcher (2020) - Toss A Coin To Your Witcher.flac.wav
|        | bd6c81f8c9621a0ee16bcb7da372eca6bb066521f8acc4368f74ba143dc2cc0c | 0,000,461,977,600 | /home/sanmayce/newstuff/strstr_Berg_Blake_anonymous.tar
|        | c6a164d6193376094794fccf61c5a89b319271db2666e585f27e46132fbd9b57 | 0,000,010,217,037 | /home/sanmayce/newstuff/some audio/y2mate.com - Милица Божинова и Илия Ангелов Скъпа моя скъпи мой 1987_480p.mp4
|        | e288a404baf4f2b200bce07e8b197d008582095d31ee9d6fbf10e9fb19d3e925 | 0,000,002,271,436 | /home/sanmayce/newstuff/Nakamichi_Ryuugan-ditto-1TB_btree.c
|        | f00b2180f5226dff805f8be0e6a9519eed063e05597333b860f69c0e5bf833c6 | 0,005,542,548,243 | /home/sanmayce/newstuff/Schizandra_r4.7z
|        | f6b4ccf6ecbd928c3840f4ac9718d18db190362a7740edbad7cfa6edb763faa4 | 0,000,000,007,322 | /home/sanmayce/newstuff/_MakeELF_Nakamichi_GCC.sh
+--------+------------------------------------------------------------------+-------------------+----------
[sanmayce@djudjeto3 qb64]$ 
```

Enfun,  
2023-Nov-14  
Sanmayce
