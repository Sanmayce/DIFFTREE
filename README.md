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

Showcasing the first feature:
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

Enfun,
2023-Nov-14
Sanmayce
