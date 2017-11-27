---
title: "Načítání textu odstavců (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 095fa0d9-7b1b-4cbb-9c13-e2c9d8923d31
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 492fc0dffd007f0ccdb7454c62e86cac753ca06b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="retrieving-the-text-of-the-paragraphs-visual-basic"></a><span data-ttu-id="ec5e2-102">Načítání textu odstavců (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec5e2-102">Retrieving the Text of the Paragraphs (Visual Basic)</span></span>
<span data-ttu-id="ec5e2-103">Tento příklad vychází na předchozí příklad, [načítání odstavců a jejich styly (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md).</span><span class="sxs-lookup"><span data-stu-id="ec5e2-103">This example builds on the previous example, [Retrieving the Paragraphs and Their Styles (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md).</span></span> <span data-ttu-id="ec5e2-104">Tento nový příklad načte text jednotlivých odstavců jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="ec5e2-104">This new example retrieves the text of each paragraph as a string.</span></span>  
  
 <span data-ttu-id="ec5e2-105">K získání textu, v tomto příkladu přidá další dotaz, který iteruje kolekcí anonymní typy a projekty novou kolekci anonymní typ s přidání nového člena, `Text`.</span><span class="sxs-lookup"><span data-stu-id="ec5e2-105">To retrieve the text, this example adds an additional query that iterates through the collection of anonymous types and projects a new collection of an anonymous type with the addition of a new member, `Text`.</span></span> <span data-ttu-id="ec5e2-106">Použije <xref:System.Linq.Enumerable.Aggregate%2A> operátor standardní dotazu k řetězení více řetězců do jednoho řetězce.</span><span class="sxs-lookup"><span data-stu-id="ec5e2-106">It uses the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span>  
  
 <span data-ttu-id="ec5e2-107">Tento postup (tedy první promítnutí do kolekce anonymního typu a potom pomocí této kolekce do projektu do nové kolekce anonymního typu) je běžné a užitečné stylu.</span><span class="sxs-lookup"><span data-stu-id="ec5e2-107">This technique (that is, first projecting to a collection of an anonymous type, then using this collection to project to a new collection of an anonymous type) is a common and useful idiom.</span></span> <span data-ttu-id="ec5e2-108">Tento dotaz může byla zapsána bez na první anonymní typ projekce.</span><span class="sxs-lookup"><span data-stu-id="ec5e2-108">This query could have been written without projecting to the first anonymous type.</span></span> <span data-ttu-id="ec5e2-109">Ale kvůli opožděné vyhodnocení to tak nepoužívá mnoho dalších výpočetní výkon.</span><span class="sxs-lookup"><span data-stu-id="ec5e2-109">However, because of lazy evaluation, doing so does not use much additional processing power.</span></span> <span data-ttu-id="ec5e2-110">Stylu vytváří více krátké povahy objektů v haldě, ale to nesnižuje podstatně výkon.</span><span class="sxs-lookup"><span data-stu-id="ec5e2-110">The idiom creates more short lived objects on the heap, but this does not substantially degrade performance.</span></span>  
  
 <span data-ttu-id="ec5e2-111">Samozřejmě by bylo možné vytvořit jeden dotaz, který obsahuje funkci pro načtení odstavců, styl jednotlivých odstavců a každý odstavec.</span><span class="sxs-lookup"><span data-stu-id="ec5e2-111">Of course, it would be possible to write a single query that contains the functionality to retrieve the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="ec5e2-112">Ale často je užitečné rozdělit složitější dotaz do více dotazů, protože výsledný kód je více modulární a jednodušší správu.</span><span class="sxs-lookup"><span data-stu-id="ec5e2-112">However, it often is useful to break up a more complicated query into multiple queries because the resulting code is more modular and easier to maintain.</span></span> <span data-ttu-id="ec5e2-113">Kromě toho pokud potřebujete znovu použít část dotazu, aby bylo jednodušší refactor Pokud dotazy jsou zapsány tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="ec5e2-113">Furthermore, if you need to reuse a portion of the query, it is easier to refactor if the queries are written in this manner.</span></span>  
  
 <span data-ttu-id="ec5e2-114">Tyto dotazy, které jsou zřetězené společně, použijte zpracování modelu, který je podrobně v tématu [kurz: odložený provádění (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md).</span><span class="sxs-lookup"><span data-stu-id="ec5e2-114">These queries, which are chained together, use the processing model that is examined in detail in the topic [Tutorial: Deferred Execution (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec5e2-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="ec5e2-115">Example</span></span>  
 <span data-ttu-id="ec5e2-116">Tento příklad zpracuje WordprocessingML dokumentu, určení uzlu elementu, název stylu a každý odstavec.</span><span class="sxs-lookup"><span data-stu-id="ec5e2-116">This example processes a WordprocessingML document, determining the element node, the style name, and the text of each paragraph.</span></span> <span data-ttu-id="ec5e2-117">Tento příklad vychází v předchozích příkladech v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="ec5e2-117">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="ec5e2-118">Nový dotaz se nazývá v komentáře v kódu níže.</span><span class="sxs-lookup"><span data-stu-id="ec5e2-118">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="ec5e2-119">Pokyny pro vytvoření zdrojový dokument v tomto příkladu najdete v tématu [vytváření zdroj Office otevřít dokument XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="ec5e2-119">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="ec5e2-120">Tento příklad používá třídy z WindowsBase sestavení.</span><span class="sxs-lookup"><span data-stu-id="ec5e2-120">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="ec5e2-121">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ec5e2-121">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    ' Following function is required because VB does not support short circuit evaluation  
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, _  
                                         ByVal defaultStyle As String) As String  
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
                If (styleRelation IsNot Nothing) Then  
                    Dim styleUri As Uri = _  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
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
  
        ' Following is the new query that retrieves the text of  
        ' each paragraph.  
        Dim paraWithText = _  
            From para In paragraphs _  
            Select New With { _  
                .ParagraphNode = para.ParagraphNode, _  
                .StyleName = para.StyleName, _  
                .Text = para.ParagraphNode.<w:r>.<w:t> _  
                    .Aggregate(New StringBuilder(), _  
                               Function(s As StringBuilder, i As String) s.Append(CStr(i)), _  
                               Function(s As StringBuilder) s.ToString) _  
            }  
  
        For Each p In paraWithText  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text)  
        Next  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="ec5e2-122">Tento příklad vytvoří následující výstup v případě použitého pro dokument popsané v [vytváření zdroj Office otevřít dokument XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="ec5e2-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
```  
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
  
## <a name="next-steps"></a><span data-ttu-id="ec5e2-123">Další kroky</span><span class="sxs-lookup"><span data-stu-id="ec5e2-123">Next Steps</span></span>  
 <span data-ttu-id="ec5e2-124">Další příklad ukazuje, jak používat metody rozšíření, místo <xref:System.Linq.Enumerable.Aggregate%2A>, aby řetězení více řetězců do jednoho řetězce.</span><span class="sxs-lookup"><span data-stu-id="ec5e2-124">The next example shows how to use an extension method, instead of <xref:System.Linq.Enumerable.Aggregate%2A>, to concatenate multiple strings into a single string.</span></span>  
  
-   [<span data-ttu-id="ec5e2-125">Refaktoring pomocí metody rozšíření (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec5e2-125">Refactoring Using an Extension Method (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="ec5e2-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec5e2-126">See Also</span></span>  
 [<span data-ttu-id="ec5e2-127">Kurz: Manipulace se obsah v dokumentu WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec5e2-127">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)  
 [<span data-ttu-id="ec5e2-128">Odložené provedení a opožděné vyhodnocení v technologii LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec5e2-128">Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
