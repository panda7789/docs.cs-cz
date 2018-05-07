---
title: Načítání odstavců a jejich styly (C#)
ms.date: 07/20/2015
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
ms.openlocfilehash: 11788c1fa46c63c78a9db0255c8e84250285863e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="retrieving-the-paragraphs-and-their-styles-c"></a>Načítání odstavců a jejich styly (C#)
V tomto příkladu jsme vytvořit dotaz, který načte odstavce uzly z WordprocessingML dokumentu. Také identifikuje styl jednotlivých odstavců.  
  
 Tento dotaz založený na dotaz v předchozím příkladu [hledání výchozí styl odstavce (C#)](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), který načte výchozí styl ze seznamu stylů. Tyto informace jsou nezbytné, aby dotaz můžete identifikovat styl odstavců, které nemají styl explicitně nastaven. Styly odstavce, se konfigurují pomocí `w:pPr` element; Pokud odstavec neobsahuje tento prvek, je formátován pomocí výchozí styl.  
  
 Toto téma vysvětluje význam některé jeho součásti dotazu a potom jako součást dokončení práce příklad ukazuje dotaz.  
  
## <a name="example"></a>Příklad  
 Zdroj dotaz pro načtení všech odstavců v dokumentu a jejich styly vypadá takto:  
  
```csharp  
xDoc.Root.Element(w + "body").Descendants(w + "p")  
```  
  
 Tento výraz je podobná zdroj dotazu v předchozím příkladu [hledání výchozí styl odstavce (C#)](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md). Hlavní rozdíl je, že používá <xref:System.Xml.Linq.XContainer.Descendants%2A> osy místo <xref:System.Xml.Linq.XContainer.Elements%2A> osy. Dotaz používá <xref:System.Xml.Linq.XContainer.Descendants%2A> osy protože v dokumentech, které mají oddíly, odstavců nebude přímé podřízené objekty daného elementu body; místo toho odstavců bude dvě úrovně dolů v hierarchii. Pomocí <xref:System.Xml.Linq.XContainer.Descendants%2A> osy, bude kód pracovat z zda dokument používá oddíly.  
  
## <a name="example"></a>Příklad  
 Dotaz používá `let` klauzule k určení elementu, který obsahuje uzel stylu. Pokud neexistuje žádný element pak `styleNode` je nastaven na `null`:  
  
```csharp  
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()  
```  
  
 `let` Nejdřív pomocí klauzule <xref:System.Xml.Linq.XContainer.Elements%2A> osy k vyhledání všech elementů s názvem `pPr`, použije <xref:System.Xml.Linq.Extensions.Elements%2A> rozšíření metody k vyhledání všech podřízených elementů s názvem `pStyle`a nakonec používá <xref:System.Linq.Enumerable.FirstOrDefault%2A> standardní dotazu operátor převést kolekci typu singleton. Pokud je kolekce prázdná, `styleNode` je nastaven na `null`. To je užitečné, stylu a Hledat `pStyle` podřízený uzel. Všimněte si, že pokud `pPr` podřízený uzel neexistuje, kód nemá ani selhání došlo k výjimce; místo toho `styleNode` je nastaven na `null`, což je toto chování žádoucí tohoto `let` klauzule.  
  
 Dotaz projekty kolekce anonymní typ s dva členy `StyleName` a `ParagraphNode`.  
  
## <a name="example"></a>Příklad  
 Tento příklad zpracuje WordprocessingML dokumentu, načítání odstavce uzly z WordprocessingML dokumentu. Také identifikuje styl jednotlivých odstavců. Tento příklad vychází v předchozích příkladech v tomto kurzu. Nový dotaz se nazývá v komentáře v kódu níže.  
  
 Pokyny pro vytvoření zdrojový dokument v tomto příkladu můžete najít [vytváření zdroj Office otevřít dokument XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
 Tento příklad používá třídy v sestavení WindowsBase. Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.  
  
```csharp  
const string fileName = "SampleDoc.docx";  
  
const string documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";  
const string wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
XDocument xDoc = null;  
XDocument styleDoc = null;  
  
using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))  
{  
    PackageRelationship docPackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();  
    if (docPackageRelationship != null)  
    {  
        Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative), docPackageRelationship.TargetUri);  
        PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
        //  Load the document XML in the part into an XDocument instance.  
        xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
        //  Find the styles part. There will only be one.  
        PackageRelationship styleRelation = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
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
  
// Following is the new query that finds all paragraphs in the  
// document and their styles.  
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
  
foreach (var p in paragraphs)  
    Console.WriteLine("StyleName:{0}", p.StyleName);  
```  
  
 Tento příklad vytvoří následující výstup v případě použitého pro dokument popsané v [vytváření zdroj Office otevřít dokument XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
```  
StyleName:Heading1  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
```  
  
## <a name="next-steps"></a>Další kroky  
 V dalším tématu [načítání textu odstavců (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), vytvoříte dotaz pro načtení textu odstavce.  
  
## <a name="see-also"></a>Viz také  
 [Kurz: Manipulace se obsah v dokumentu WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
