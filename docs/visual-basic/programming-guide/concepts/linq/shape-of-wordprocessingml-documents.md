---
title: Tvar dokumentů WordprocessingML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 2dfb446b-5a07-4c00-9ab3-a74ba734ff3a
ms.openlocfilehash: 30ec7a0c6b03d0c6f00561ce08cb836aab3c167b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404835"
---
# <a name="shape-of-wordprocessingml-documents-visual-basic"></a>Tvar dokumentů WordprocessingML (Visual Basic)
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
  
## <a name="external-resources"></a>Externí zdroje  
 [Úvod do formátů souborů Office (2007) Open XML](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205(v=office.12))  
  
 [Přehled WordprocessingML](https://msdn.microsoft.com/en-us/library/aa212812(office.11).aspx)  
  
 [Office 2003: Stáhnout schémat XML odkaz na stránku](https://go.microsoft.com/fwlink/?LinkId=98095)  
  
## <a name="see-also"></a>Viz také  
 [Kurz: Manipulace s obsahem v dokumentu WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
