_Introduction_

This project implements a simple templating system in C# using the Django style {{ varName }}, double curly notation. The class was implemented specifically for templatizing html/javascript but can be used with any file type.

The templates only do replacements. Unlike Django, there are no conditional statements, for loops etc.. This can all be accomplished within C# itself and keeps layout nicely separated from logic.

_Points of Interest_

Unlike StringTemplate from www.stringtemplate.org (which seems to be the best open source template engine written in c#) this template engine indexes the variable locations within the template instead of breaking the template into multiple chunks and putting them back together for output. The indexing occurs only once when the template is first used. It's then stored in a global dictionary with the filename as its key. The reason for indexing is the same reason you would use a StringBuilder rather than concatenation operators i.e. ("asdf" + "ghjk") to build strings. It keeps everything in one string, lowering the copy time and memory use associated with separating the template into many different strings and putting it back together for output. The only trade-off here is that you have to recalculate the indicies above an inserted variable by adding the length of the value inserted. I assumed this trade-off would be well worth it.

These templates are currently in use on SpyFu.com.

_Background_

The real driver for me to create this was the frustration that came from trying to replicate the same ASP.NET user control several times on a page. While this can be done, I've only got it to work by putting all the code in markup and pasting the same markup (user control) over and over, or by putting all the code in code-behind files and creating all the HTML elements in C#...uck. While the first option is probably the best since the HTML is actually editable in its native format and the need for pagination usually means a limited number of controls, I knew that templates, after using Google App Engine and Django, would offer a more elegant solution.

_Note_

The tests included run within Visual Studio itself and to my knowledge are a new feature in Visual Studio 2008.

**Please download the source using the link on the right. There are tests as well as an example website to show you how to use templates.**