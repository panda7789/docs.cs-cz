---
title: Refaktoring pomocí čisté funkce
ms.date: 07/20/2015
ms.assetid: af0ea62f-4f57-4868-b624-a85524055935
ms.openlocfilehash: 3a0365c79b8283fef242ecf8f2b68ea4de780049
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266934"
---
# <a name="refactoring-using-a-pure-function-visual-basic"></a><span data-ttu-id="366f7-102">Refaktoring pomocí čisté funkce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="366f7-102">Refactoring Using a Pure Function (Visual Basic)</span></span>
<span data-ttu-id="366f7-103">Následující příklad refaktoruje předchozí příklad [Refaktoring Pomocí metody rozšíření (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-an-extension-method.md), chcete-li použít čistou funkci V tomto `ParagraphText`příkladu je kód pro nalezení textu odstavce přesunut na čistě statickou metodu .</span><span class="sxs-lookup"><span data-stu-id="366f7-103">The following example refactors the previous example, [Refactoring Using an Extension Method (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-an-extension-method.md), to use a pure function In this example, the code to find the text of a paragraph is moved to the pure static method `ParagraphText`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="366f7-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="366f7-104">Example</span></span>  
 <span data-ttu-id="366f7-105">Tento příklad zpracuje dokument WordprocessingML, načtení odstavcových uzlů z dokumentu WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="366f7-105">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="366f7-106">Také identifikuje styl každého odstavce.</span><span class="sxs-lookup"><span data-stu-id="366f7-106">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="366f7-107">Tento příklad vychází z předchozích příkladů v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="366f7-107">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="366f7-108">Refaktorovaný kód je volán v komentářích v níže uvedeném kódu.</span><span class="sxs-lookup"><span data-stu-id="366f7-108">The refactored code is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="366f7-109">Pokyny k vytvoření zdrojového dokumentu v tomto příkladu naleznete [v tématu Vytvoření dokumentu Open XML (Visual Basic) zdrojové sady Office](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="366f7-109">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="366f7-110">Tento příklad používá třídy z sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="366f7-110">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="366f7-111">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="366f7-111">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
Module Module1  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(ByVal source As IEnumerable(Of String)) As String  
        Dim sb = New StringBuilder()  
        For Each s In source  
            sb.Append(s)  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal func As Func(Of T, String)) As String  
        Dim sb = New StringBuilder()  
        For Each item As T In source  
            sb.Append(func(item))  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal separator As String) As String  
        Dim sb = New StringBuilder()  
        For Each s As T In source  
            sb.Append(s).Append(separator)  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal func As Func(Of T, String), ByVal separator As String) As String  
        Dim sb = New StringBuilder()  
        For Each item As T In source  
            sb.Append(func(item)).Append(separator)  
        Next  
        Return sb.ToString()  
    End Function  
  
    ' This is a new method that assembles the paragraph text.  
    Public Function ParagraphText(ByVal e As XElement) As String  
        Dim w = e.Name.Namespace  
        Return (e.<w:r>.<w:t>).StringConcatenate(Function(element) CStr(element))  
    End Function  
  
    ' Following function is required because Visual Basic does not support short circuit evaluation  
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, _  
                                         ByVal defaultStyle As String) As String  
        If styleNode Is Nothing Then  
            Return defaultStyle  
        Else  
            Return styleNode.@w:val  
        End If  
    End Function  
  
    Sub Main()  
        Dim fileName = "SampleDoc.docx"  
  
        Dim documentRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Dim stylesRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
        Dim wordmlNamespace = _  
          "http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = _  
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), _  
                  docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                '  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                '  Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = _  
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If styleRelation IsNot Nothing Then  
                    Dim styleUri As Uri = _  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)  
  
                    '  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
            End If  
        End Using  
  
        Dim defaultStyle = _  
            ( _  
                From style In styleDoc.Root.<w:style> _  
                Where style.@w:type = "paragraph" And _  
                      style.@w:default = "1" _  
                Select style _  
            ).First().@w:styleId  
  
        ' Find all paragraphs in the document.  
        Dim paragraphs = _  
            From para In xDoc.Root.<w:body>...<w:p> _  
        Let styleNode = para.<w:pPr>.<w:pStyle>.FirstOrDefault _  
        Select New With { _  
            .ParagraphNode = para, _  
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _  
        }  
  
        ' Retrieve the text of each paragraph.  
        Dim paraWithText = _  
            From para In paragraphs _  
            Select New With { _  
                .ParagraphNode = para.ParagraphNode, _  
                .StyleName = para.StyleName, _  
                .Text = ParagraphText(para.ParagraphNode) _  
            }  
  
        For Each p In paraWithText  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text)  
        Next  
    End Sub  
End Module
```  
  
 <span data-ttu-id="366f7-112">Tento příklad vytváří stejný výstup jako před refaktoring:</span><span class="sxs-lookup"><span data-stu-id="366f7-112">This example produces the same output as before the refactoring:</span></span>  
  
```console  
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<  
StyleName:Normal ><  
StyleName:Normal >The following example prints to the console.<  
StyleName:Normal ><  
StyleName:Code >Imports System<  
StyleName:Code ><  
StyleName:Code >Class Program<  
StyleName:Code >    Public Shared  Sub Main(ByVal args() As String)<  
StyleName:Code >        Console.WriteLine("Hello World")<  
StyleName:Code >   End Sub<  
StyleName:Code >End Class<  
StyleName:Normal ><  
StyleName:Normal >This example produces the following output:<  
StyleName:Normal ><  
StyleName:Code >Hello World<  
```  
  
### <a name="next-steps"></a><span data-ttu-id="366f7-113">Další kroky</span><span class="sxs-lookup"><span data-stu-id="366f7-113">Next Steps</span></span>  
 <span data-ttu-id="366f7-114">Následující příklad ukazuje, jak promítat XML do jiného tvaru:</span><span class="sxs-lookup"><span data-stu-id="366f7-114">The next example shows how to project XML into a different shape:</span></span>  
  
- [<span data-ttu-id="366f7-115">Promítání XML v jiném obrazci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="366f7-115">Projecting XML in a Different Shape (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projecting-xml-in-a-different-shape.md)  
  
## <a name="see-also"></a><span data-ttu-id="366f7-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="366f7-116">See also</span></span>

- [<span data-ttu-id="366f7-117">Kurz: Manipulace s obsahem v dokumentu WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="366f7-117">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [<span data-ttu-id="366f7-118">Refaktoring pomocí metody rozšíření (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="366f7-118">Refactoring Using an Extension Method (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)
- [<span data-ttu-id="366f7-119">Refaktoring do čistých funkcí (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="366f7-119">Refactoring Into Pure Functions (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md)
