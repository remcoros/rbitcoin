Changed

- **`tx.head` insert runs on the confirm write thread.** The open tail is a private slot table, so confirm no longer keeps an `ibd-confirm-head` thread or overlaps that insert with Class C. Annotate still finishes first, and the insert stays outside the `--datadir-hdd` spindle hold.
