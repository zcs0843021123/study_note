# 修复 Mac 电脑不识别 U 盘剩余空间的问题
> 当 U 盘做启动盘后，再次插入 Mac 电脑后，原本磁盘空间很大的 U 盘，只剩下几百兆了，这时候需要重新格式化修复 U 盘

## 列出所有的磁盘信息

`diskutil list`

输出

```
/dev/disk0 (internal, physical):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *500.3 GB   disk0
   1:                        EFI ⁨EFI⁩                     314.6 MB   disk0s1
   2:                 Apple_APFS ⁨Container disk1⁩         500.0 GB   disk0s2

/dev/disk1 (synthesized):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      APFS Container Scheme -                      +500.0 GB   disk1
                                 Physical Store disk0s2
   1:                APFS Volume ⁨Macintosh HD - 数据⁩     214.5 GB   disk1s1
   2:                APFS Volume ⁨Preboot⁩                 292.8 MB   disk1s2
   3:                APFS Volume ⁨Recovery⁩                610.7 MB   disk1s3
   4:                APFS Volume ⁨VM⁩                      20.5 KB    disk1s4
   5:                APFS Volume ⁨Macintosh HD⁩            15.0 GB    disk1s5
   6:              APFS Snapshot ⁨com.apple.os.update-...⁩ 15.0 GB    disk1s5s1

/dev/disk2 (external, physical):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *31.9 GB    disk2
   1:                        EFI ⁨EFI⁩                     209.7 MB   disk2s1
   2:       Microsoft Basic Data ⁨USB64⁩                   31.7 GB    disk2s2
```

## 列出支持的文件系统

`diskutil listFilesystems`

输出

```
Formattable file systems

These file system personalities can be used for erasing and partitioning.
When specifying a personality as a parameter to a verb, case is not considered.
Certain common aliases (also case-insensitive) are listed below as well.

-------------------------------------------------------------------------------
PERSONALITY                     USER VISIBLE NAME
-------------------------------------------------------------------------------
Case-sensitive APFS             APFS (Case-sensitive)
  (or) APFSX
APFS                            APFS
  (or) APFSI
ExFAT                           ExFAT
MS-DOS                          MS-DOS (FAT)
MS-DOS FAT12                    MS-DOS (FAT12)
MS-DOS FAT16                    MS-DOS (FAT16)
MS-DOS FAT32                    MS-DOS (FAT32)
  (or) FAT32
HFS+                            Mac OS Extended
Case-sensitive HFS+             Mac OS Extended (Case-sensitive)
  (or) HFSX
Case-sensitive Journaled HFS+   Mac OS Extended (Case-sensitive, Journaled)
  (or) JHFSX
Journaled HFS+                  Mac OS Extended (Journaled)
  (or) JHFS+
Free Space                      可用空间
  (or) FREE
```

## 完全格式化磁盘

* 先格式化成 empty 这个时候格式化后不会显示盘符 `diskutil eraseDisk free EMPTY /dev/disk2`

* 再格式化成 FAT32 格式，并将 U 盘命名为 BERRY `diskutil eraseDisk FAT32 BERRY /dev/disk2`



