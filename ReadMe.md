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

---
All files in this repository, except the 'License.txt' file and boot code (MBR/VBR/IPL) embedded in image files, are available under the "CC0 1.0 Universal" code. See the 'License.txt' file.
