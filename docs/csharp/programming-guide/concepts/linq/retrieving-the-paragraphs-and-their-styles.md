---
title: Načítání odstavců a jejich stylů (C#)
ms.date: 07/20/2015
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
ms.openlocfilehash: 47127b6f1d6bfaa0d8d93333882a0d0b59f1bae6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168294"
---
# <a name="retrieving-the-paragraphs-and-their-styles-c"></a>Načítání odstavců a jejich stylů (C#)
V tomto příkladu napíšeme dotaz, který načte uzly odstavce z dokumentu Wordprocessing ML. Také identifikuje styl každého odstavce.  
  
 Tento dotaz vychází z dotazu v předchozím příkladu [Hledání výchozího odstavcového stylu (C#),](./finding-the-default-paragraph-style.md)který načte výchozí styl ze seznamu stylů. Tyto informace jsou vyžadovány tak, aby dotaz mohl identifikovat styl odstavců, které nemají explicitně nastavený styl. Odstavcové styly `w:pPr` jsou nastaveny prostřednictvím prvku; Pokud odstavec tento prvek neobsahuje, je formátován s výchozím stylem.  
  
 Toto téma vysvětluje význam některých částí dotazu a potom zobrazí dotaz jako součást úplného, pracovního příkladu.  
  
## <a name="example"></a>Příklad  
 Zdroj dotazu pro načtení všech odstavců v dokumentu a jejich styly je následující:  
  
```csharp  
xDoc.Root.Element(w + "body").Descendants(w + "p")  
```  
  
 Tento výraz je podobný zdroji dotazu v předchozím příkladu [Hledání výchozího odstavcového stylu (C#).](./finding-the-default-paragraph-style.md) Hlavní rozdíl spočá, že používá osu <xref:System.Xml.Linq.XContainer.Descendants%2A> namísto osy. <xref:System.Xml.Linq.XContainer.Elements%2A> Dotaz používá <xref:System.Xml.Linq.XContainer.Descendants%2A> osu, protože v dokumentech, které mají oddíly, odstavce nebudou přímými podřízenými prvky těla; spíše odstavce budou v hierarchii o dvě úrovně níže. Pomocí <xref:System.Xml.Linq.XContainer.Descendants%2A> osy bude kód fungovat, zda dokument používá oddíly.  
  
## <a name="example"></a>Příklad  
 Dotaz používá `let` klauzuli k určení prvku, který obsahuje uzel stylu. Pokud není žádný prvek, `styleNode` pak `null`je nastavena na :  
  
```csharp  
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()  
```  
  
 `let` Klauzule nejprve <xref:System.Xml.Linq.XContainer.Elements%2A> používá osu `pPr`najít všechny <xref:System.Xml.Linq.Extensions.Elements%2A> prvky s názvem `pStyle`, pak používá <xref:System.Linq.Enumerable.FirstOrDefault%2A> metodu rozšíření najít všechny podřízené prvky s názvem a nakonec používá operátor standardní dotaz převést kolekci na singleton. Pokud je kolekce `styleNode` prázdná, `null`je nastavena na . To to je užitečné idiom `pStyle` hledat uzel potomka. Všimněte si, že pokud `pPr` podřízený uzel neexistuje, kód neselže ani nepodaří vyvoláním výjimky; místo `styleNode` , je `null`nastavena na , `let` což je požadované chování této klauzule.  
  
 Dotaz projekty kolekce anonymního typu se `StyleName` `ParagraphNode`dvěma členy a .  
  
## <a name="example"></a>Příklad  
 Tento příklad zpracuje dokument WordprocessingML, načtení odstavcových uzlů z dokumentu WordprocessingML. Také identifikuje styl každého odstavce. Tento příklad vychází z předchozích příkladů v tomto kurzu. Nový dotaz je volán v komentářích v níže uvedeném kódu.  
  
 Pokyny pro vytvoření zdrojového dokumentu pro tento příklad naleznete v [části Vytvoření dokumentu Open XML (C#) zdrojové sady Office](./creating-the-source-office-open-xml-document.md).  
  
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
  
 Tento příklad vytvoří následující výstup při použití na dokument popsaný v [části Vytvoření dokumentu Open XML (C#) zdrojové kanceláře](./creating-the-source-office-open-xml-document.md).  
  
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
 V dalším tématu [Načítání textu odstavců (C#)](./retrieving-the-text-of-the-paragraphs.md)vytvoříte dotaz pro načtení textu odstavců.  
  
## <a name="see-also"></a>Viz také

- [Kurz: Manipulace s obsahem v dokumentu WordprocessingML (C#)](./shape-of-wordprocessingml-documents.md)
