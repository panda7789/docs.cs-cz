---
title: Tvar dokumentů WordprocessingML (C#)
ms.date: 07/20/2015
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
ms.openlocfilehash: 58c028fed465f45fdcf8f63f2119eb8e8b201e32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76732670"
---
# <a name="shape-of-wordprocessingml-documents-c"></a>Tvar dokumentů WordprocessingML (C#)
Toto téma představuje obrazec XML dokumentu WordprocessingML.  
  
## <a name="microsoft-office-formats"></a>Formáty microsoft office  
 Nativní formát souboru pro systém Microsoft Office 2007 je Office Open XML (běžně nazývaný Open XML). Open XML je formát založený na xml, který standardec ecma a v současné době prochází procesem norem ISO-IEC. Značkovací jazyk pro soubory zpracování textu v otevřeném XML se nazývá WordprocessingML. Tento kurz používá wordprocessingML zdrojové soubory jako vstup pro příklady.  
  
 Pokud používáte sadu Microsoft Office 2003, můžete dokumenty uložit ve formátu Office Open XML, pokud jste nainstalovali sadu Microsoft Office Compatibility Pack pro formáty souborů aplikace Word, Excel a PowerPoint 2007.  
  
## <a name="the-shape-of-wordprocessingml-documents"></a>Obrazec wordprocessingml dokumentů  
 První věc, kterou pochopit, je tvar wordprocessingML dokumentů. WordprocessingML dokument obsahuje element těla (s názvem), `w:body`který obsahuje odstavce dokumentu. Každý odstavec obsahuje jeden nebo `w:r`více spuštění textu (s názvem ). Každé spuštění textu obsahuje jeden nebo `w:t`více textových částí (s názvem).  
  
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
  
 Tento dokument obsahuje dva odstavce. Oba obsahují jeden text spustit a každý text spustit obsahuje jeden text kus.  
  
 Nejjednodušší způsob, jak zobrazit obsah dokumentu WordprocessingML ve formuláři XML, je vytvořit jej pomocí aplikace Microsoft Word, uložit jej a spustit následující program, který vytiskne xml do konzoly.  
  
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

- [Představujeme office (2007) Formáty souborů Open XML](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205%28v=office.12%29)
- [Přehled wordprocessingml](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812%28v=office.11%29)
- [Anatomie souboru WordProcessingML](http://officeopenxml.com/anatomyofOOXML.php)
- [Úvod do wordprocessingml](https://ericwhite.com/blog/introduction-to-wordprocessingml-series/)

## <a name="see-also"></a>Viz také

- [Kurz: Manipulace s obsahem v dokumentu WordprocessingML (C#)](./shape-of-wordprocessingml-documents.md)
