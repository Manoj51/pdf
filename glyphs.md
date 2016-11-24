Complex fonts are generally embedded using an identity encoding which references characters by glyph index 
rather than character code. Because glyph indexes are specific to a particular font,
to extract text from the PDF you need a table mapping the glyph indexed to character codes.
This map is called the ToUnicode map.

Well behaved PDF producers will insert a ToUnicode map for all fonts that they embed. However some font producers 
may fail to do so. This means that copying or extracting text from such a PDF will result in gibberish.
