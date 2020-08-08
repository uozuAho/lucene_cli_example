# Lucene text file search example

A console app that indexes text files in a directory tree, allowing full text
and tag based search. Uses Lucene.


## Development

Run all tests

> ./gradlew test

To build the distributable jar plus runner script

> ./build.dist.sh  # output sent to dist/


## Indexing and searching

The following scripts build the distributable jar before using it, so won't be
as fast as just running the jar.

Before running any searches, you need to rebuild the search index. To do so:

> ./note_searcher.sh index /path/to/index

This builds the index next to the distributable jar.

To run a search:

> ./note_searcher.sh search 'your search query'  # quotes are required for multiple words

Search queries are expected to be in lucene classic parser syntax, see:
https://lucene.apache.org/core/8_0_0/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#package.description

Some examples:

`apple banana +carrot`  # file contains the word carrot, and possibly apple or banana
`apple banana -carrot`  # file does not contain carrot, but either apple and/or banana
`apple banana #food`    # file contains apple, banana, and/or the tag #food


## References

- http://shaierera.blogspot.com/2016/01/indexing-tagged-data-with-lucene.html
- https://lucene.apache.org/core/8_4_1/core/index.html has some demos
- http://intelligiblebabble.com/custom-lucene-tokenizer-for-tech-keywords/
- https://www.toptal.com/database/full-text-search-of-dialogues-with-apache-lucene
