---
title: Hledání výchozího stylu odstavce (C#)
description: Naučte se zpracovat dokument WordprocessingML pomocí LINQ v jazyce C#. Tento příklad najde výchozí styl odstavců v dokumentu.
ms.date: 07/20/2015
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: e18bbbdbd5b2627c9ff4c3c3eedd84d7cb166a62
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103821"
---
# <a name="finding-the-default-paragraph-style-c"></a>Hledání výchozího stylu odstavce (C#)
Prvním úkolem při manipulaci s informacemi v WordprocessingML dokumentu je najít výchozí styl odstavců v dokumentu.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad otevře dokument Office Open XML WordprocessingML, vyhledá části dokumentu a stylu a potom spustí dotaz, který najde výchozí název stylu. Informace o balíčcích dokumentů Office Open XML a částech, ze kterých se skládají, najdete v tématu [Podrobnosti o Office Open XML WordprocessingML Documents (C#)](./wordprocessingml-document-with-styles.md).  
  
 Dotaz najde uzel s názvem `w:style` , který má atribut s názvem `w:type` s hodnotou "Paragraph", a má také atribut s názvem `w:default` "1". Vzhledem k tomu, že bude existovat pouze jeden uzel XML s těmito atributy, dotaz použije <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operátor pro převod kolekce na typ singleton. Pak získá hodnotu atributu s názvem `w:styleId` .  
  
 Tento příklad používá třídy ze sestavení WindowsBase. Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.  
  
### <a name="code"></a>Kód  
  
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
 Tento příklad vytvoří následující výstup:  
  
```output  
The default style is: Normal  
```  
  
## <a name="next-steps"></a>Další kroky  
 V dalším příkladu vytvoříte podobný dotaz, který najde všechny odstavce v dokumentu a jejich styly:  
  
- [Načítání odstavců a jejich stylů (C#)](./retrieving-the-paragraphs-and-their-styles.md)  
