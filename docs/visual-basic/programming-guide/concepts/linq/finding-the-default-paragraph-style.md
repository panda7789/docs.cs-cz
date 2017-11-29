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
# <a name="finding-the-default-paragraph-style-visual-basic"></a><span data-ttu-id="68bcf-102">Hledání výchozí styl odstavce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68bcf-102">Finding the Default Paragraph Style (Visual Basic)</span></span>
<span data-ttu-id="68bcf-103">První úlohou manipulace s nimi informace v dokumentu WordprocessingML kurzu je najít výchozí styl odstavců v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="68bcf-103">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68bcf-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="68bcf-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="68bcf-105">Popis</span><span class="sxs-lookup"><span data-stu-id="68bcf-105">Description</span></span>  
 <span data-ttu-id="68bcf-106">Následující příklad otevře dokument Office Open XML WordprocessingML, vyhledá části dokumentu a stylu balíčku a potom provede dotaz, který vyhledá výchozí název stylu.</span><span class="sxs-lookup"><span data-stu-id="68bcf-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="68bcf-107">Informace o balíčcích dokumentu Office Open XML a skládají se z části najdete v tématu [podrobnosti systému Office otevřít WordprocessingML dokumentů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="68bcf-107">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).</span></span>  
  
 <span data-ttu-id="68bcf-108">Tento dotaz najde uzel s názvem `w:style` , má atribut s názvem `w:type` s hodnotou "odstavec", a má také atribut pojmenovaný `w:default` s hodnotou "1".</span><span class="sxs-lookup"><span data-stu-id="68bcf-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="68bcf-109">Vzhledem k tomu, že budou existovat jenom jeden uzel XML s těmito atributy, pomocí dotazu <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operátor převést kolekci typu singleton.</span><span class="sxs-lookup"><span data-stu-id="68bcf-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="68bcf-110">Potom získá hodnotu atributu s názvem `w:styleId`.</span><span class="sxs-lookup"><span data-stu-id="68bcf-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="68bcf-111">Tento příklad používá třídy z WindowsBase sestavení.</span><span class="sxs-lookup"><span data-stu-id="68bcf-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="68bcf-112">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="68bcf-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="68bcf-113">Kód</span><span class="sxs-lookup"><span data-stu-id="68bcf-113">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="68bcf-114">Komentáře</span><span class="sxs-lookup"><span data-stu-id="68bcf-114">Comments</span></span>  
 <span data-ttu-id="68bcf-115">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="68bcf-115">This example produces the following output:</span></span>  
  
```  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="68bcf-116">Další kroky</span><span class="sxs-lookup"><span data-stu-id="68bcf-116">Next Steps</span></span>  
 <span data-ttu-id="68bcf-117">V dalším příkladu vytvoříte podobné dotaz, který vyhledá všechny odstavce do dokumentu a jejich styly:</span><span class="sxs-lookup"><span data-stu-id="68bcf-117">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
-   [<span data-ttu-id="68bcf-118">Načítání odstavců a jejich styly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68bcf-118">Retrieving the Paragraphs and Their Styles (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)  
  
## <a name="see-also"></a><span data-ttu-id="68bcf-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="68bcf-119">See Also</span></span>  
 [<span data-ttu-id="68bcf-120">Kurz: Manipulace se obsah v dokumentu WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68bcf-120">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
