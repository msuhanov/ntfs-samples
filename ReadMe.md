This repository contains various NTFS file system images for testing.

# ntfs-ptrn.raw

* This image was filled with the "PTRN" byte pattern prior to the formatting.
* The Windows 10 (18348) installation was used to format the image.
* Some files were created in the volume.

## Artifacts
* Cluster slack (file path: "/2.txt").
* Unallocated data marked as allocated (file path: "/$Extend/$RmMetadata/$Repair", streams: "$Corrupt" and "$Verify", search for the "PTRN" byte pattern there).

# ntfs-ramslack.raw

* This image was filled with the "PTRN" byte pattern prior to the formatting.
* The Windows 10 (14393) installation was used to format the image (with the compression feature enabled for the new volume).
* Some files were created in the volume.

## Artifacts
* RAM slack (file path: "/1.txt", image offset: 213303).
* Cluster slack (file path: "/1.txt", image offset: 213504).
* Unallocated data marked as allocated (file path: "/$Extend/$RmMetadata/$Repair", streams: "$Corrupt" and "$Verify", search for the "PTRN" byte pattern there).

# ntfs-lastaccess.raw

* This image was filled with the "PTRN" byte pattern prior to the formatting.
* The Windows 10 (18348) installation was used to format the image.
* A single directory and a single file in this directory were created in the volume.
* This file was opened several times.

## Artifacts
* Two different last access timestamps (in the $STANDARD_INFORMATION and $I30->$FILE_NAME attributes) for a single file (file path: "/test/1.txt"): 2019-03-03 12:37:55 and 2019-03-03 12:35:17.
* Unallocated data marked as allocated (file path: "/$Extend/$RmMetadata/$Repair", streams: "$Corrupt" and "$Verify", search for the "PTRN" byte pattern there).

# ntfs-2m.raw

* This image contains a file system with large clusters (2 097 152 bytes per cluster).
* The Windows 10 (18362) installation was used to format the image.

# ntfs_extremely_fragmented_mft.raw

The image (894 MiB in the RAR-compressed form) is hosted on another site:
* https://mega.nz/#!uVdHmAKD!8piInddWWdV0qsMuy9j6KYlGrxGY7IZmGs1Xz1IpzXI
* MD5(ntfs_extremely_fragmented_mft.rar) = b45bdd5f1acaccbd0300db0b16ba74d1

## Details
* This image contains a file system with an extremely fragmented $MFT file. Its size is 52166656000 bytes, it has the following MD5: ed9c202405fd9a28b7e0ee96e3f07b33.
* The following file record numbers are used by attributes of this file: 0, 15, 16, 17, 18, 19, 20, 21, 22, 34799617, 34799618, and 34799619.

# ntfs-si-vs-fn.raw

* This image contains a simulated (modified using a HEX editor) file system with three different sets of timestamps (in the $STANDARD_INFORMATION, $FILE_NAME, and $I30->$FILE_NAME attributes) for a single file (file path: "/test/test.txt").
* The $FILE_NAME attribute in the file record contains the following timestamps: 2014-12-12.
* The $STANDARD_INFORMATION attribute in the file record contains the following timestamps: 2015-11-03.
* The $I30->$FILE_NAME attribute in the parent file record (file path: "/test/") contains the following timestamps: 2016-09-24.

# ntfs.raw

This image contains several artifacts that are ignored by multiple DFIR tools. The image was created using a Windows "20H1" installation (no modifications were made in a HEX editor).
* MD5(ntfs.raw) = 8db1a094a129a8ebe9500841006aede5

## Artifacts
* There are two shadow copies of the NTFS volume, one of them is marked as offline (thus, not shown in the "vssadmin list shadows" output). Some tools that rely on Windows to work with shadow copies see only one shadow copy. Do you see two shadow copies? Do you see a file named "shadow_2" in the root directory of the latest shadow copy?
* There is a file name entry ($I30) existing in the $MFT slack space (within the main volume, not within two shadow copies). Do you see it? Do you see an entry named "file_hidden.txt" in the "test_dir" directory?
* There are two files with different last access timestamps recorded (within the main volume, not within two shadow copies) in file system metadata (excluding the $FILE_NAME attribute in a file record). Do you see the following last access timestamps for the "/test_dir_2/file_2_1.txt" file: 2020-07-25 12:49:21 and 2020-07-25 12:35:48? Also, do you see the following last access timestamps for the "/test_dir/file_1.txt" file: 2020-07-25 12:33:24 and 2020-07-25 12:35:24?

---
All files in this repository, except the 'License.txt' file and boot code (MBR/VBR/IPL) embedded in image files, are available under the "CC0 1.0 Universal" code. See the 'License.txt' file.
