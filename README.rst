bloom-filter
============

A pure python bloom filter (low storage requirement, probabilistic
set datastructure) is provided.  It is known to work on CPython 3.x, Pypy,
and Jython.

Includes mmap, in-memory and disk-seek backends.

This project builds on `drs-bloom-filter` and `bloom_filter_mod`.
Credits and links can be found in AUTHORS.md.

Usage
-----

The user specifies the desired maximum number of elements and the
desired maximum false positive probability, and the module
calculates the rest.

::

    from bloom_filter2 import BloomFilter

    # instantiate BloomFilter with custom settings,
    # max_elements is how many elements you expect the filter to hold.
    # error_rate defines accuracy; You can use defaults with
    # `BloomFilter()` without any arguments. Following example
    # is same as defaults:
    bloom = BloomFilter(max_elements=10000, error_rate=0.1)

    # Test whether the bloom-filter has seen a key:
    assert "test-key" not in bloom

    # Mark the key as seen
    bloom.add("test-key")

    # Now check again
    assert "test-key" in bloom
