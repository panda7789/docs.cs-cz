---
title: Vyhledání výchozího stylu odstavce
ms.date: 07/20/2015
ms.assetid: 9d094a4a-ec8c-41b0-b7ab-a3deb2a01d45
ms.openlocfilehash: b70ae72c293d00c4f7b7a2601bfd20b85702b6d5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398074"
---
# <a name="finding-the-default-paragraph-style-visual-basic"></a><span data-ttu-id="6a7e3-102">Hledání výchozího stylu odstavce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a7e3-102">Finding the Default Paragraph Style (Visual Basic)</span></span>
<span data-ttu-id="6a7e3-103">Prvním úkolem při manipulaci s informacemi v WordprocessingML dokumentu je najít výchozí styl odstavců v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="6a7e3-103">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a7e3-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="6a7e3-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="6a7e3-105">Description</span><span class="sxs-lookup"><span data-stu-id="6a7e3-105">Description</span></span>  
 <span data-ttu-id="6a7e3-106">Následující příklad otevře dokument Office Open XML WordprocessingML, vyhledá části dokumentu a stylu a potom spustí dotaz, který najde výchozí název stylu.</span><span class="sxs-lookup"><span data-stu-id="6a7e3-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="6a7e3-107">Informace o balíčcích dokumentů Office Open XML a částech, ze kterých se skládají, najdete v tématu [Podrobnosti o dokumentech Office Open XML WordprocessingML (Visual Basic)](details-of-office-open-xml-wordprocessingml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="6a7e3-107">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (Visual Basic)](details-of-office-open-xml-wordprocessingml-documents.md).</span></span>  
  
 <span data-ttu-id="6a7e3-108">Dotaz najde uzel s názvem `w:style` , který má atribut s názvem `w:type` s hodnotou "Paragraph", a má také atribut s názvem `w:default` "1".</span><span class="sxs-lookup"><span data-stu-id="6a7e3-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="6a7e3-109">Vzhledem k tomu, že bude existovat pouze jeden uzel XML s těmito atributy, dotaz použije <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operátor pro převod kolekce na typ singleton.</span><span class="sxs-lookup"><span data-stu-id="6a7e3-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="6a7e3-110">Pak získá hodnotu atributu s názvem `w:styleId` .</span><span class="sxs-lookup"><span data-stu-id="6a7e3-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="6a7e3-111">Tento příklad používá třídy ze sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="6a7e3-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="6a7e3-112">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6a7e3-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6a7e3-113">Kód</span><span class="sxs-lookup"><span data-stu-id="6a7e3-113">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="6a7e3-114">Komentáře</span><span class="sxs-lookup"><span data-stu-id="6a7e3-114">Comments</span></span>  
 <span data-ttu-id="6a7e3-115">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6a7e3-115">This example produces the following output:</span></span>  
  
```console  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="6a7e3-116">Další kroky</span><span class="sxs-lookup"><span data-stu-id="6a7e3-116">Next Steps</span></span>  
 <span data-ttu-id="6a7e3-117">V dalším příkladu vytvoříte podobný dotaz, který najde všechny odstavce v dokumentu a jejich styly:</span><span class="sxs-lookup"><span data-stu-id="6a7e3-117">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
- [<span data-ttu-id="6a7e3-118">Načítání odstavců a jejich stylů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a7e3-118">Retrieving the Paragraphs and Their Styles (Visual Basic)</span></span>](retrieving-the-paragraphs-and-their-styles.md)  
  
## <a name="see-also"></a><span data-ttu-id="6a7e3-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="6a7e3-119">See also</span></span>

- [<span data-ttu-id="6a7e3-120">Kurz: manipulace s obsahem v dokumentu WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a7e3-120">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](tutorial-manipulating-content-in-a-wordprocessingml-document.md)
