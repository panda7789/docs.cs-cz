---
title: Načítání textu odstavců (C#)
ms.date: 07/20/2015
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
ms.openlocfilehash: 07a289ec8c3f0c783a9c85cb1d25d17164008e06
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327155"
---
# <a name="retrieving-the-text-of-the-paragraphs-c"></a>Načítání textu odstavců (C#)
Tento příklad vychází na předchozí příklad, [načítání odstavců a jejich styly (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md). Tento nový příklad načte text jednotlivých odstavců jako řetězec.  
  
 K získání textu, v tomto příkladu přidá další dotaz, který iteruje kolekcí anonymní typy a projekty novou kolekci anonymní typ s přidání nového člena, `Text`. Použije <xref:System.Linq.Enumerable.Aggregate%2A> operátor standardní dotazu k řetězení více řetězců do jednoho řetězce.  
  
 Tento postup (tedy první promítnutí do kolekce anonymního typu a potom pomocí této kolekce do projektu do nové kolekce anonymního typu) je běžné a užitečné stylu. Tento dotaz může byla zapsána bez na první anonymní typ projekce. Ale kvůli opožděné vyhodnocení to tak nepoužívá mnoho dalších výpočetní výkon. Stylu vytváří více krátké povahy objektů v haldě, ale to nesnižuje podstatně výkon.  
  
 Samozřejmě by bylo možné vytvořit jeden dotaz, který obsahuje funkci pro načtení odstavců, styl jednotlivých odstavců a každý odstavec. Ale často je užitečné rozdělit složitější dotaz do více dotazů, protože výsledný kód je více modulární a jednodušší správu. Kromě toho pokud potřebujete znovu použít část dotazu, aby bylo jednodušší refactor Pokud dotazy jsou zapsány tímto způsobem.  
  
 Tyto dotazy, které jsou zřetězené společně, použijte zpracování modelu, který je podrobně v tématu [kurz: řetězení dotazy společně (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md).  
  
## <a name="example"></a>Příklad  
 Tento příklad zpracuje WordprocessingML dokumentu, určení uzlu elementu, název stylu a každý odstavec. Tento příklad vychází v předchozích příkladech v tomto kurzu. Nový dotaz se nazývá v komentáře v kódu níže.  
  
 Pokyny pro vytvoření zdrojový dokument v tomto příkladu najdete v tématu [vytváření zdroj Office otevřít dokument XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
 Tento příklad používá třídy z WindowsBase sestavení. Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.  
  
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
  
 Tento příklad vytvoří následující výstup v případě použitého pro dokument popsané v [vytváření zdroj Office otevřít dokument XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
```  
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
 Další příklad ukazuje, jak používat metody rozšíření, místo <xref:System.Linq.Enumerable.Aggregate%2A>, aby řetězení více řetězců do jednoho řetězce.  
  
-   [Refaktoring pomocí metody rozšíření (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a>Viz také  
 [Kurz: Manipulace se obsah v dokumentu WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)  
 [Odložené provedení a opožděné vyhodnocení v technologii LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
