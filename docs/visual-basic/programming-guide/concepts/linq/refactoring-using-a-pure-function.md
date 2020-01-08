---
title: Refaktoring pomocí čisté funkce
ms.date: 07/20/2015
ms.assetid: af0ea62f-4f57-4868-b624-a85524055935
ms.openlocfilehash: ce07622a030f291bbbee54dc342562ffecd3258c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341660"
---
# <a name="refactoring-using-a-pure-function-visual-basic"></a><span data-ttu-id="3543a-102">Refaktoring pomocí funkce Pure (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3543a-102">Refactoring Using a Pure Function (Visual Basic)</span></span>
<span data-ttu-id="3543a-103">Následující příklad [refaktoruje předchozí příklad refaktoringu pomocí metody rozšíření (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)pro použití funkce Pure v tomto příkladu, kód pro nalezení textu odstavce je přesunut do metody pure static `ParagraphText`.</span><span class="sxs-lookup"><span data-stu-id="3543a-103">The following example refactors the previous example, [Refactoring Using an Extension Method (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-an-extension-method.md), to use a pure function In this example, the code to find the text of a paragraph is moved to the pure static method `ParagraphText`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3543a-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="3543a-104">Example</span></span>  
 <span data-ttu-id="3543a-105">Tento příklad zpracovává dokument WordprocessingML a načítá uzly odstavců z dokumentu WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="3543a-105">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="3543a-106">Určuje také styl každého odstavce.</span><span class="sxs-lookup"><span data-stu-id="3543a-106">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="3543a-107">Tento příklad sestaví na předchozích příkladech v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="3543a-107">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="3543a-108">Refaktoring Code se volá v komentářích v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="3543a-108">The refactored code is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="3543a-109">Pokyny k vytvoření zdrojového dokumentu pro tento příklad najdete v tématu [vytvoření zdrojového dokumentu XML pro Office Open (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="3543a-109">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="3543a-110">Tento příklad používá třídy ze sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="3543a-110">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="3543a-111">Používá typy v oboru názvů <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3543a-111">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="3543a-112">Tento příklad vytvoří stejný výstup jako před refaktoringem:</span><span class="sxs-lookup"><span data-stu-id="3543a-112">This example produces the same output as before the refactoring:</span></span>  
  
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
  
### <a name="next-steps"></a><span data-ttu-id="3543a-113">Další kroky</span><span class="sxs-lookup"><span data-stu-id="3543a-113">Next Steps</span></span>  
 <span data-ttu-id="3543a-114">Následující příklad ukazuje, jak projekt XML do jiného tvaru:</span><span class="sxs-lookup"><span data-stu-id="3543a-114">The next example shows how to project XML into a different shape:</span></span>  
  
- [<span data-ttu-id="3543a-115">Projektování XML v jiném obrazci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3543a-115">Projecting XML in a Different Shape (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projecting-xml-in-a-different-shape.md)  
  
## <a name="see-also"></a><span data-ttu-id="3543a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3543a-116">See also</span></span>

- [<span data-ttu-id="3543a-117">Kurz: manipulace s obsahem v dokumentu WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3543a-117">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [<span data-ttu-id="3543a-118">Refaktoring pomocí metody rozšíření (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3543a-118">Refactoring Using an Extension Method (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)
- [<span data-ttu-id="3543a-119">Refaktoring na čistě funkce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3543a-119">Refactoring Into Pure Functions (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md)
