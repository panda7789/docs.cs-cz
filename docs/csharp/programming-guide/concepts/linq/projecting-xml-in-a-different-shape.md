---
title: Projektování XML v jiném obrazci (C#)
ms.date: 07/20/2015
ms.assetid: 4cb6b14a-32dc-4a2a-813e-bf9368fa8d86
ms.openlocfilehash: 1377df1ce7f54bc9a0f58836d7df5e5b7b54a69a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591533"
---
# <a name="projecting-xml-in-a-different-shape-c"></a><span data-ttu-id="7d70e-102">Projektování XML v jiném obrazci (C#)</span><span class="sxs-lookup"><span data-stu-id="7d70e-102">Projecting XML in a Different Shape (C#)</span></span>
<span data-ttu-id="7d70e-103">Toto téma ukazuje příklad projektu XML, který je v jiném tvaru než zdrojový kód XML.</span><span class="sxs-lookup"><span data-stu-id="7d70e-103">This topic shows an example of projecting XML that is in a different shape than the source XML.</span></span>  
  
 <span data-ttu-id="7d70e-104">Mnoho typických transformací XML sestává z zřetězených dotazů, jako v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="7d70e-104">Many typical XML transformations consist of chained queries, as in this example.</span></span> <span data-ttu-id="7d70e-105">Je běžné začít s určitou formou jazyka XML, mezilehlé výsledky projektu jako kolekce anonymních typů nebo pojmenovaných typů a pak nakonec k prohlédnutí výsledků zpět do XML, které jsou v zcela jiném tvaru než zdrojový kód XML.</span><span class="sxs-lookup"><span data-stu-id="7d70e-105">It is common to start with some form of XML, project intermediate results as collections of anonymous types or named types, and then finally to project the results back into XML that is in an entirely different shape than the source XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d70e-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="7d70e-106">Example</span></span>  
 <span data-ttu-id="7d70e-107">Tento příklad zpracovává dokument WordprocessingML a načítá uzly odstavců z dokumentu WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="7d70e-107">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="7d70e-108">Také identifikuje styl a text každého odstavce.</span><span class="sxs-lookup"><span data-stu-id="7d70e-108">It also identifies the style and text of each paragraph.</span></span> <span data-ttu-id="7d70e-109">Nakonec ukázkový projekt XML s jiným tvarem.</span><span class="sxs-lookup"><span data-stu-id="7d70e-109">Finally, the example projects XML with a different shape.</span></span> <span data-ttu-id="7d70e-110">Tento příklad sestaví na předchozích příkladech v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="7d70e-110">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="7d70e-111">Nový příkaz, který je projekcí vyvolán v komentářích v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="7d70e-111">The new statement that does the projection is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="7d70e-112">Pokyny k vytvoření zdrojového dokumentu pro tento příklad najdete v tématu [vytvoření zdrojového dokumentu XML (C#) pro zdrojový Office](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="7d70e-112">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="7d70e-113">Tento příklad používá třídy ze sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="7d70e-113">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="7d70e-114">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7d70e-114">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
public static class LocalExtensions  
{  
    public static string StringConcatenate(this IEnumerable<string> source)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item));  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate(this IEnumerable<string> source, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s).Append(separator);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item)).Append(separator);  
        return sb.ToString();  
    }  
}  
  
class Program  
{  
    public static string ParagraphText(XElement e)  
    {  
        XNamespace w = e.Name.Namespace;  
        return e  
               .Elements(w + "r")  
               .Elements(w + "t")  
               .StringConcatenate(element => (string)element);  
    }  
  
    static void Main(string[] args)  
    {  
        const string fileName = "SampleDoc.docx";  
  
        const string documentRelationshipType =  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
        const string stylesRelationshipType =  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";  
        const string wordmlNamespace =  
          "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
        XNamespace w = wordmlNamespace;  
  
        XDocument xDoc = null;  
        XDocument styleDoc = null;  
  
        using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))  
        {  
            PackageRelationship docPackageRelationship =  
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();  
            if (docPackageRelationship != null)  
            {  
                Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative),  
                  docPackageRelationship.TargetUri);  
                PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
                //  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
                //  Find the styles part. There will only be one.  
                PackageRelationship styleRelation =  
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
                if (styleRelation != null)  
                {  
                    Uri styleUri =  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
                    PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
                    //  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
                }  
            }  
        }  
  
        string defaultStyle =  
            (string)(  
                from style in styleDoc.Root.Elements(w + "style")  
                where (string)style.Attribute(w + "type") == "paragraph" &&  
                      (string)style.Attribute(w + "default") == "1"  
                select style  
            ).First().Attribute(w + "styleId");  
  
        // Find all paragraphs in the document.  
        var paragraphs =  
            from para in xDoc  
                         .Root  
                         .Element(w + "body")  
                         .Descendants(w + "p")  
            let styleNode = para  
                            .Elements(w + "pPr")  
                            .Elements(w + "pStyle")  
                            .FirstOrDefault()  
            select new  
            {  
                ParagraphNode = para,  
                StyleName = styleNode != null ?  
                    (string)styleNode.Attribute(w + "val") :  
                    defaultStyle  
            };  
  
        // Retrieve the text of each paragraph.  
        var paraWithText =  
            from para in paragraphs  
            select new  
            {  
                ParagraphNode = para.ParagraphNode,  
                StyleName = para.StyleName,  
                Text = ParagraphText(para.ParagraphNode)  
            };  
  
        // The following is the new code that projects XML in a new shape.  
        XElement root = new XElement("Root",  
            from p in paraWithText  
            select new XElement("Paragraph",  
                new XElement("StyleName", p.StyleName),  
                new XElement("Text", p.Text)  
            )  
        );  
  
        Console.WriteLine(root);  
    }  
}  
```  
  
 <span data-ttu-id="7d70e-115">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="7d70e-115">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Paragraph>  
    <StyleName>Heading1</StyleName>  
    <Text>Parsing WordprocessingML with LINQ to XML</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Normal</StyleName>  
    <Text></Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Normal</StyleName>  
    <Text>The following example prints to the console.</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Normal</StyleName>  
    <Text></Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text>using System;</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text></Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text>class Program {</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text>    public static void (string[] args) {</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text>        Console.WriteLine("Hello World");</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text>    }</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text>}</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Normal</StyleName>  
    <Text></Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Normal</StyleName>  
    <Text>This example produces the following output:</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Normal</StyleName>  
    <Text></Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text>Hello World</Text>  
  </Paragraph>  
</Root>  
```  
  
## <a name="next-steps"></a><span data-ttu-id="7d70e-116">Další kroky</span><span class="sxs-lookup"><span data-stu-id="7d70e-116">Next Steps</span></span>  
 <span data-ttu-id="7d70e-117">V dalším příkladu se dotazuje na vyhledání veškerého textu v dokumentu aplikace Word:</span><span class="sxs-lookup"><span data-stu-id="7d70e-117">In the next example, you'll query to find all the text in a Word document:</span></span>  
  
- [<span data-ttu-id="7d70e-118">Hledání textu v dokumentech aplikace WordC#()</span><span class="sxs-lookup"><span data-stu-id="7d70e-118">Finding Text in Word Documents (C#)</span></span>](./finding-text-in-word-documents.md)  
  