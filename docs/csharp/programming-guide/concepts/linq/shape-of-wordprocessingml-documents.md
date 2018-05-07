---
title: Tvar WordprocessingML dokumentů (C#)
ms.date: 07/20/2015
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
ms.openlocfilehash: 0d8a80a8e7d33facd452e3b7fb31793c1ed55c58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="shape-of-wordprocessingml-documents-c"></a>Tvar WordprocessingML dokumentů (C#)
Toto téma představuje obrazec WordprocessingML dokumentu XML.  
  
## <a name="microsoft-office-formats"></a>Formáty Microsoft Office  
 Nativní formát pro systém Microsoft Office 2007 je Office Open XML (označovaného jako Open XML). Otevřete soubor XML je XML na základě formátu, který Ecma standard a je aktuálně projít proces standardy ISO / IEC. Jazyk kódu pro zpracování textu soubory v rámci Open XML se nazývá WordprocessingML. Tento kurz používá WordprocessingML zdrojové soubory jako vstup pro příklady.  
  
 Pokud používáte Microsoft Office 2003, můžete uložit dokumenty ve formátu Office Open XML Pokud jste nainstalovali sadu Microsoft Office kompatibility pro Word, Excel a PowerPoint formáty souborů 2007.  
  
## <a name="the-shape-of-wordprocessingml-documents"></a>Obrazec WordprocessingML dokumenty  
 První věc pochopit je obrazec WordprocessingML dokumenty. Dokument WordprocessingML obsahuje body element (s názvem `w:body`), který obsahuje odstavců dokumentu. Jednotlivých odstavců, obsahuje jeden nebo více spustí text (s názvem `w:r`). Každý text spustit obsahuje jeden nebo více částí textu (s názvem `w:t`).  
  
 Toto je velmi jednoduchý WordprocessingML dokumentu:  
  
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
  
 Tento dokument obsahuje dva odstavce. Oba obsahují jednoho textu s spustit a každý text spustit obsahuje část jednoho textu.  
  
 Nejjednodušší způsob, jak zobrazit obsah v dokumentu WordprocessingML ve formátu XML je vytvořit pomocí aplikace Microsoft Word, uložte ho a pak spusťte následující program, který vytiskne XML do konzoly.  
  
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
 [Představení formáty souborů Office (2007) Open XML](https://msdn.microsoft.com/library/ms406049.aspx)  
 [Přehled WordprocessingML](https://msdn.microsoft.com/library/aa212812(office.11).aspx)  
 [Anatomie WordProcessingML souboru](http://officeopenxml.com/anatomyofOOXML.php)  
 [Úvod do WordprocessingML](http://ericwhite.com/blog/introduction-to-wordprocessingml-series/)  
 [Office 2003: Stáhnout schémat XML odkaz na stránku](https://www.microsoft.com/en-us/download/details.aspx?id=101)  
  
## <a name="see-also"></a>Viz také  
 [Kurz: Manipulace se obsah v dokumentu WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
