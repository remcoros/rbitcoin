Fixed

- **The Class A tear-guard copy no longer locks the append.** One thread appends each stem and publishes that length after the pwrite. The tip flush reads only up to the length it loaded, writes the inactive tail slot, and fsyncs that slot in the same sync as the stems. The next body write no longer waits out that copy, so the confirm write queue is not stuck behind it. A page-0 image stores that loaded length before its checksum. Open writes the tail slot's length into the header, so a length torn in during the copy does not hide a zeroed tail.
