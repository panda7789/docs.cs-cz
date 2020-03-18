---
title: Promítání XML v jiném obrazci (C#)
ms.date: 07/20/2015
ms.assetid: 4cb6b14a-32dc-4a2a-813e-bf9368fa8d86
ms.openlocfilehash: 1377df1ce7f54bc9a0f58836d7df5e5b7b54a69a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591533"
---
# <a name="projecting-xml-in-a-different-shape-c"></a>Promítání XML v jiném obrazci (C#)
Toto téma ukazuje příklad promítání XML, který je v jiném tvaru než zdrojový XML.  
  
 Mnoho typické transformace XML se skládají z řetězových dotazů, jako v tomto příkladu. Je běžné začít s nějakou formou XML, zprostředkující výsledky projektu jako kolekce anonymních typů nebo pojmenovaných typů a nakonec promítnout výsledky zpět do XML, který je ve zcela jiném tvaru než zdrojový XML.  
  
## <a name="example"></a>Příklad  
 Tento příklad zpracuje dokument WordprocessingML, načtení odstavcových uzlů z dokumentu WordprocessingML. Také identifikuje styl a text každého odstavce. Nakonec příklad projekty XML s jiným tvarem. Tento příklad vychází z předchozích příkladů v tomto kurzu. Nové prohlášení, které provádí projekci, je voláno v komentářích v níže uvedeném kódu.  
  
 Pokyny k vytvoření zdrojového dokumentu pro tento příklad naleznete [v tématu Vytvoření dokumentu Open XML (C#) zdrojové sady Office](./creating-the-source-office-open-xml-document.md).  
  
 Tento příklad používá třídy z sestavení WindowsBase. Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.  
  
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
  
 Tento příklad vytváří následující výstup:  
  
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
  
## <a name="next-steps"></a>Další kroky  
 V dalším příkladu se dotazuje, jak najít veškerý text v dokumentu aplikace Word:  
  
- [Hledání textu v dokumentech aplikace Word (C#)](./finding-text-in-word-documents.md)  
  