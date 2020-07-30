---
title: Tvar dokumentů WordprocessingML (C#)
description: Přečtěte si o formátu dokumentu WordprocessingML. Několik příkladů C# používá WordprocessingML dokument.
ms.date: 07/20/2015
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
ms.openlocfilehash: 4a7716d775a634c5ad3719714be68fce67d5cbfe
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302344"
---
# <a name="shape-of-wordprocessingml-documents-c"></a>Tvar dokumentů WordprocessingML (C#)
Toto téma představuje tvar XML dokumentu WordprocessingML.  
  
## <a name="microsoft-office-formats"></a>Formáty systém Microsoft Office  
 Nativní formát souboru pro 2007 systém Microsoft Office je Office Open XML (obvykle se označuje jako Open XML). Open XML je formát založený na jazyce XML, který Standard ECMA používá a právě prochází procesem standardů ISO-IEC. Jazyk značek pro soubory pro zpracování textu v jazyce Open XML se nazývá WordprocessingML. Tento kurz používá jako vstup pro příklady zdrojové soubory WordprocessingML.  
  
 Pokud používáte systém Microsoft Office 2003, můžete dokumenty ukládat ve formátu Office Open XML, pokud jste nainstalovali sadu systém Microsoft Office Compatibility Pack pro formáty souborů Word, Excel a PowerPoint 2007.  
  
## <a name="the-shape-of-wordprocessingml-documents"></a>Tvar dokumentů WordprocessingML  
 První věc, kterou je třeba pochopit, je tvar dokumentů WordprocessingML. WordprocessingML dokument obsahuje element tělo (pojmenovaný `w:body` ), který obsahuje odstavce v dokumentu. Každý odstavec obsahuje jedno nebo více textových běhů (s názvem `w:r` ). Každý běh textu obsahuje jednu nebo více textových částí (s názvem `w:t` ).  
  
 Následuje velmi jednoduchý dokument WordprocessingML:  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<w:document  
xmlns:ve="http://schemas.openxmlformats.org/markup-compatibility/2006"  
xmlns:o="urn:schemas-microsoft-com:office:office"  
xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"  
xmlns:m="http://schemas.openxmlformats.org/officeDocument/2006/math"  
xmlns:v="urn:schemas-microsoft-com:vml"  
xmlns:wp="http://schemas.openxmlformats.org/drawingml/2006/wordprocessingDrawing"  
xmlns:w10="urn:schemas-microsoft-com:office:word"  
xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
xmlns:wne="http://schemas.microsoft.com/office/word/2006/wordml">  
  <w:body>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is a paragraph.</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is another paragraph.</w:t>  
      </w:r>  
    </w:p>  
  </w:body>  
</w:document>  
```  
  
 Tento dokument obsahuje dva odstavce. Oba obsahují jeden textový běh a každý spuštěný text obsahuje jeden textový kámen.  
  
 Nejjednodušší způsob, jak zobrazit obsah dokumentu WordprocessingML ve formátu XML, je vytvořit ho pomocí Microsoft Wordu, uložit ho a pak spustit následující program, který vytiskne XML do konzoly.  
  
 Tento příklad používá třídy nalezené v sestavení WindowsBase. Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.  
  
```csharp  
const string documentRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string wordmlNamespace =  
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
using (Package wdPackage = Package.Open("SampleDoc.docx", FileMode.Open, FileAccess.Read))  
{  
    PackageRelationship relationship =  
        wdPackage  
        .GetRelationshipsByType(documentRelationshipType)  
        .FirstOrDefault();  
    if (relationship != null)  
    {  
        Uri documentUri =  
            PackUriHelper.ResolvePartUri(  
                new Uri("/", UriKind.Relative),  
                relationship.TargetUri);  
        PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
        //  Get the officeDocument part from the package.  
        //  Load the XML in the part into an XDocument instance.  
        XDocument xdoc =  
            XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
        Console.WriteLine(xdoc.Root);  
    }  
}  
```  
  
## <a name="external-resources"></a>Externí zdroje

- [Představení formátů souborů XML sady Office (2007)](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205%28v=office.12%29)
- [Přehled WordprocessingML](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812%28v=office.11%29)
- [Anatomie souboru WordProcessingML](http://officeopenxml.com/anatomyofOOXML.php)
- [Úvod do WordprocessingML](https://ericwhite.com/blog/introduction-to-wordprocessingml-series/)

## <a name="see-also"></a>Viz také:

- [Kurz: manipulace s obsahem v dokumentu WordprocessingML (C#)](./shape-of-wordprocessingml-documents.md)
