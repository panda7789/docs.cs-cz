---
title: Načtení textu odstavců (C#)
ms.date: 07/20/2015
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
ms.openlocfilehash: cedca9df84ee687a9e304cde0015b46d07956364
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423331"
---
# <a name="retrieving-the-text-of-the-paragraphs-c"></a>Načtení textu odstavců (C#)
Tento příklad sestaví v předchozím příkladu [a načítá odstavce a jejich stylyC#()](./retrieving-the-paragraphs-and-their-styles.md). Tento nový příklad načte text každého odstavce jako řetězec.  
  
 Chcete-li načíst text, tento příklad přidá další dotaz, který prochází kolekcí anonymních typů a projekty nové kolekce anonymního typu s přidáním nového člena, `Text`. Používá operátor dotazu <xref:System.Linq.Enumerable.Aggregate%2A> Standard k zřetězení více řetězců do jednoho řetězce.  
  
 Tato technika (to znamená, že nejprve procházíte do kolekce anonymního typu a pak tuto kolekci použijete pro projekt k nové kolekci anonymního typu) je běžné a užitečné idiom. Tento dotaz může být zapsaný bez projekce prvního anonymního typu. Z důvodu opožděného vyhodnocení ale nevyužívá mnohem další výpočetní výkon. Idiom vytváří v haldě krátkodobé objekty pro zpracování, ale v podstatě nesnižuje výkon.  
  
 Samozřejmě by bylo možné napsat jeden dotaz, který obsahuje funkce pro načtení odstavců, styl každého odstavce a text každého odstavce. Často je však užitečné rozdělit složitější dotaz do několika dotazů, protože výsledný kód je více modulární a snazší pro údržbu. Kromě toho, pokud potřebujete znovu použít část dotazu, je snazší Refaktorovat, pokud jsou dotazy zapisovány tímto způsobem.  
  
 Tyto dotazy, které jsou zřetězeny společně, používají model zpracování, který je podrobně prověřen v tématu [kurz: zřetězení dotazů společněC#()](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
## <a name="example"></a>Příklad  
 Tento příklad zpracovává dokument WordprocessingML, určuje uzel elementu, název stylu a text každého odstavce. Tento příklad sestaví na předchozích příkladech v tomto kurzu. Nový dotaz se zavolá v komentářích v následujícím kódu.  
  
 Pokyny k vytvoření zdrojového dokumentu pro tento příklad najdete v tématu [vytvoření zdrojového dokumentu XML (C#) pro zdrojový Office](./creating-the-source-office-open-xml-document.md).  
  
 Tento příklad používá třídy ze sestavení WindowsBase. Používá typy v oboru názvů <xref:System.IO.Packaging?displayProperty=nameWithType>.  
  
```csharp  
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
            Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
            PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
            //  Load the style XML in the part into an XDocument instance.  
            styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
        }  
    }  
}  
  
string defaultStyle =   
    (string)(  
        from style in styleDoc.Root.Elements(w + "style")  
        where (string)style.Attribute(w + "type") == "paragraph"&&  
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
  
// Following is the new query that retrieves the text of  
// each paragraph.  
var paraWithText =  
    from para in paragraphs  
    select new  
    {  
        ParagraphNode = para.ParagraphNode,  
        StyleName = para.StyleName,  
        Text = para  
               .ParagraphNode  
               .Elements(w + "r")  
               .Elements(w + "t")  
               .Aggregate(  
                   new StringBuilder(),  
                   (s, i) => s.Append((string)i),  
                   s => s.ToString()  
               )  
    };  
  
foreach (var p in paraWithText)  
    Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
```  
  
 Tento příklad vytvoří následující výstup při použití v dokumentu popsaném v [tématu vytvoření zdrojového dokumentu XML pro OfficeC#()](./creating-the-source-office-open-xml-document.md).  
  
```output  
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<  
StyleName:Normal ><  
StyleName:Normal >The following example prints to the console.<  
StyleName:Normal ><  
StyleName:Code >using System;<  
StyleName:Code ><  
StyleName:Code >class Program {<  
StyleName:Code >    public static void (string[] args) {<  
StyleName:Code >        Console.WriteLine("Hello World");<  
StyleName:Code >    }<  
StyleName:Code >}<  
StyleName:Normal ><  
StyleName:Normal >This example produces the following output:<  
StyleName:Normal ><  
StyleName:Code >Hello World<  
```  
  
## <a name="next-steps"></a>Další kroky  
 Další příklad ukazuje, jak použít rozšiřující metodu namísto <xref:System.Linq.Enumerable.Aggregate%2A>, k zřetězení více řetězců do jednoho řetězce.  
  
- [Refaktoring pomocí metody rozšíření (C#)](./refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a>Viz také:

- [Kurz: manipulace s obsahem v dokumentu WordprocessingML (C#)](shape-of-wordprocessingml-documents.md)
- [Odložené provádění a opožděné vyhodnocení v LINQ to XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
