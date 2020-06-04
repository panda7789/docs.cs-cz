---
title: Načtení odstavců a jejich stylů
ms.date: 07/20/2015
ms.assetid: d9ed2238-d38e-4ad4-b88b-db7859df9bde
ms.openlocfilehash: ad904abf9bd94e83b981859662c22787652e294f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413402"
---
# <a name="retrieving-the-paragraphs-and-their-styles-visual-basic"></a><span data-ttu-id="53489-102">Načítání odstavců a jejich stylů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53489-102">Retrieving the Paragraphs and Their Styles (Visual Basic)</span></span>
<span data-ttu-id="53489-103">V tomto příkladu zapíšeme dotaz, který načte uzly odstavců z dokumentu WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="53489-103">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="53489-104">Určuje také styl každého odstavce.</span><span class="sxs-lookup"><span data-stu-id="53489-104">It also identifies the style of each paragraph.</span></span>  
  
 <span data-ttu-id="53489-105">Tento dotaz sestaví na dotazu v předchozím příkladu a hledá [výchozí styl odstavce (Visual Basic)](finding-the-default-paragraph-style.md), který načte výchozí styl ze seznamu stylů.</span><span class="sxs-lookup"><span data-stu-id="53489-105">This query builds on the query in the previous example, [Finding the Default Paragraph Style (Visual Basic)](finding-the-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="53489-106">Tyto informace jsou požadovány, aby dotaz mohl identifikovat styl odstavců, které nemají explicitně nastaven styl.</span><span class="sxs-lookup"><span data-stu-id="53489-106">This information is required so that the query can identify the style of paragraphs that do not have a style explicitly set.</span></span> <span data-ttu-id="53489-107">Odstavcové styly se nastavují prostřednictvím `w:pPr` elementu; Pokud odstavec tento prvek neobsahuje, naformátuje se s výchozím stylem.</span><span class="sxs-lookup"><span data-stu-id="53489-107">Paragraph styles are set through the `w:pPr` element; if a paragraph does not contain this element, it is formatted with the default style.</span></span>  
  
 <span data-ttu-id="53489-108">Toto téma vysvětluje význam některých částí dotazu a pak zobrazuje dotaz jako součást kompletního a funkčního příkladu.</span><span class="sxs-lookup"><span data-stu-id="53489-108">This topic explains the significance of some pieces of the query, then shows the query as part of a complete, working example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53489-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="53489-109">Example</span></span>  
 <span data-ttu-id="53489-110">Zdroj dotazu pro načtení všech odstavců v dokumentu a jejich stylů je následující:</span><span class="sxs-lookup"><span data-stu-id="53489-110">The source of the query to retrieve all the paragraphs in a document and their styles is as follows:</span></span>  
  
```vb  
xDoc.Root.<w:body>...<w:p>  
```  
  
 <span data-ttu-id="53489-111">Tento výraz je podobný zdroji dotazu v předchozím příkladu, kde je [nalezen výchozí styl odstavce (Visual Basic)](finding-the-default-paragraph-style.md).</span><span class="sxs-lookup"><span data-stu-id="53489-111">This expression is similar to the source of the query in the previous example, [Finding the Default Paragraph Style (Visual Basic)](finding-the-default-paragraph-style.md).</span></span> <span data-ttu-id="53489-112">Hlavní rozdíl spočívá v tom, že <xref:System.Xml.Linq.XContainer.Descendants%2A> místo osy používá osu <xref:System.Xml.Linq.XContainer.Elements%2A> .</span><span class="sxs-lookup"><span data-stu-id="53489-112">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="53489-113">Dotaz používá osu, <xref:System.Xml.Linq.XContainer.Descendants%2A> protože v dokumentech, které mají oddíly, nebudou odstavce přímo podřízeny elementu těla. místo toho budou v hierarchii tyto odstavce dvě.</span><span class="sxs-lookup"><span data-stu-id="53489-113">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs will not be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="53489-114">Pomocí <xref:System.Xml.Linq.XContainer.Descendants%2A> osy bude kód pracovat na tom, zda dokument používá oddíly.</span><span class="sxs-lookup"><span data-stu-id="53489-114">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work of whether or not the document uses sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53489-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="53489-115">Example</span></span>  
 <span data-ttu-id="53489-116">Dotaz používá `Let` klauzuli k určení prvku, který obsahuje uzel Style.</span><span class="sxs-lookup"><span data-stu-id="53489-116">The query uses a `Let` clause to determine the element that contains the style node.</span></span> <span data-ttu-id="53489-117">Pokud není žádný element, pak `styleNode` je nastaven na `Nothing` :</span><span class="sxs-lookup"><span data-stu-id="53489-117">If there is no element, then `styleNode` is set to `Nothing`:</span></span>  
  
```vb  
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()  
```  
  
 <span data-ttu-id="53489-118">`Let`Klauzule nejprve používá <xref:System.Xml.Linq.XContainer.Elements%2A> osu k vyhledání všech prvků s názvem `pPr` a poté používá <xref:System.Xml.Linq.Extensions.Elements%2A> metodu rozšíření k vyhledání všech podřízených elementů s názvem `pStyle` a nakonec používá <xref:System.Linq.Enumerable.FirstOrDefault%2A> standardní operátor dotazu k převedení kolekce na typ singleton.</span><span class="sxs-lookup"><span data-stu-id="53489-118">The `Let` clause first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="53489-119">Je-li kolekce prázdná, `styleNode` je nastavena na hodnotu `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="53489-119">If the collection is empty, `styleNode` is set to `Nothing`.</span></span> <span data-ttu-id="53489-120">Toto je užitečná idiom pro vyhledání `pStyle` podřízeného uzlu.</span><span class="sxs-lookup"><span data-stu-id="53489-120">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="53489-121">Všimněte si, že pokud `pPr` neexistuje podřízený uzel, kód selže ani selže vyvoláním výjimky; namísto toho `styleNode` je nastavena na `Nothing` , což je požadované chování této `Let` klauzule.</span><span class="sxs-lookup"><span data-stu-id="53489-121">Note that if the `pPr` child node does not exist, the code does nor fail by throwing an exception; instead, `styleNode` is set to `Nothing`, which is the desired behavior of this `Let` clause.</span></span>  
  
 <span data-ttu-id="53489-122">Dotaz projektuje kolekci anonymního typu se dvěma členy `StyleName` a `ParagraphNode` .</span><span class="sxs-lookup"><span data-stu-id="53489-122">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53489-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="53489-123">Example</span></span>  
 <span data-ttu-id="53489-124">Tento příklad zpracovává dokument WordprocessingML a načítá uzly odstavců z dokumentu WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="53489-124">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="53489-125">Určuje také styl každého odstavce.</span><span class="sxs-lookup"><span data-stu-id="53489-125">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="53489-126">Tento příklad sestaví na předchozích příkladech v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="53489-126">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="53489-127">Nový dotaz se zavolá v komentářích v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="53489-127">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="53489-128">Pokyny pro vytvoření zdrojového dokumentu pro tento příklad najdete v [tématu vytvoření zdrojového dokumentu XML pro Office Open (Visual Basic)](creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="53489-128">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (Visual Basic)](creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="53489-129">Tento příklad používá třídy nalezené v sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="53489-129">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="53489-130">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="53489-130">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="53489-131">Tento příklad vytvoří následující výstup při použití v dokumentu popsaném v [tématu vytvoření zdrojového dokumentu XML pro Office Open (Visual Basic)](creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="53489-131">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (Visual Basic)](creating-the-source-office-open-xml-document.md).</span></span>  
  
```console  
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
  
## <a name="next-steps"></a><span data-ttu-id="53489-132">Další kroky</span><span class="sxs-lookup"><span data-stu-id="53489-132">Next Steps</span></span>  
 <span data-ttu-id="53489-133">V dalším tématu [načtení textu odstavců (Visual Basic)](retrieving-the-text-of-the-paragraphs.md)vytvoříte dotaz pro načtení textu odstavců.</span><span class="sxs-lookup"><span data-stu-id="53489-133">In the next topic, [Retrieving the Text of the Paragraphs (Visual Basic)](retrieving-the-text-of-the-paragraphs.md), you'll create a query to retrieve the text of paragraphs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53489-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="53489-134">See also</span></span>

- [<span data-ttu-id="53489-135">Kurz: manipulace s obsahem v dokumentu WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53489-135">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](tutorial-manipulating-content-in-a-wordprocessingml-document.md)
