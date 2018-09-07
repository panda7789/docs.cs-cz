---
title: Tvar dokumentů WordprocessingML (C#)
ms.date: 07/20/2015
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
ms.openlocfilehash: aeb047f23f60ba6951950a85a6e2ef57fcbd9dda
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44080469"
---
# <a name="shape-of-wordprocessingml-documents-c"></a>Tvar dokumentů WordprocessingML (C#)
Toto téma popisuje nastavení tvaru XML dokumentu WordprocessingML.  
  
## <a name="microsoft-office-formats"></a>Formáty Microsoft Office  
 Nativní formát souborů pro systém Microsoft Office 2007 je Office Open XML (označovaného jako Open XML). Open XML je založený na formátu XML, který formát Ecma standard a je momentálně probíhá prostřednictvím procesu normy ISO / IEC. Značkovací jazyk pro soubory zpracování textu v rámci Open XML WordprocessingML nazývá. Tento kurz používá WordprocessingML zdrojové soubory jako vstup pro příklady.  
  
 Pokud používáte Microsoft Office 2003, můžete uložit dokumenty ve formát Office Open XML Pokud jste nainstalovali sadu kompatibility aplikace Microsoft Office pro Word, Excel a PowerPoint 2007 formátů.  
  
## <a name="the-shape-of-wordprocessingml-documents"></a>Tvar dokumentů WordprocessingML  
 První věc, kterou pochopit je tvar dokumentů WordprocessingML. Dokument WordprocessingML obsahuje text prvku (s názvem `w:body`), který obsahuje odstavců z dokumentu. K jednotlivým odstavcům obsahuje jeden nebo více spuštění text (s názvem `w:r`). Každý text spuštění obsahuje jeden nebo více kusů text (s názvem `w:t`).  
  
 Toto je velmi jednoduchý dokumentu WordprocessingML:  
  
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
  
 Tento dokument obsahuje dva odstavce. Oba obsahují jednoho textu s spuštění a každý text spuštění obsahuje část jednoho textu.  
  
 Nejjednodušší způsob, jak zobrazit obsah dokumentu WordprocessingML v podobě XML je ji vytvořit pomocí aplikace Microsoft Word, uložte a spusťte následující program, který vytiskne XML do konzoly.  
  
 Tento příklad používá třídy v sestavení WindowsBase. Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.  
  
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
 [Úvod do formátů souborů Office (2007) Open XML](https://msdn.microsoft.com/library/ms406049.aspx)  
 [Přehled WordprocessingML](https://msdn.microsoft.com/library/aa212812(office.11).aspx)  
 [Anatomie soubor WordProcessingML](http://officeopenxml.com/anatomyofOOXML.php)  
 [Úvod do WordprocessingML](http://ericwhite.com/blog/introduction-to-wordprocessingml-series/)  
 [Office 2003: Stáhnout schémat XML odkaz na stránku](https://www.microsoft.com/en-us/download/details.aspx?id=101)  
  
## <a name="see-also"></a>Viz také

- [Kurz: Manipulace s obsahem v dokumentu WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
