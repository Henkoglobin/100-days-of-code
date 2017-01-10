# 100 Days Of Code - Log

### Day 1: January 10, 2017

**Today's Progress**: Implemented [Boyer-Moore string search](https://en.wikipedia.org/wiki/Boyer–Moore_string_search_algorithm) for [Kfr Reader](https://github.com/Henkoglobin/kfr-reader).

**Thoughts:**

I wanted to remove the need to hold each and every file in memory twice (as `byte[]` and as `string`),
since the `string` representation was only needed to search for keywords. Instead, I now search in
the `byte[]` representation using Boyer-Moore string search.

I had problems with the algorithm because I only implemented the bad-character jumps at first.
This works well in some cases, but apparently the algorithm can get stuck this way.

I will need to revisit this implementation and check if it's considerably slower than the old
approach.

**Link to work:** [Kfr Reader, commit fbe6c87](https://github.com/Henkoglobin/kfr-reader/commit/fbe6c87b25a3a4b6001697db472022e6c077c635)
