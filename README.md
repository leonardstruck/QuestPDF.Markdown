# QuestPDF.Markdown
QuestPDF.Markdown allows rendering markdown into a [QuestPDF](https://www.questpdf.com/) document using the [markdig](https://github.com/xoofx/markdig) parser.

[![Nuget](https://img.shields.io/nuget/v/QuestPDF.Markdown)](https://www.nuget.org/packages/QuestPDF.Markdown)

## Usage
```csharp
var text = 
@"# Hello, world!
*Greetings* from **markdown**!
> Hello, back!";

var document = Document.Create(container =>
{
    container.Page(page =>
    {
        page.Margin(20);
        page.Content().Markdown(text);
    });
});
```

![Usage](https://github.com/christiaanderidder/QuestPDF.Markdown/blob/main/img/usage.png?raw=true)

## What's supported?
The aim of this library is to support all basic markdown functionality and some of the extensions supported by markdig.

Currently the following features are supported:
- Headings
- Block quotes
- Code blocks
- Lists (ordered and unordered)
- Emphasis (bold, italic)
- Task lists
- Extra emphasis (subscript, superscript, strikethrough, marked, inserted)
- Tables

Support for the following features will be added in the future:
- Images
- Footnotes
- A way to configure the styling of rendered components

Support for the following features is not planned:
- Raw HTML
- Math blocks
- Diagrams

## Contributing
To quickly test changes made in the library, you can make use of the excellent QuestPDF previewer in combination with the QuestPDF.Markdown.Tests project and `dotnet watch`

To render the test markdown file in the previewer, run the following command in the root directory of the repository:
```zsh
dotnet watch test --project ./tests/QuestPDF.Markdown.Tests -- --filter Name=Render
```

To render the test markdown file in the previewer with additional background colors and margins, run the following command in the root directory of the repository:
```zsh
dotnet watch test --project ./tests/QuestPDF.Markdown.Tests -- --filter Name=RenderDebug
```

Any changes made to the MarkdownRenderer class will be automatically reflected in the previewer.
