---
title: Načítání odstavců a jejich stylů (C#)
ms.date: 07/20/2015
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
ms.openlocfilehash: ec59ef0ac36f8691ca93a4c21c5379118ee0491f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253063"
---
# <a name="retrieving-the-paragraphs-and-their-styles-c"></a>Načítání odstavců a jejich stylů (C#)
V tomto příkladu zapíšeme dotaz, který načte uzly odstavců z dokumentu WordprocessingML. Určuje také styl každého odstavce.  
  
 Tento dotaz sestaví na dotazu v předchozím příkladu a hledá [výchozí styl odstavce (C#)](./finding-the-default-paragraph-style.md), který načte výchozí styl ze seznamu stylů. Tyto informace jsou požadovány, aby dotaz mohl identifikovat styl odstavců, které nemají explicitně nastaven styl. Odstavcové styly se nastavují `w:pPr` prostřednictvím elementu; Pokud odstavec tento prvek neobsahuje, naformátuje se s výchozím stylem.  
  
 Toto téma vysvětluje význam některých částí dotazu a pak zobrazuje dotaz jako součást kompletního a funkčního příkladu.  
  
## <a name="example"></a>Příklad  
 Zdroj dotazu pro načtení všech odstavců v dokumentu a jejich stylů je následující:  
  
```csharp  
xDoc.Root.Element(w + "body").Descendants(w + "p")  
```  
  
 Tento výraz je podobný zdroji dotazu v předchozím příkladu, kde [hledání výchozího stylu odstavceC#()](./finding-the-default-paragraph-style.md). Hlavní rozdíl spočívá v tom, že místo <xref:System.Xml.Linq.XContainer.Descendants%2A> <xref:System.Xml.Linq.XContainer.Elements%2A> osy používá osu. Dotaz používá <xref:System.Xml.Linq.XContainer.Descendants%2A> osu, protože v dokumentech, které mají oddíly, nebudou odstavce přímo podřízeny elementu těla. místo toho budou v hierarchii tyto odstavce dvě. Pomocí <xref:System.Xml.Linq.XContainer.Descendants%2A> osy bude kód pracovat na tom, zda dokument používá oddíly.  
  
## <a name="example"></a>Příklad  
 Dotaz používá `let` klauzuli k určení prvku, který obsahuje uzel Style. Pokud není žádný element, pak `styleNode` je nastaven na: `null`  
  
```csharp  
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()  
```  
  
 `pPr` <xref:System.Xml.Linq.Extensions.Elements%2A> `pStyle` <xref:System.Linq.Enumerable.FirstOrDefault%2A> Klauzule nejprve <xref:System.Xml.Linq.XContainer.Elements%2A> používá osu k vyhledání všech prvků s názvem a poté používá metodu rozšíření k vyhledání všech podřízených elementů s názvem a nakonec používá standardní dotaz. `let` operátor pro převod kolekce na typ singleton. Je-li kolekce prázdná, `styleNode` je nastavena na `null`hodnotu. Toto je užitečná idiom pro vyhledání `pStyle` podřízeného uzlu. Všimněte si, že `pPr` Pokud neexistuje podřízený uzel, kód selže ani selže vyvoláním výjimky; `styleNode` namísto toho je nastavena na `null`, což je požadované chování této `let` klauzule.  
  
 Dotaz projektuje kolekci anonymního typu se dvěma členy `StyleName` a. `ParagraphNode`  
  
## <a name="example"></a>Příklad  
 Tento příklad zpracovává dokument WordprocessingML a načítá uzly odstavců z dokumentu WordprocessingML. Určuje také styl každého odstavce. Tento příklad sestaví na předchozích příkladech v tomto kurzu. Nový dotaz se zavolá v komentářích v následujícím kódu.  
  
 Pokyny pro vytvoření zdrojového dokumentu pro tento příklad najdete v [tématu vytvoření zdrojového dokumentuC#XML pro Office Open](./creating-the-source-office-open-xml-document.md).  
  
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
  
 Tento příklad vytvoří následující výstup při použití v dokumentu popsaném v [tématu vytvoření zdrojového dokumentu XML pro OfficeC#()](./creating-the-source-office-open-xml-document.md).  
  
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
 V dalším tématu [načtení textu odstavcůC#()](./retrieving-the-text-of-the-paragraphs.md)vytvoříte dotaz pro načtení textu odstavců.  
  
## <a name="see-also"></a>Viz také:

- [Kurz: Manipulace s obsahem v dokumentu WordprocessingML (C#)](./shape-of-wordprocessingml-documents.md)
