# Markdown File Review
- - -
> Overview: Two Markdown files were under review. 3 implementations were made to each file to discover issues.

Repo links to the Markdownfiles:

[Markdown File 1](https://github.com/ezhou413/markdown-parse)

[Markdown File 2](https://github.com/sm52/markdown-parse)

- - - 
### Snippet 1
This implementaion should produce the following result
![s1](s1.png)

the test was written in the MarkdownTest file
```
 @Test
    public void testsnippet1() throws IOException {
        String contents = Files.readString(Path.of("snippet1.md"));
        List<String> expect = List.of("url.com","`google.com","google.com","ucsd.edu");
        assertEquals(MarkdownParse.getLinks(contents), expect);
    }

```
output after running the test
#### Markdown File 1
![o1](o1.png)

I have nerver consider the senerio where brackets could be inside of name of the link. To fix this issue bigger change of code is needed. A loop is needed to search for the last close bracket. After the index of the last close bracket is located, the program can verify if open parenthesis is on the next index.

- - -
### Snippet 2
This implementaion should produce the following result
![s2](s2.png)

the test was written in the MarkdownTest file
```
@Test
    public void testsnippet2() throws IOException {
        String contents = Files.readString(Path.of("snippet2.md"));
        List<String> expect = List.of("a.com","b.com","a.com(())","example.com");
        assertEquals(MarkdownParse.getLinks(contents), expect);
    }

```
output after running the test
#### Markdown File 1
![o2](o2.png)

To fix this bug, a small change of code is needed. I have never consider parenthesis can be inside the link. After the open parenthesis is loacted, the propgram should search for the las parenthesis and return the text inbewteen them.
- - - 
### Snippet 3
This implementaion should produce the following result
![s3](s3.png)

the test was written in the MarkdownTest file
```
 @Test
    public void testsnippet3() throws IOException {
        String contents = Files.readString(Path.of("snippet3.md"));
        List<String> expect = List.of(" https://www.twitter.com","https://ucsd-cse15l-w22.github.io","github.com","https://cse.ucsd.edu/");
        assertEquals(MarkdownParse.getLinks(contents), expect);
    }

```
output after running the test
#### Markdown File 1
![o3](o3.png)

To fix this bug, a big change of code is required. Beacuse there is a link inside another link, which is a scenrio that was never considered before.
