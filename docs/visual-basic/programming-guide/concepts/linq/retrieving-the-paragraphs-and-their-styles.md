---
title: Načítání odstavců a jejich styly (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d9ed2238-d38e-4ad4-b88b-db7859df9bde
ms.openlocfilehash: 5b8075b5aa05c32d2dc894149a8fa53f103138c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648304"
---
# <a name="retrieving-the-paragraphs-and-their-styles-visual-basic"></a><span data-ttu-id="f8515-102">Načítání odstavců a jejich styly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8515-102">Retrieving the Paragraphs and Their Styles (Visual Basic)</span></span>
<span data-ttu-id="f8515-103">V tomto příkladu jsme vytvořit dotaz, který načte odstavce uzly z WordprocessingML dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f8515-103">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="f8515-104">Také identifikuje styl jednotlivých odstavců.</span><span class="sxs-lookup"><span data-stu-id="f8515-104">It also identifies the style of each paragraph.</span></span>  
  
 <span data-ttu-id="f8515-105">Tento dotaz založený na dotaz v předchozím příkladu [hledání výchozí styl odstavce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), který načte výchozí styl ze seznamu stylů.</span><span class="sxs-lookup"><span data-stu-id="f8515-105">This query builds on the query in the previous example, [Finding the Default Paragraph Style (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="f8515-106">Tyto informace jsou nezbytné, aby dotaz můžete identifikovat styl odstavců, které nemají styl explicitně nastaven.</span><span class="sxs-lookup"><span data-stu-id="f8515-106">This information is required so that the query can identify the style of paragraphs that do not have a style explicitly set.</span></span> <span data-ttu-id="f8515-107">Styly odstavce, se konfigurují pomocí `w:pPr` element; Pokud odstavec neobsahuje tento prvek, je formátován pomocí výchozí styl.</span><span class="sxs-lookup"><span data-stu-id="f8515-107">Paragraph styles are set through the `w:pPr` element; if a paragraph does not contain this element, it is formatted with the default style.</span></span>  
  
 <span data-ttu-id="f8515-108">Toto téma vysvětluje význam některé jeho součásti dotazu a potom jako součást dokončení práce příklad ukazuje dotaz.</span><span class="sxs-lookup"><span data-stu-id="f8515-108">This topic explains the significance of some pieces of the query, then shows the query as part of a complete, working example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8515-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8515-109">Example</span></span>  
 <span data-ttu-id="f8515-110">Zdroj dotaz pro načtení všech odstavců v dokumentu a jejich styly vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="f8515-110">The source of the query to retrieve all the paragraphs in a document and their styles is as follows:</span></span>  
  
```vb  
xDoc.Root.<w:body>...<w:p>  
```  
  
 <span data-ttu-id="f8515-111">Tento výraz je podobná zdroj dotazu v předchozím příkladu [hledání styl odstavce výchozí (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md).</span><span class="sxs-lookup"><span data-stu-id="f8515-111">This expression is similar to the source of the query in the previous example, [Finding the Default Paragraph Style (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md).</span></span> <span data-ttu-id="f8515-112">Hlavní rozdíl je, že používá <xref:System.Xml.Linq.XContainer.Descendants%2A> osy místo <xref:System.Xml.Linq.XContainer.Elements%2A> osy.</span><span class="sxs-lookup"><span data-stu-id="f8515-112">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="f8515-113">Dotaz používá <xref:System.Xml.Linq.XContainer.Descendants%2A> osy protože v dokumentech, které mají oddíly, odstavců nebude přímé podřízené objekty daného elementu body; místo toho odstavců bude dvě úrovně dolů v hierarchii.</span><span class="sxs-lookup"><span data-stu-id="f8515-113">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs will not be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="f8515-114">Pomocí <xref:System.Xml.Linq.XContainer.Descendants%2A> osy, bude kód pracovat z zda dokument používá oddíly.</span><span class="sxs-lookup"><span data-stu-id="f8515-114">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work of whether or not the document uses sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8515-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8515-115">Example</span></span>  
 <span data-ttu-id="f8515-116">Dotaz používá `Let` klauzule k určení elementu, který obsahuje uzel stylu.</span><span class="sxs-lookup"><span data-stu-id="f8515-116">The query uses a `Let` clause to determine the element that contains the style node.</span></span> <span data-ttu-id="f8515-117">Pokud neexistuje žádný element pak `styleNode` je nastaven na `Nothing`:</span><span class="sxs-lookup"><span data-stu-id="f8515-117">If there is no element, then `styleNode` is set to `Nothing`:</span></span>  
  
```vb  
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()  
```  
  
 <span data-ttu-id="f8515-118">`Let` Nejdřív pomocí klauzule <xref:System.Xml.Linq.XContainer.Elements%2A> osy k vyhledání všech elementů s názvem `pPr`, použije <xref:System.Xml.Linq.Extensions.Elements%2A> rozšíření metody k vyhledání všech podřízených elementů s názvem `pStyle`a nakonec používá <xref:System.Linq.Enumerable.FirstOrDefault%2A> standardní dotazu operátor převést kolekci typu singleton.</span><span class="sxs-lookup"><span data-stu-id="f8515-118">The `Let` clause first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="f8515-119">Pokud je kolekce prázdná, `styleNode` je nastaven na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="f8515-119">If the collection is empty, `styleNode` is set to `Nothing`.</span></span> <span data-ttu-id="f8515-120">To je užitečné, stylu a Hledat `pStyle` podřízený uzel.</span><span class="sxs-lookup"><span data-stu-id="f8515-120">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="f8515-121">Všimněte si, že pokud `pPr` podřízený uzel neexistuje, kód nemá ani selhání došlo k výjimce; místo toho `styleNode` je nastaven na `Nothing`, což je toto chování žádoucí tohoto `Let` klauzule.</span><span class="sxs-lookup"><span data-stu-id="f8515-121">Note that if the `pPr` child node does not exist, the code does nor fail by throwing an exception; instead, `styleNode` is set to `Nothing`, which is the desired behavior of this `Let` clause.</span></span>  
  
 <span data-ttu-id="f8515-122">Dotaz projekty kolekce anonymní typ s dva členy `StyleName` a `ParagraphNode`.</span><span class="sxs-lookup"><span data-stu-id="f8515-122">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8515-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8515-123">Example</span></span>  
 <span data-ttu-id="f8515-124">Tento příklad zpracuje WordprocessingML dokumentu, načítání odstavce uzly z WordprocessingML dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f8515-124">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="f8515-125">Také identifikuje styl jednotlivých odstavců.</span><span class="sxs-lookup"><span data-stu-id="f8515-125">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="f8515-126">Tento příklad vychází v předchozích příkladech v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="f8515-126">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="f8515-127">Nový dotaz se nazývá v komentáře v kódu níže.</span><span class="sxs-lookup"><span data-stu-id="f8515-127">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="f8515-128">Pokyny pro vytvoření zdrojový dokument v tomto příkladu můžete najít [vytváření zdroj Office otevřít dokument XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="f8515-128">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="f8515-129">Tento příklad používá třídy v sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="f8515-129">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="f8515-130">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f8515-130">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, ByVal defaultStyle As String) As String  
        If (styleNode Is Nothing) Then  
            Return defaultStyle  
        Else  
            Return styleNode.@w:val  
        End If  
    End Function  
  
    Sub Main()  
        Dim fileName = "SampleDoc.docx"  
  
        Dim documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Dim stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
        Dim wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), docPackageRelationship.TargetUri)  
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
  
        ' Following is the new query that finds all paragraphs in the  
        ' document and their styles.  
        Dim paragraphs = _  
            From para In xDoc.Root.<w:body>...<w:p> _  
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault() _  
        Select New With { _  
            .ParagraphNode = para, _  
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _  
        }  
  
        For Each p In paragraphs  
            Console.WriteLine("StyleName:{0}", p.StyleName)  
        Next  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="f8515-131">Tento příklad vytvoří následující výstup v případě použitého pro dokument popsané v [vytváření zdroj Office otevřít dokument XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="f8515-131">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
```  
StyleName:Heading1  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
```  
  
## <a name="next-steps"></a><span data-ttu-id="f8515-132">Další kroky</span><span class="sxs-lookup"><span data-stu-id="f8515-132">Next Steps</span></span>  
 <span data-ttu-id="f8515-133">V dalším tématu [načítání textu odstavců (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), vytvoříte dotaz pro načtení textu odstavce.</span><span class="sxs-lookup"><span data-stu-id="f8515-133">In the next topic, [Retrieving the Text of the Paragraphs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), you'll create a query to retrieve the text of paragraphs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8515-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="f8515-134">See Also</span></span>  
 [<span data-ttu-id="f8515-135">Kurz: Manipulace se obsah v dokumentu WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8515-135">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
