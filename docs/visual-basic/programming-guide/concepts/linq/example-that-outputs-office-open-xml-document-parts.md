---
title: Příklad, jehož výstupem jsou části dokumentu Office Open XML
ms.date: 07/20/2015
ms.assetid: a951925b-c985-48ed-b215-2a68b58f1ae5
ms.openlocfilehash: 47a4ac649fb370145962247e07e1d8841411cac0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353502"
---
# <a name="example-that-outputs-office-open-xml-document-parts-visual-basic"></a><span data-ttu-id="8e4bb-102">Example that Outputs Office Open XML Document Parts (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e4bb-102">Example that Outputs Office Open XML Document Parts (Visual Basic)</span></span>
<span data-ttu-id="8e4bb-103">This topic shows how to open an Office Open XML document and access parts within it.</span><span class="sxs-lookup"><span data-stu-id="8e4bb-103">This topic shows how to open an Office Open XML document and access parts within it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e4bb-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="8e4bb-104">Example</span></span>  
 <span data-ttu-id="8e4bb-105">The following example opens an Office Open XML document, and prints the document part and the style part to the console.</span><span class="sxs-lookup"><span data-stu-id="8e4bb-105">The following example opens an Office Open XML document, and prints the document part and the style part to the console.</span></span>  
  
 <span data-ttu-id="8e4bb-106">This example uses classes from the WindowsBase assembly.</span><span class="sxs-lookup"><span data-stu-id="8e4bb-106">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="8e4bb-107">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="8e4bb-107">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Const fileName As String = "SampleDoc.docx"  
  
Const documentRelationshipType As String = _  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
Const stylesRelationshipType As String = _  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
Const wordmlNamespace As String = _  
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
Dim w As XNamespace = wordmlNamespace  
  
Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
    Dim docPackageRelationship As PackageRelationship = _  
      wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
    If docPackageRelationship IsNot Nothing Then  
        Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), _  
          docPackageRelationship.TargetUri)  
        Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
        ' Load the document XML in the part into an XDocument instance.  
        Dim xdoc As XDocument = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
        Console.WriteLine("TargetUri:{0}", docPackageRelationship.TargetUri)  
        Console.WriteLine("==================================================================")  
        Console.WriteLine(xdoc.Root)  
        Console.WriteLine()  
  
        ' Find the styles part. There will only be one.  
        Dim styleRelation As PackageRelationship = _  
          documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
        If styleRelation IsNot Nothing Then  
            Dim styleUri As Uri = _  
              PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
            Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)  
  
            ' Load the style XML in the part into an XDocument instance.  
            Dim styleDoc As XDocument = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
  
            Console.WriteLine("TargetUri:{0}", styleRelation.TargetUri)  
            Console.WriteLine("==================================================================")  
            Console.WriteLine(styleDoc.Root)  
            Console.WriteLine()  
        End If  
    End If  
End Using  
```  
  
## <a name="see-also"></a><span data-ttu-id="8e4bb-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8e4bb-108">See also</span></span>

- [<span data-ttu-id="8e4bb-109">Details of Office Open XML WordprocessingML Documents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e4bb-109">Details of Office Open XML WordprocessingML Documents (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)
