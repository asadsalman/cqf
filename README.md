# cqf
A General-Purpose Counting Filter: Counting Quotient Filter (CQF)

Overview
--------
 The CQF supports approximate membership testing and counting the occurrences of
 items in a data set. This general-purpose AMQ is small and fast, has good
 locality of reference, scales out of RAM to SSD, and supports deletions,
 counting (even on skewed data sets), resizing, merging, and highly concurrent
 access.

API
--------
* 'qf_insert(item, count)': insert an item to the filter
* 'qf_count_key_value(item)': return the count of the item. Note that this
  method may return false positive results like Bloom filters or an over count.
* 'qf_remove(item, count)': decrement the count of the item by count. If count
  is 0 then completely remove the item.

Build
-------
This library depends on libssl.

 $ make
 $ ./main 24

 The argument to main is the log of the number of slots in the CQF. For example,
 to create a CQF of 2^30 slots, the argument will be 30.

Contributing
------------
Contributions via GitHub pull requests are welcome.


Authors
-------
- Prashant Pandey <ppandey@cs.stonybrook.edu>
- Rob Johnson <rob@cs.stonybrook.edu>
