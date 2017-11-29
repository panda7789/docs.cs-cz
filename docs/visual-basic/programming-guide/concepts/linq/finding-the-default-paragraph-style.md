---
title: "Hledání výchozí styl odstavce (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d094a4a-ec8c-41b0-b7ab-a3deb2a01d45
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cd22a545f8162352050ba698717fb0ceb3a72cfc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="finding-the-default-paragraph-style-visual-basic"></a>Hledání výchozí styl odstavce (Visual Basic)
První úlohou manipulace s nimi informace v dokumentu WordprocessingML kurzu je najít výchozí styl odstavců v dokumentu.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad otevře dokument Office Open XML WordprocessingML, vyhledá části dokumentu a stylu balíčku a potom provede dotaz, který vyhledá výchozí název stylu. Informace o balíčcích dokumentu Office Open XML a skládají se z části najdete v tématu [podrobnosti systému Office otevřít WordprocessingML dokumentů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).  
  
 Tento dotaz najde uzel s názvem `w:style` , má atribut s názvem `w:type` s hodnotou "odstavec", a má také atribut pojmenovaný `w:default` s hodnotou "1". Vzhledem k tomu, že budou existovat jenom jeden uzel XML s těmito atributy, pomocí dotazu <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operátor převést kolekci typu singleton. Potom získá hodnotu atributu s názvem `w:styleId`.  
  
 Tento příklad používá třídy z WindowsBase sestavení. Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.  
  
### <a name="code"></a>Kód  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
  
    Sub Main()  
  
        Const fileName As String = "SampleDoc.docx"  
  
        Const documentRelationshipType As String = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Const stylesRelationshipType As String = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = _  
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If docPackageRelationship IsNot Nothing Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), _  
                  docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                ' Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                ' Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = _  
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If styleRelation IsNot Nothing Then  
                    Dim styleUri As Uri = _  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)  
  
                    ' Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
            End If  
        End Using  
  
        ' The following query finds all the paragraphs that have the default style.  
        Dim defParas As IEnumerable(Of XElement) = _  
            From style In styleDoc.Root.<w:style> _  
            Where style.@w:type.Equals("paragraph") And _  
                   style.@w:default.Equals("1") _  
            Select style  
        ' Then find the style of the first.  
        Dim defaultStyle As String = defParas.First().@w:styleId  
  
        Console.WriteLine("The default style is: " & defaultStyle)  
    End Sub  
End Module  
```  
  
### <a name="comments"></a>Komentáře  
 Tento příklad vytvoří následující výstup:  
  
```  
The default style is: Normal  
```  
  
## <a name="next-steps"></a>Další kroky  
 V dalším příkladu vytvoříte podobné dotaz, který vyhledá všechny odstavce do dokumentu a jejich styly:  
  
-   [Načítání odstavců a jejich styly (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)  
  
## <a name="see-also"></a>Viz také  
 [Kurz: Manipulace se obsah v dokumentu WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
