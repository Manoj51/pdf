Complex fonts are generally embedded using an identity encoding which references characters by glyph index 
rather than character code. Because glyph indexes are specific to a particular font,
to extract text from the PDF you need a table mapping the glyph indexed to character codes.
This map is called the ToUnicode map.

Well behaved PDF producers will insert a ToUnicode map for all fonts that they embed. However some font producers 
may fail to do so. This means that copying or extracting text from such a PDF will result in gibberish.




Normal PDF documents containing Unicode text do not store the text as characters - but as references to the glyphs (letter shapes) in the fonts used. When embedding fonts in a PDF document Unicode fonts are also often converted by Acrobat to several smaller fonts - so, even if you use only one font, these references may be to glyphs in several smaller fonts not to the glyphs in the original font.

When cutting and pasting Unicode text from Acrobat to another application, Acrobat needs enough information to reconstruct the Unicode characters from the letter shapes. If the font used has glyphs named accoring to the Adobe Glyph Naming Convention then Acrobat can parse these names (which are also stored in the PDF document) and reconstruct the Unicode text. Unfortunatly, there are many Unicode fonts, including the standard Windows fonts, which do not follow this convention - so this may not be possible.

Tagged PDF files also ensure reliable translation of text into Unicode -so you should be able to cut and paste Unicode text from a Tagged PDF file.

So, if you want to prevent this problem in future, when crating a PDF from a document containing non-Latin Unicode text always generate the PDF file as a Tagged PDF and try to use only fonts which have been created with glyphs named accoring to the the Adobe Glyph Naming Convention. Doing this will ensure that your Unicode PDF documents are searchable and that texr can be reliably cut and paste text from them.

A Unicode is a standardized number describing the meaning of a character independant of its appearance, e.g. the characters a, a and a have the same Unicode but a different appearance. In a font, the description of the appearance of a character is called a glyph. In a Microsoft Word document the Unicodes are used to store the text. PDF, in contrast, selects the character of an embedded font by its glyph number. The glyph number is local to the font and only valid in conjunction with the particular font.



References:

* https://www.websupergoo.com/helppdfnet/source/6-abcpdf.objects/fontobject/1-methods/regeneratetounicode.htm

* http://superuser.com/questions/92615/cannot-copy-non-latin-characters-from-pdf-document 

* http://blog.pdf-tools.com/2014/01/why-is-extraction-of-text-from-pdf.html

* http://stackoverflow.com/questions/20355884/how-are-various-glyphs-encoded-inside-a-pdf-content-stream

* 
