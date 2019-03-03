This repository contains various NTFS file system images for testing.

# ntfs-ptrn.raw

* This image was filled with the "PTRN" byte pattern prior to the formatting.
* The Windows 10 (18348) installation was used to format the image.
* Some files were created in the volume.

Artifacts:
* Cluster slack (file path: "/2.txt").
* Unallocated data marked as allocated (file path: "/$Extend/$RmMetadata/$Repair", streams: "$Corrupt" and "$Verify", search for the "PTRN" byte pattern there).

# ntfs-ramslack.raw

* This image was filled with the "PTRN" byte pattern prior to the formatting.
* The Windows 10 (14393) installation was used to format the image (with the compression feature enabled for the new volume).
* Some files were created in the volume.

Artifacts:
* RAM slack (file path: "/1.txt", image offset: 213303).
* Cluster slack (file path: "/1.txt", image offset: 213504).
* Unallocated data marked as allocated (file path: "/$Extend/$RmMetadata/$Repair", streams: "$Corrupt" and "$Verify", search for the "PTRN" byte pattern there).
