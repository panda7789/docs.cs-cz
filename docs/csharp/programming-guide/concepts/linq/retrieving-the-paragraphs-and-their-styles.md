---
title: Načtení odstavců a jejich stylů (C#)
ms.date: 07/20/2015
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
ms.openlocfilehash: 9edbaaf004018a26b84539d1e8ab133af5dca934
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66483883"
---
# <a name="retrieving-the-paragraphs-and-their-styles-c"></a>Načtení odstavců a jejich stylů (C#)
V tomto příkladu jsme vytvořit dotaz, který načte uzly odstavců z dokumentu WordprocessingML. Styl k jednotlivým odstavcům také identifikuje.  
  
 Tento dotaz je založena na dotazu v předchozím příkladu [vyhledání výchozího stylu odstavce (C#)](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), který načte výchozí styl seznamu styly. Tyto informace jsou nezbytné, aby dotaz můžete identifikovat styl odstavce, které nemají explicitně nastavit styl. Styly odstavci, se konfigurují pomocí `w:pPr` element; Pokud odstavce neobsahuje tohoto prvku, je naformátována pomocí výchozího stylu.  
  
 Toto téma vysvětluje význam některé části dotazu a potom se zobrazí dotaz jako součást kompletní, funkční příklad.  
  
## <a name="example"></a>Příklad  
 Zdrojový dotaz pro načtení všech odstavce v dokumentu a jejich stylů vypadá takto:  
  
```csharp  
xDoc.Root.Element(w + "body").Descendants(w + "p")  
```  
  
 Tento výraz je podobný zdroje dotazu v předchozím příkladu [hledání výchozí styl odstavce (C#)](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md). Hlavním rozdílem je, že používá <xref:System.Xml.Linq.XContainer.Descendants%2A> osy místo <xref:System.Xml.Linq.XContainer.Elements%2A> osy. Použije dotaz <xref:System.Xml.Linq.XContainer.Descendants%2A> osy vzhledem k tomu, že v dokumentech, které mají oddíly, odstavců nebudou přímé podřízené objekty daného elementu těla; místo toho odstavců bude dvě úrovně dolů v hierarchii. S použitím <xref:System.Xml.Linq.XContainer.Descendants%2A> osy, kód bude fungovat z Určuje, jestli dokument používá oddíly.  
  
## <a name="example"></a>Příklad  
 Použije dotaz `let` klauzule určit element, který obsahuje uzel stylu. Pokud neexistuje žádný element, pak `styleNode` je nastavena na `null`:  
  
```csharp  
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()  
```  
  
 `let` Nejdřív pomocí klauzule <xref:System.Xml.Linq.XContainer.Elements%2A> osy k vyhledání všech elementů s názvem `pPr`, použije <xref:System.Xml.Linq.Extensions.Elements%2A> metodu rozšíření k vyhledání všech podřízených elementů s názvem `pStyle`a nakonec používá <xref:System.Linq.Enumerable.FirstOrDefault%2A> standardního dotazu operátor pro převod kolekce na jednotlivý prvek. Pokud kolekce je prázdná, `styleNode` je nastavena na `null`. To je užitečné idiom Hledat `pStyle` uzel potomka. Všimněte si, že pokud `pPr` podřízený uzel se buď neexistuje, kód neodpovídá ani selhání vyvoláním výjimky; místo toho `styleNode` je nastavena na `null`, což je požadované chování tohoto `let` klauzuli.  
  
 Dotaz projekty kolekce anonymního typu se dvěma členy `StyleName` a `ParagraphNode`.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu zpracovává dokumentu WordprocessingML načítání uzly odstavců z dokumentu WordprocessingML. Styl k jednotlivým odstavcům také identifikuje. Tento příklad je založen na předchozí příklady v tomto kurzu. Nový dotaz je uvedeny v komentářích v následujícím kódu.  
  
 Můžete najít pokyny pro vytvoření zdrojového dokumentu v tomto příkladu v [vytváření zdroj Office Open XML dokumentu (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
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
  
 Tento příklad vytvoří následující výstup při použití u dokumentu je popsáno v [vytváření zdroj Office Open XML dokumentu (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
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
 V dalším tématu [načtení textu odstavců (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), vytvoříte dotaz pro načtení textu odstavců.  
  
## <a name="see-also"></a>Viz také:

- [Kurz: Manipulace s obsahem v dokumentu WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/shape-of-wordprocessingml-documents.md)
