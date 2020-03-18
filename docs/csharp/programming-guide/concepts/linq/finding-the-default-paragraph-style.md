---
title: Nalezení výchozího odstavcového stylu (C#)
ms.date: 07/20/2015
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: 8cc1f1b9df208b0b180e5fe4a50922b5ee46b480
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169529"
---
# <a name="finding-the-default-paragraph-style-c"></a>Nalezení výchozího odstavcového stylu (C#)
První úkol v manipulaci s informacemi v kurzu dokumentu WordprocessingML je najít výchozí styl odstavců v dokumentu.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad otevře dokument Office Open XML WordprocessingML, vyhledá části balíčku a styly a potom snímá dotaz, který vyhledá výchozí název stylu. Informace o balíčcích dokumentů Office Open XML a jejich částech naleznete [v tématu Podrobnosti o dokumentech Pm Open XML WordprocessingML Documents (C#).](./wordprocessingml-document-with-styles.md)  
  
 Dotaz vyhledá uzel s `w:style` názvem, který `w:type` má atribut s názvem s hodnotou `w:default` "paragraph" a má také atribut s názvem s hodnotou "1". Vzhledem k tomu, že bude existovat pouze jeden <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> uzel XML s těmito atributy, dotaz používá operátor převést kolekci na singleton. Potom získá hodnotu atributu s `w:styleId`názvem .  
  
 Tento příklad používá třídy z sestavení WindowsBase. Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.  
  
### <a name="code"></a>kód  
  
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
  
// The following query finds all the paragraphs that have the default style.  
string defaultStyle =
    (string)(  
        from style in styleDoc.Root.Elements(w + "style")  
        where (string)style.Attribute(w + "type") == "paragraph"&&  
              (string)style.Attribute(w + "default") == "1"  
              select style  
    ).First().Attribute(w + "styleId");  
  
Console.WriteLine("The default style is: {0}", defaultStyle);  
```  
  
### <a name="comments"></a>Komentáře  
 Tento příklad vytváří následující výstup:  
  
```output  
The default style is: Normal  
```  
  
## <a name="next-steps"></a>Další kroky  
 V dalším příkladu vytvoříte podobný dotaz, který vyhledá všechny odstavce v dokumentu a jejich styly:  
  
- [Načítání odstavců a jejich stylů (C#)](./retrieving-the-paragraphs-and-their-styles.md)  
