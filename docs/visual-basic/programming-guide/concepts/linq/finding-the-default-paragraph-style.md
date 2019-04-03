---
title: Vyhledání výchozího stylu odstavce (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9d094a4a-ec8c-41b0-b7ab-a3deb2a01d45
ms.openlocfilehash: 0694c9144e44e4a5de262f97581eb18943937243
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841097"
---
# <a name="finding-the-default-paragraph-style-visual-basic"></a>Vyhledání výchozího stylu odstavce (Visual Basic)
První úkol v manipulaci s informace v dokumentu WordprocessingML kurzu je vyhledání výchozího stylu odstavce v dokumentu.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad otevře dokumentu Office Open XML WordprocessingML, najde dokument a styl součástí balíčku a pak provede dotaz, který vyhledá výchozí název stylu. Informace o balíčcích dokumentu Office Open XML a skládají se z části najdete v tématu [podrobnosti z Office Open XML WordprocessingML dokumentů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).  
  
 Tento dotaz najde uzel s názvem `w:style` , který má atribut s názvem `w:type` s hodnotou "odstavec", a také atribut s názvem `w:default` s hodnotou "1". Vzhledem k tomu, že bude existovat jenom jeden uzel XML s těmito atributy, pomocí dotazu <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operátor k převodu kolekce na jednotlivý prvek. Potom získá hodnotu atributu s názvem `w:styleId`.  
  
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
 V následujícím příkladu vytvoříte podobně jako dotaz, který najde všechny odstavce v dokumentu a jejich stylů:  
  
-   [Načtení odstavců a jejich stylů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)  
  
## <a name="see-also"></a>Viz také:

- [Kurz: Manipulace s obsahem v dokumentu WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
