---
title: Načítání odstavců a jejich stylů (C#)
description: Naučte se napsat dotaz, který načte odstavce a pak určí styl každého odstavce.
ms.date: 07/20/2015
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
ms.openlocfilehash: 94d01a13485f70bc9d9cef55b5f390c3b30d7f14
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303397"
---
# <a name="retrieving-the-paragraphs-and-their-styles-c"></a>Načítání odstavců a jejich stylů (C#)
V tomto příkladu zapíšeme dotaz, který načte uzly odstavců z dokumentu WordprocessingML. Určuje také styl každého odstavce.  
  
 Tento dotaz sestaví na dotazu v předchozím příkladu a hledá [výchozí styl odstavce (C#)](./finding-the-default-paragraph-style.md), který načte výchozí styl ze seznamu stylů. Tyto informace jsou požadovány, aby dotaz mohl identifikovat styl odstavců, které nemají explicitně nastaven styl. Odstavcové styly se nastavují prostřednictvím `w:pPr` elementu; Pokud odstavec tento prvek neobsahuje, naformátuje se s výchozím stylem.  
  
 Toto téma vysvětluje význam některých částí dotazu a pak zobrazuje dotaz jako součást kompletního a funkčního příkladu.  
  
## <a name="example"></a>Příklad  
 Zdroj dotazu pro načtení všech odstavců v dokumentu a jejich stylů je následující:  
  
```csharp  
xDoc.Root.Element(w + "body").Descendants(w + "p")  
```  
  
 Tento výraz je podobný zdroji dotazu v předchozím příkladu, který [najde výchozí styl odstavce (C#)](./finding-the-default-paragraph-style.md). Hlavní rozdíl spočívá v tom, že <xref:System.Xml.Linq.XContainer.Descendants%2A> místo osy používá osu <xref:System.Xml.Linq.XContainer.Elements%2A> . Dotaz používá osu, <xref:System.Xml.Linq.XContainer.Descendants%2A> protože v dokumentech, které mají oddíly, nebudou odstavce přímo podřízeny elementu těla. místo toho budou v hierarchii tyto odstavce dvě. Pomocí <xref:System.Xml.Linq.XContainer.Descendants%2A> osy bude kód pracovat na tom, zda dokument používá oddíly.  
  
## <a name="example"></a>Příklad  
 Dotaz používá `let` klauzuli k určení prvku, který obsahuje uzel Style. Pokud není žádný element, pak `styleNode` je nastaven na `null` :  
  
```csharp  
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()  
```  
  
 `let`Klauzule nejprve používá <xref:System.Xml.Linq.XContainer.Elements%2A> osu k vyhledání všech prvků s názvem `pPr` a poté používá <xref:System.Xml.Linq.Extensions.Elements%2A> metodu rozšíření k vyhledání všech podřízených elementů s názvem `pStyle` a nakonec používá <xref:System.Linq.Enumerable.FirstOrDefault%2A> standardní operátor dotazu k převedení kolekce na typ singleton. Je-li kolekce prázdná, `styleNode` je nastavena na hodnotu `null` . Toto je užitečná idiom pro vyhledání `pStyle` podřízeného uzlu. Všimněte si, že pokud `pPr` neexistuje podřízený uzel, kód selže ani selže vyvoláním výjimky; namísto toho `styleNode` je nastavena na `null` , což je požadované chování této `let` klauzule.  
  
 Dotaz projektuje kolekci anonymního typu se dvěma členy `StyleName` a `ParagraphNode` .  
  
## <a name="example"></a>Příklad  
 Tento příklad zpracovává dokument WordprocessingML a načítá uzly odstavců z dokumentu WordprocessingML. Určuje také styl každého odstavce. Tento příklad sestaví na předchozích příkladech v tomto kurzu. Nový dotaz se zavolá v komentářích v následujícím kódu.  
  
 Pokyny pro vytvoření zdrojového dokumentu pro tento příklad najdete v [tématu vytvoření zdrojového dokumentu XML pro Office (C#)](./creating-the-source-office-open-xml-document.md).  
  
 Tento příklad používá třídy nalezené v sestavení WindowsBase. Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.  
  
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
  
 Tento příklad vytvoří následující výstup při použití v dokumentu popsaném v [tématu vytvoření zdrojového dokumentu XML pro Office (C#)](./creating-the-source-office-open-xml-document.md).  
  
```output  
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
 V dalším tématu [načtení textu odstavců (C#)](./retrieving-the-text-of-the-paragraphs.md)vytvoříte dotaz pro načtení textu odstavců.  
  
## <a name="see-also"></a>Viz také:

- [Kurz: manipulace s obsahem v dokumentu WordprocessingML (C#)](./shape-of-wordprocessingml-documents.md)
