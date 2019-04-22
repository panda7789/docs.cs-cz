---
title: 'Postupy: Načtení odstavců z dokumentu Office Open XML (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 66053f21-9217-473c-a6f3-a0897be07756
ms.openlocfilehash: 325f0d981c4988379938385fbfff5d36d0f5bff8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58828573"
---
# <a name="how-to-retrieve-paragraphs-from-an-office-open-xml-document-visual-basic"></a><span data-ttu-id="db4ab-102">Postupy: Načtení odstavců z dokumentu Office Open XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db4ab-102">How to: Retrieve Paragraphs from an Office Open XML Document (Visual Basic)</span></span>
<span data-ttu-id="db4ab-103">Toto téma představuje příklad, který otevře dokumentu Office Open XML a načte kolekci všech odstavce v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="db4ab-103">This topic presents an example that opens an Office Open XML document, and retrieves a collection of all of the paragraphs in the document.</span></span>  
  
 <span data-ttu-id="db4ab-104">Další informace o Office Open XML naleznete v tématu [Eric prázdné blogu](http://www.ericwhite.com).</span><span class="sxs-lookup"><span data-stu-id="db4ab-104">For more information on Office Open XML, see [Eric White's Blog](http://www.ericwhite.com).</span></span>  
  
## <a name="example"></a><span data-ttu-id="db4ab-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="db4ab-105">Example</span></span>  
 <span data-ttu-id="db4ab-106">Tento příklad otevře balíček Office Open XML, používá k nalezení dokumentů a částí styl vztahy v rámci balíčku Open XML.</span><span class="sxs-lookup"><span data-stu-id="db4ab-106">This example opens an Office Open XML package, uses the relationships within the Open XML package to find the document and the style parts.</span></span> <span data-ttu-id="db4ab-107">Následně se dotazuje dokumentu projekci kolekce anonymního typu, který obsahuje odstavce <xref:System.Xml.Linq.XElement> uzlu, název stylu k jednotlivým odstavcům a každý odstavec.</span><span class="sxs-lookup"><span data-stu-id="db4ab-107">It then queries the document, projecting a collection of an anonymous type that contains the paragraph <xref:System.Xml.Linq.XElement> node, the style name of each paragraph, and the text of each paragraph.</span></span>  
  
 <span data-ttu-id="db4ab-108">Tento příklad používá metodu rozšíření s názvem `StringConcatenate`, který je rovněž dodán v příkladu.</span><span class="sxs-lookup"><span data-stu-id="db4ab-108">The example uses an extension method named `StringConcatenate`, which is also supplied in the example.</span></span>  
  
 <span data-ttu-id="db4ab-109">Podrobný kurz vysvětluje, jak tento příklad funguje, najdete v tématu [čistě funkční transformace XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span><span class="sxs-lookup"><span data-stu-id="db4ab-109">For a detailed tutorial that explains how this example works, see [Pure Functional Transformations of XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span></span>  
  
 <span data-ttu-id="db4ab-110">Tento příklad používá třídy v sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="db4ab-110">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="db4ab-111">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="db4ab-111">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(ByVal source As IEnumerable(Of String)) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each s As String In source  
            sb.Append(s)  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal func As Func(Of T, String)) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each item As T In source  
            sb.Append(func(item))  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal separator As String) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each s As T In source  
            sb.Append(s).Append(separator)  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal func As Func(Of T, String), ByVal separator As String) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each item As T In source  
            sb.Append(func(item)).Append(separator)  
        Next  
        Return sb.ToString()  
    End Function  
  
    Public Function ParagraphText(ByVal e As XElement) As String  
        Dim w As XNamespace = e.Name.Namespace  
        Return (e.<w:r>.<w:t>).StringConcatenate(Function(element) CStr(element))  
    End Function  
  
    ' Following function is required because VB does not support short circuit evaluation  
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, ByVal defaultStyle As String) _  
                As String  
        If (styleNode Is Nothing) Then  
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
              wdPackage _  
              .GetRelationshipsByType(documentRelationshipType) _  
              .FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = _  
                  PackUriHelper _  
                  .ResolvePartUri(New Uri("/", UriKind.Relative), docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                '  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                '  Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If (styleRelation IsNot Nothing) Then  
                    Dim styleUri As Uri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)  
  
                    '  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
            End If  
        End Using  
  
        Dim defaultStyle As String = _  
            ( _  
                From style In styleDoc.Root.<w:style> _  
                Where style.@w:type = "paragraph" And _  
                      style.@w:default = "1" _  
                Select style _  
            ).First().@w:styleId  
  
        ' Find all paragraphs in the document.  
        Dim paragraphs = _  
            From para In xDoc.Root.<w:body>...<w:p> _  
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault _  
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
  
 <span data-ttu-id="db4ab-112">Při spuštění s ukázkový dokument Open XML je popsáno v [vytváření zdroj Office otevřít dokument XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md), tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="db4ab-112">When run with the sample Open XML document described in [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md), this example produces the following output:</span></span>  
  
```  
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<  
StyleName:Normal ><  
StyleName:Normal >The following example prints to the console.<  
StyleName:Normal ><  
StyleName:Code >using System;<  
StyleName:Code ><  
StyleName:Code >class Program {<  
StyleName:Code >    public static void (string[] args) {<  
StyleName:Code >        Console.WriteLine("Hello World");<  
StyleName:Code >    }<  
StyleName:Code >}<  
StyleName:Normal ><  
StyleName:Normal >This example produces the following output:<  
StyleName:Normal ><  
StyleName:Code >Hello World<  
```  
  
## <a name="see-also"></a><span data-ttu-id="db4ab-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db4ab-113">See also</span></span>

- [<span data-ttu-id="db4ab-114">Pokročilé techniky dotazování (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db4ab-114">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
