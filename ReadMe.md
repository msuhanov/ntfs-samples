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

---
All files in this repository, except the 'License.txt' file and boot code (MBR/VBR/IPL) embedded in image files, are available under the "CC0 1.0 Universal" code. See the 'License.txt' file.
