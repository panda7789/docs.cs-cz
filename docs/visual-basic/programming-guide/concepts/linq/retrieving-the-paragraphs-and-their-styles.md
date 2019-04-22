---
title: Načtení odstavců a jejich stylů (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d9ed2238-d38e-4ad4-b88b-db7859df9bde
ms.openlocfilehash: 3c6554c44c95db13aada0d9edf96cc2df595c6d1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816938"
---
# <a name="retrieving-the-paragraphs-and-their-styles-visual-basic"></a><span data-ttu-id="bcc85-102">Načtení odstavců a jejich stylů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bcc85-102">Retrieving the Paragraphs and Their Styles (Visual Basic)</span></span>
<span data-ttu-id="bcc85-103">V tomto příkladu jsme vytvořit dotaz, který načte uzly odstavců z dokumentu WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="bcc85-103">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="bcc85-104">Styl k jednotlivým odstavcům také identifikuje.</span><span class="sxs-lookup"><span data-stu-id="bcc85-104">It also identifies the style of each paragraph.</span></span>  
  
 <span data-ttu-id="bcc85-105">Tento dotaz je založena na dotazu v předchozím příkladu [vyhledání výchozího stylu odstavce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), který načte výchozí styl seznamu styly.</span><span class="sxs-lookup"><span data-stu-id="bcc85-105">This query builds on the query in the previous example, [Finding the Default Paragraph Style (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="bcc85-106">Tyto informace jsou nezbytné, aby dotaz můžete identifikovat styl odstavce, které nemají explicitně nastavit styl.</span><span class="sxs-lookup"><span data-stu-id="bcc85-106">This information is required so that the query can identify the style of paragraphs that do not have a style explicitly set.</span></span> <span data-ttu-id="bcc85-107">Styly odstavci, se konfigurují pomocí `w:pPr` element; Pokud odstavce neobsahuje tohoto prvku, je naformátována pomocí výchozího stylu.</span><span class="sxs-lookup"><span data-stu-id="bcc85-107">Paragraph styles are set through the `w:pPr` element; if a paragraph does not contain this element, it is formatted with the default style.</span></span>  
  
 <span data-ttu-id="bcc85-108">Toto téma vysvětluje význam některé části dotazu a potom se zobrazí dotaz jako součást kompletní, funkční příklad.</span><span class="sxs-lookup"><span data-stu-id="bcc85-108">This topic explains the significance of some pieces of the query, then shows the query as part of a complete, working example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcc85-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="bcc85-109">Example</span></span>  
 <span data-ttu-id="bcc85-110">Zdrojový dotaz pro načtení všech odstavce v dokumentu a jejich stylů vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="bcc85-110">The source of the query to retrieve all the paragraphs in a document and their styles is as follows:</span></span>  
  
```vb  
xDoc.Root.<w:body>...<w:p>  
```  
  
 <span data-ttu-id="bcc85-111">Tento výraz je podobný zdroje dotazu v předchozím příkladu [hledání (Visual Basic) výchozí styl odstavce](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md).</span><span class="sxs-lookup"><span data-stu-id="bcc85-111">This expression is similar to the source of the query in the previous example, [Finding the Default Paragraph Style (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md).</span></span> <span data-ttu-id="bcc85-112">Hlavním rozdílem je, že používá <xref:System.Xml.Linq.XContainer.Descendants%2A> osy místo <xref:System.Xml.Linq.XContainer.Elements%2A> osy.</span><span class="sxs-lookup"><span data-stu-id="bcc85-112">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="bcc85-113">Použije dotaz <xref:System.Xml.Linq.XContainer.Descendants%2A> osy vzhledem k tomu, že v dokumentech, které mají oddíly, odstavců nebudou přímé podřízené objekty daného elementu těla; místo toho odstavců bude dvě úrovně dolů v hierarchii.</span><span class="sxs-lookup"><span data-stu-id="bcc85-113">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs will not be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="bcc85-114">S použitím <xref:System.Xml.Linq.XContainer.Descendants%2A> osy, kód bude fungovat z Určuje, jestli dokument používá oddíly.</span><span class="sxs-lookup"><span data-stu-id="bcc85-114">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work of whether or not the document uses sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcc85-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="bcc85-115">Example</span></span>  
 <span data-ttu-id="bcc85-116">Použije dotaz `Let` klauzule určit element, který obsahuje uzel stylu.</span><span class="sxs-lookup"><span data-stu-id="bcc85-116">The query uses a `Let` clause to determine the element that contains the style node.</span></span> <span data-ttu-id="bcc85-117">Pokud neexistuje žádný element, pak `styleNode` je nastavena na `Nothing`:</span><span class="sxs-lookup"><span data-stu-id="bcc85-117">If there is no element, then `styleNode` is set to `Nothing`:</span></span>  
  
```vb  
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()  
```  
  
 <span data-ttu-id="bcc85-118">`Let` Nejdřív pomocí klauzule <xref:System.Xml.Linq.XContainer.Elements%2A> osy k vyhledání všech elementů s názvem `pPr`, použije <xref:System.Xml.Linq.Extensions.Elements%2A> metodu rozšíření k vyhledání všech podřízených elementů s názvem `pStyle`a nakonec používá <xref:System.Linq.Enumerable.FirstOrDefault%2A> standardního dotazu operátor pro převod kolekce na jednotlivý prvek.</span><span class="sxs-lookup"><span data-stu-id="bcc85-118">The `Let` clause first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="bcc85-119">Pokud kolekce je prázdná, `styleNode` je nastavena na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="bcc85-119">If the collection is empty, `styleNode` is set to `Nothing`.</span></span> <span data-ttu-id="bcc85-120">To je užitečné idiom Hledat `pStyle` uzel potomka.</span><span class="sxs-lookup"><span data-stu-id="bcc85-120">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="bcc85-121">Všimněte si, že pokud `pPr` podřízený uzel se buď neexistuje, kód neodpovídá ani selhání vyvoláním výjimky; místo toho `styleNode` je nastavena na `Nothing`, což je požadované chování tohoto `Let` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="bcc85-121">Note that if the `pPr` child node does not exist, the code does nor fail by throwing an exception; instead, `styleNode` is set to `Nothing`, which is the desired behavior of this `Let` clause.</span></span>  
  
 <span data-ttu-id="bcc85-122">Dotaz projekty kolekce anonymního typu se dvěma členy `StyleName` a `ParagraphNode`.</span><span class="sxs-lookup"><span data-stu-id="bcc85-122">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcc85-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="bcc85-123">Example</span></span>  
 <span data-ttu-id="bcc85-124">V tomto příkladu zpracovává dokumentu WordprocessingML načítání uzly odstavců z dokumentu WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="bcc85-124">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="bcc85-125">Styl k jednotlivým odstavcům také identifikuje.</span><span class="sxs-lookup"><span data-stu-id="bcc85-125">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="bcc85-126">Tento příklad je založen na předchozí příklady v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="bcc85-126">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="bcc85-127">Nový dotaz je uvedeny v komentářích v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="bcc85-127">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="bcc85-128">Můžete najít pokyny pro vytvoření zdrojového dokumentu v tomto příkladu v [vytváření zdroj Office otevřít dokument XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="bcc85-128">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="bcc85-129">Tento příklad používá třídy v sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="bcc85-129">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="bcc85-130">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="bcc85-130">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="bcc85-131">Tento příklad vytvoří následující výstup při použití u dokumentu je popsáno v [vytváření zdroj Office otevřít dokument XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="bcc85-131">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
## <a name="next-steps"></a><span data-ttu-id="bcc85-132">Další kroky</span><span class="sxs-lookup"><span data-stu-id="bcc85-132">Next Steps</span></span>  
 <span data-ttu-id="bcc85-133">V dalším tématu [načtení textu odstavců (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), vytvoříte dotaz pro načtení textu odstavců.</span><span class="sxs-lookup"><span data-stu-id="bcc85-133">In the next topic, [Retrieving the Text of the Paragraphs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), you'll create a query to retrieve the text of paragraphs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcc85-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bcc85-134">See also</span></span>

- [<span data-ttu-id="bcc85-135">Kurz: Manipulace s obsahem v dokumentu WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bcc85-135">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
