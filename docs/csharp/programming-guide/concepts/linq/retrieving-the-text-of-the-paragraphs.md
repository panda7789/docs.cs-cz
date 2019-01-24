---
title: Načtení textu odstavců (C#)
ms.date: 07/20/2015
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
ms.openlocfilehash: 070bf4a3254f8e30ff7f4568c283f37ca288348c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737095"
---
# <a name="retrieving-the-text-of-the-paragraphs-c"></a>Načtení textu odstavců (C#)
Tento příklad je založen na předchozím příkladu [načtení odstavců a jejich stylů (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md). Tento nový příklad načte text k jednotlivým odstavcům jako řetězec.  
  
 K získání textu, v tomto příkladu přidá další dotaz, který Iteruje přes kolekci anonymních typů a projekty novou kolekci s přidáním nového člena anonymního typu `Text`. Používá <xref:System.Linq.Enumerable.Aggregate%2A> operátor standardního dotazu pro řetězení více řetězců do jednoho řetězce.  
  
 Tato technika (to znamená, že první promítání na kolekci anonymního typu a pak pomocí této kolekce projektu do nové kolekce anonymního typu) je běžné a užitečné idiom. Tento dotaz by mohl být napsán bez promítání na první anonymního typu. Však z důvodu opožděné vyhodnocení to uděláte tak nebude používat mnoho další výpočetní výkon. Idiom vytvoří více krátký povahy objektů na haldě, ale to mít nežádoucí vliv podstatně výkonu.  
  
 Samozřejmě by bylo možné vytvořit jeden dotaz, který obsahuje funkce pro načtení odstavců, styl k jednotlivým odstavcům a každý odstavec. Ale často je užitečné rozdělit složitější dotaz do více dotazů, protože výsledný kód je modulární a jednodušší správu. Kromě toho pokud je potřeba znovu použít části dotazu, je jednodušší refaktorace Pokud dotazy se zapisují tímto způsobem.  
  
 Tyto dotazy, které jsou zřetězen dohromady, použijte zpracování modelu, který je podrobně v tématu [kurzu: Zřetězení dotazů (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md).  
  
## <a name="example"></a>Příklad  
 V tomto příkladu zpracovává dokumentu WordprocessingML, určení uzlu elementu, název stylu a každý odstavec. Tento příklad je založen na předchozí příklady v tomto kurzu. Nový dotaz je uvedeny v komentářích v následujícím kódu.  
  
 Pokyny pro vytvoření zdrojového dokumentu pro účely tohoto příkladu naleznete v tématu [vytváření zdroj Office Open XML dokumentu (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
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
  
 Tento příklad vytvoří následující výstup při použití u dokumentu je popsáno v [vytváření zdroj Office Open XML dokumentu (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
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
 Následující příklad ukazuje způsob použití metody rozšíření, namísto <xref:System.Linq.Enumerable.Aggregate%2A>pro řetězení více řetězců do jednoho řetězce.  
  
-   [Refaktoring pomocí rozšiřující metodu (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a>Viz také:

- [Kurz: Manipulace s obsahem v dokumentu WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [Odložené provedení a opožděné vyhodnocení v LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
