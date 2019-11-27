---
title: Tvar dokumentů WordprocessingML
ms.date: 07/20/2015
ms.assetid: 2dfb446b-5a07-4c00-9ab3-a74ba734ff3a
ms.openlocfilehash: 64e9ca280c000ba488bfc72248bd83e37474f043
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350606"
---
# <a name="shape-of-wordprocessingml-documents-visual-basic"></a>Tvar dokumentů WordprocessingML (Visual Basic)
Toto téma představuje tvar XML dokumentu WordprocessingML.  
  
## <a name="microsoft-office-formats"></a>Formáty systém Microsoft Office  
 Nativní formát souboru pro 2007 systém Microsoft Office je Office Open XML (obvykle se označuje jako Open XML). Open XML je formát založený na jazyce XML, který Standard ECMA používá a právě prochází procesem standardů ISO-IEC. Jazyk značek pro soubory pro zpracování textu v jazyce Open XML se nazývá WordprocessingML. Tento kurz používá jako vstup pro příklady zdrojové soubory WordprocessingML.  
  
 Pokud používáte systém Microsoft Office 2003, můžete dokumenty ukládat ve formátu Office Open XML, pokud jste nainstalovali sadu systém Microsoft Office Compatibility Pack pro formáty souborů Word, Excel a PowerPoint 2007.  
  
## <a name="the-shape-of-wordprocessingml-documents"></a>Tvar dokumentů WordprocessingML  
 První věc, kterou je třeba pochopit, je tvar dokumentů WordprocessingML. WordprocessingML dokument obsahuje element tělo (nazvaný `w:body`), který obsahuje odstavce v dokumentu. Každý odstavec obsahuje jedno nebo více textových běhů (s názvem `w:r`). Každý běh textu obsahuje jednu nebo více textových částí (s názvem `w:t`).  
  
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
  
 Tento příklad používá třídy nalezené v sestavení WindowsBase. Používá typy v oboru názvů <xref:System.IO.Packaging?displayProperty=nameWithType>.  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    Sub Main()  
        Dim documentRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
  
        Using wdPackage As Package = _  
          Package.Open("SampleDoc.docx", _  
                       FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = wdPackage _  
                .GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri( _  
                            New Uri("/", UriKind.Relative), _  
                            docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                ' Get the officeDocument part from the package.  
                ' Load the XML in the part into an XDocument instance.  
                Dim xDoc As XDocument = _  
                    XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
                Console.WriteLine(xDoc.Root)  
            End If  
        End Using  
    End Sub  
End Module  
```  
  
## <a name="external-resources"></a>Externí prostředky  
 [Představení formátů souborů XML sady Office (2007)](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205(v=office.12))  
  
 [Přehled WordprocessingML](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812(v=office.11))  
  
 [Office 2003: Stránka pro stažení referenčních schémat XML](https://go.microsoft.com/fwlink/?LinkId=98095)  
  
## <a name="see-also"></a>Viz také:

- [Kurz: manipulace s obsahem v dokumentu WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
