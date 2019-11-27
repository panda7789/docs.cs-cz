---
title: Načtení textu odstavců
ms.date: 07/20/2015
ms.assetid: 095fa0d9-7b1b-4cbb-9c13-e2c9d8923d31
ms.openlocfilehash: 596a6548f45d82c7ae260f9b010d2f139eb1c1fa
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347518"
---
# <a name="retrieving-the-text-of-the-paragraphs-visual-basic"></a><span data-ttu-id="4ec15-102">Načtení textu odstavců (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ec15-102">Retrieving the Text of the Paragraphs (Visual Basic)</span></span>
<span data-ttu-id="4ec15-103">Tento příklad sestaví v předchozím příkladu [a načte odstavce a jejich styly (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md).</span><span class="sxs-lookup"><span data-stu-id="4ec15-103">This example builds on the previous example, [Retrieving the Paragraphs and Their Styles (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md).</span></span> <span data-ttu-id="4ec15-104">Tento nový příklad načte text každého odstavce jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="4ec15-104">This new example retrieves the text of each paragraph as a string.</span></span>  
  
 <span data-ttu-id="4ec15-105">Chcete-li načíst text, tento příklad přidá další dotaz, který prochází kolekcí anonymních typů a projekty nové kolekce anonymního typu s přidáním nového člena, `Text`.</span><span class="sxs-lookup"><span data-stu-id="4ec15-105">To retrieve the text, this example adds an additional query that iterates through the collection of anonymous types and projects a new collection of an anonymous type with the addition of a new member, `Text`.</span></span> <span data-ttu-id="4ec15-106">Používá operátor dotazu <xref:System.Linq.Enumerable.Aggregate%2A> Standard k zřetězení více řetězců do jednoho řetězce.</span><span class="sxs-lookup"><span data-stu-id="4ec15-106">It uses the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span>  
  
 <span data-ttu-id="4ec15-107">Tato technika (to znamená, že nejprve procházíte do kolekce anonymního typu a pak tuto kolekci použijete pro projekt k nové kolekci anonymního typu) je běžné a užitečné idiom.</span><span class="sxs-lookup"><span data-stu-id="4ec15-107">This technique (that is, first projecting to a collection of an anonymous type, then using this collection to project to a new collection of an anonymous type) is a common and useful idiom.</span></span> <span data-ttu-id="4ec15-108">Tento dotaz může být zapsaný bez projekce prvního anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="4ec15-108">This query could have been written without projecting to the first anonymous type.</span></span> <span data-ttu-id="4ec15-109">Z důvodu opožděného vyhodnocení ale nevyužívá mnohem další výpočetní výkon.</span><span class="sxs-lookup"><span data-stu-id="4ec15-109">However, because of lazy evaluation, doing so does not use much additional processing power.</span></span> <span data-ttu-id="4ec15-110">Idiom vytváří v haldě krátkodobé objekty pro zpracování, ale v podstatě nesnižuje výkon.</span><span class="sxs-lookup"><span data-stu-id="4ec15-110">The idiom creates more short lived objects on the heap, but this does not substantially degrade performance.</span></span>  
  
 <span data-ttu-id="4ec15-111">Samozřejmě by bylo možné napsat jeden dotaz, který obsahuje funkce pro načtení odstavců, styl každého odstavce a text každého odstavce.</span><span class="sxs-lookup"><span data-stu-id="4ec15-111">Of course, it would be possible to write a single query that contains the functionality to retrieve the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="4ec15-112">Často je však užitečné rozdělit složitější dotaz do několika dotazů, protože výsledný kód je více modulární a snazší pro údržbu.</span><span class="sxs-lookup"><span data-stu-id="4ec15-112">However, it often is useful to break up a more complicated query into multiple queries because the resulting code is more modular and easier to maintain.</span></span> <span data-ttu-id="4ec15-113">Kromě toho, pokud potřebujete znovu použít část dotazu, je snazší Refaktorovat, pokud jsou dotazy zapisovány tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="4ec15-113">Furthermore, if you need to reuse a portion of the query, it is easier to refactor if the queries are written in this manner.</span></span>  
  
 <span data-ttu-id="4ec15-114">Tyto dotazy, které jsou zřetězeny společně, používají model zpracování, který je podrobně prověřen v tématu [kurz: odložené spuštění (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md).</span><span class="sxs-lookup"><span data-stu-id="4ec15-114">These queries, which are chained together, use the processing model that is examined in detail in the topic [Tutorial: Deferred Execution (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ec15-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="4ec15-115">Example</span></span>  
 <span data-ttu-id="4ec15-116">Tento příklad zpracovává dokument WordprocessingML, určuje uzel elementu, název stylu a text každého odstavce.</span><span class="sxs-lookup"><span data-stu-id="4ec15-116">This example processes a WordprocessingML document, determining the element node, the style name, and the text of each paragraph.</span></span> <span data-ttu-id="4ec15-117">Tento příklad sestaví na předchozích příkladech v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="4ec15-117">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="4ec15-118">Nový dotaz se zavolá v komentářích v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="4ec15-118">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="4ec15-119">Pokyny k vytvoření zdrojového dokumentu pro tento příklad najdete v tématu [vytvoření zdrojového dokumentu XML pro Office Open (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="4ec15-119">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="4ec15-120">Tento příklad používá třídy ze sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="4ec15-120">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="4ec15-121">Používá typy v oboru názvů <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4ec15-121">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="4ec15-122">Tento příklad vytvoří následující výstup při použití v dokumentu popsaném v [tématu vytvoření zdrojového dokumentu XML pro Office Open (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="4ec15-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
## <a name="next-steps"></a><span data-ttu-id="4ec15-123">Další kroky</span><span class="sxs-lookup"><span data-stu-id="4ec15-123">Next Steps</span></span>  
 <span data-ttu-id="4ec15-124">Další příklad ukazuje, jak použít rozšiřující metodu namísto <xref:System.Linq.Enumerable.Aggregate%2A>, k zřetězení více řetězců do jednoho řetězce.</span><span class="sxs-lookup"><span data-stu-id="4ec15-124">The next example shows how to use an extension method, instead of <xref:System.Linq.Enumerable.Aggregate%2A>, to concatenate multiple strings into a single string.</span></span>  
  
- [<span data-ttu-id="4ec15-125">Refaktoring pomocí metody rozšíření (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ec15-125">Refactoring Using an Extension Method (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="4ec15-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ec15-126">See also</span></span>

- [<span data-ttu-id="4ec15-127">Kurz: manipulace s obsahem v dokumentu WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ec15-127">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [<span data-ttu-id="4ec15-128">Odložené provádění a opožděné vyhodnocení v LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ec15-128">Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
