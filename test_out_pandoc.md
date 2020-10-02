# Working

## Redmine internal link syntax is preserved

This is a \[\[wiki link\]\].

## Code highlighting is preserved

    <code class="sql">
    SELECT * FROM table;
    </code>

## Inline code can contains @

Repository is `git`github.com/user/repo@.

## Block code use backtick, not indent, if they are not preceded by a blank line

Try this:

    echo "OK"

## Quotations are preserved

&gt; I'll be back! Ha! You didn't know I was gonna say that, did you?

## XML tags are preserved

    <code>
    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
    <plist version="1.0">
        <array>
            <dict>
                <key>foo</key>
                <string>bar</string>
            </dict>
        </array>
    </plist>
    </code>

## Plain URL should not get broken by escaped characters

http://example.com/example\_site/\#test

# Known limitations

## Unsupported cell formatting is dropped silently

<table>
<tbody>
<tr class="odd">
<td style="text-align: right;">one</td>
<td style="text-align: left;">two</td>
</tr>
<tr class="even">
<td style="text-align: right;">Cell spanning 2 columns</td>
<td style="text-align: left;"></td>
</tr>
<tr class="odd">
<td style="text-align: right;">Cell spanning 2 rows</td>
<td style="text-align: left;">one</td>
</tr>
<tr class="even">
<td style="text-align: right;">two</td>
<td style="text-align: left;"></td>
</tr>
<tr class="odd">
<td style="text-align: right;">Right-aligned cell</td>
<td style="text-align: left;">Left-aligned cell</td>
</tr>
</tbody>
</table>

## Unsupported multiline tables

<table>
<thead>
<tr class="header">
<th>one</th>
<th>two</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Cell spanning 2 columns<br />
asd</td>
<td></td>
</tr>
<tr class="even">
<td>Cell spanning 2 rows</td>
<td>one</td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr class="header">
<th>one</th>
<th>two</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>multilinecell<br />
- List 1<br />
- List 2<br />
- List 3</td>
<td>multilinecell<br />
- List 1<br />
- List 2<br />
- List 3</td>
</tr>
<tr class="even">
<td>Right-aligned cell</td>
<td>Left-aligned cell</td>
</tr>
</tbody>
</table>

Other Table

<table>
<tbody>
<tr class="odd">
<td>A:</td>
<td>B</td>
</tr>
<tr class="even">
<td>D:</td>
<td>Dunkelgrün</td>
</tr>
<tr class="odd">
<td>C:</td>
<td>Grün</td>
</tr>
</tbody>
</table>

## List with code block is partially supported

The numbering will be reset after each code block, but layout is preserved:

\# first item:

    <code class="sql">
    SELECT * FROM table;
    </code>

\# second item:

    rm -rf /tmp/*

1.  final item

But some more complex case might result in broken list layout.

## Wrongly formatted lists (wrong textile, but works in redmine)

Correct List

1.  A
    -   A
        -   B
            -   C
    -   A
        -   R
2.  A
    -   G
        -   G
            -   G
                -   G
                -   G
            -   G

First wrong List

1.  A  
    \#\* A  
    \# B  
    \#\* C  
    \#\* A  
    \# R
2.  A  
    \#\* G  
    \# G  
    \#\* G  
    \# G  
    \# G  
    \#\* G

Second wrong list

-   A  
    \*\# A  
    \*\#\# B  
    \*\#\#\# C  
    \*\# A  
    \*\#\# R
-   A  
    \*\# G  
    \*\#\# G  
    \*\#\#\# G  
    \*\#\#\#\# G  
    \*\#\#\#\# G  
    \*\#\#\# G
