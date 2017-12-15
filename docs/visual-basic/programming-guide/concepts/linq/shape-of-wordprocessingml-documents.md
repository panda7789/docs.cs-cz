---
title: Tvar WordprocessingML dokumenty (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dfb446b-5a07-4c00-9ab3-a74ba734ff3a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5809e8148e7ac426b876ad11948878ee0bfcd016
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/14/2017
---
# <a name="shape-of-wordprocessingml-documents-visual-basic"></a>Tvar WordprocessingML dokumenty (Visual Basic)
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
 [Představení formáty souborů Office (2007) Open XML](http://go.microsoft.com/fwlink/?LinkId=98093)  
  
 [Přehled WordprocessingML](http://go.microsoft.com/fwlink/?LinkId=98094)  
  
 [Office 2003: Stáhnout schémat XML odkaz na stránku](http://go.microsoft.com/fwlink/?LinkId=98095)  
  
## <a name="see-also"></a>Viz také  
 [Kurz: Manipulace se obsah v dokumentu WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
