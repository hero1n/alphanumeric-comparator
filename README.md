# Alphanumeric Comparator 
An implementation of a comparator that sort strings in an order that makes sense for a human. I.e. it performs an "alphabetical"/"alphanumeric" comparison instead of a lexicographical comparison.  
It is mainly intended to be used to sort information that are to be read by humans (in UI's etc). So keep in mind that what the "correct" ordering should be is entirely subjective and application specific. 
It should however be straightforward to modify the comparator to suit any specific needs.


##Examples

Given file names:

    image-1.jpg
    image-4.jpg
    image-10.jpg
    image-02.jpg
    image-22.jpg
    image-9.jpg
    image-11.jpg
    
A standard lexicographical sort would produce the following:

    image-02.jpg
    image-1.jpg
    image-10.jpg
    image-11.jpg
    image-22.jpg
    image-4.jpg
    image-9.jpg
  
But as a human, the numbers in the file name has a meaning an the file "9" should come before the file "10", and "02" should not come before "1".
Using the `AlphanumericComparator` would produce the following result instead:

    image-1.jpg
    image-02.jpg
    image-4.jpg
    image-9.jpg
    image-10.jpg
    image-11.jpg
    image-22.jpg

This comparator also supports the use of a locale-sensitive `Collator` for string comparison.

```java
    @Test
    public void example() {
        final List<String> stringsToSort = asList("HD 20GB", "HD 2GB");

        stringsToSort.sort(new AlphanumericComparator(Locale.ENGLISH));
        
        assertEquals(asList("HD 2GB", "HD 20GB"), stringsToSort);
    }
```

##License
This code is available under GNU LGPL. (See source for details)

The original Alphanum Algorithm can be found at http://www.DaveKoelle.com

##Download

Releases are available at the Maven central repository. Or you can just use the source code directly if you prefer that.

```xml
<dependency>
    <groupId>se.sawano.java</groupId>
    <artifactId>alphanumeric-comparator</artifactId>
    <version>1.2</version>
</dependency>
```
