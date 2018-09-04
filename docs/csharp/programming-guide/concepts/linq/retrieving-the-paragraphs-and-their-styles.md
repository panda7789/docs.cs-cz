---
title: Načtení odstavců a jejich stylů (C#)
ms.date: 07/20/2015
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
ms.openlocfilehash: 46ffc13c9808b6186efa402bd46b75c6c1a9bbda
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510771"
---
# <a name="retrieving-the-paragraphs-and-their-styles-c"></a><span data-ttu-id="3dc09-102">Načtení odstavců a jejich stylů (C#)</span><span class="sxs-lookup"><span data-stu-id="3dc09-102">Retrieving the Paragraphs and Their Styles (C#)</span></span>
<span data-ttu-id="3dc09-103">V tomto příkladu jsme vytvořit dotaz, který načte uzly odstavců z dokumentu WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="3dc09-103">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="3dc09-104">Styl k jednotlivým odstavcům také identifikuje.</span><span class="sxs-lookup"><span data-stu-id="3dc09-104">It also identifies the style of each paragraph.</span></span>  
  
 <span data-ttu-id="3dc09-105">Tento dotaz je založena na dotazu v předchozím příkladu [vyhledání výchozího stylu odstavce (C#)](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), který načte výchozí styl seznamu styly.</span><span class="sxs-lookup"><span data-stu-id="3dc09-105">This query builds on the query in the previous example, [Finding the Default Paragraph Style (C#)](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="3dc09-106">Tyto informace jsou nezbytné, aby dotaz můžete identifikovat styl odstavce, které nemají explicitně nastavit styl.</span><span class="sxs-lookup"><span data-stu-id="3dc09-106">This information is required so that the query can identify the style of paragraphs that do not have a style explicitly set.</span></span> <span data-ttu-id="3dc09-107">Styly odstavci, se konfigurují pomocí `w:pPr` element; Pokud odstavce neobsahuje tohoto prvku, je naformátována pomocí výchozího stylu.</span><span class="sxs-lookup"><span data-stu-id="3dc09-107">Paragraph styles are set through the `w:pPr` element; if a paragraph does not contain this element, it is formatted with the default style.</span></span>  
  
 <span data-ttu-id="3dc09-108">Toto téma vysvětluje význam některé části dotazu a potom se zobrazí dotaz jako součást kompletní, funkční příklad.</span><span class="sxs-lookup"><span data-stu-id="3dc09-108">This topic explains the significance of some pieces of the query, then shows the query as part of a complete, working example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3dc09-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="3dc09-109">Example</span></span>  
 <span data-ttu-id="3dc09-110">Zdrojový dotaz pro načtení všech odstavce v dokumentu a jejich stylů vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="3dc09-110">The source of the query to retrieve all the paragraphs in a document and their styles is as follows:</span></span>  
  
```csharp  
xDoc.Root.Element(w + "body").Descendants(w + "p")  
```  
  
 <span data-ttu-id="3dc09-111">Tento výraz je podobný zdroje dotazu v předchozím příkladu [hledání výchozí styl odstavce (C#)](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md).</span><span class="sxs-lookup"><span data-stu-id="3dc09-111">This expression is similar to the source of the query in the previous example, [Finding the Default Paragraph Style (C#)](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md).</span></span> <span data-ttu-id="3dc09-112">Hlavním rozdílem je, že používá <xref:System.Xml.Linq.XContainer.Descendants%2A> osy místo <xref:System.Xml.Linq.XContainer.Elements%2A> osy.</span><span class="sxs-lookup"><span data-stu-id="3dc09-112">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="3dc09-113">Použije dotaz <xref:System.Xml.Linq.XContainer.Descendants%2A> osy vzhledem k tomu, že v dokumentech, které mají oddíly, odstavců nebudou přímé podřízené objekty daného elementu těla; místo toho odstavců bude dvě úrovně dolů v hierarchii.</span><span class="sxs-lookup"><span data-stu-id="3dc09-113">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs will not be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="3dc09-114">S použitím <xref:System.Xml.Linq.XContainer.Descendants%2A> osy, kód bude fungovat z Určuje, jestli dokument používá oddíly.</span><span class="sxs-lookup"><span data-stu-id="3dc09-114">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work of whether or not the document uses sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3dc09-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="3dc09-115">Example</span></span>  
 <span data-ttu-id="3dc09-116">Použije dotaz `let` klauzule určit element, který obsahuje uzel stylu.</span><span class="sxs-lookup"><span data-stu-id="3dc09-116">The query uses a `let` clause to determine the element that contains the style node.</span></span> <span data-ttu-id="3dc09-117">Pokud neexistuje žádný element, pak `styleNode` je nastavena na `null`:</span><span class="sxs-lookup"><span data-stu-id="3dc09-117">If there is no element, then `styleNode` is set to `null`:</span></span>  
  
```csharp  
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()  
```  
  
 <span data-ttu-id="3dc09-118">`let` Nejdřív pomocí klauzule <xref:System.Xml.Linq.XContainer.Elements%2A> osy k vyhledání všech elementů s názvem `pPr`, použije <xref:System.Xml.Linq.Extensions.Elements%2A> metodu rozšíření k vyhledání všech podřízených elementů s názvem `pStyle`a nakonec používá <xref:System.Linq.Enumerable.FirstOrDefault%2A> standardního dotazu operátor pro převod kolekce na jednotlivý prvek.</span><span class="sxs-lookup"><span data-stu-id="3dc09-118">The `let` clause first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="3dc09-119">Pokud kolekce je prázdná, `styleNode` je nastavena na `null`.</span><span class="sxs-lookup"><span data-stu-id="3dc09-119">If the collection is empty, `styleNode` is set to `null`.</span></span> <span data-ttu-id="3dc09-120">To je užitečné idiom Hledat `pStyle` uzel potomka.</span><span class="sxs-lookup"><span data-stu-id="3dc09-120">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="3dc09-121">Všimněte si, že pokud `pPr` podřízený uzel se buď neexistuje, kód neodpovídá ani selhání vyvoláním výjimky; místo toho `styleNode` je nastavena na `null`, což je požadované chování tohoto `let` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="3dc09-121">Note that if the `pPr` child node does not exist, the code does nor fail by throwing an exception; instead, `styleNode` is set to `null`, which is the desired behavior of this `let` clause.</span></span>  
  
 <span data-ttu-id="3dc09-122">Dotaz projekty kolekce anonymního typu se dvěma členy `StyleName` a `ParagraphNode`.</span><span class="sxs-lookup"><span data-stu-id="3dc09-122">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3dc09-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="3dc09-123">Example</span></span>  
 <span data-ttu-id="3dc09-124">V tomto příkladu zpracovává dokumentu WordprocessingML načítání uzly odstavců z dokumentu WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="3dc09-124">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="3dc09-125">Styl k jednotlivým odstavcům také identifikuje.</span><span class="sxs-lookup"><span data-stu-id="3dc09-125">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="3dc09-126">Tento příklad je založen na předchozí příklady v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="3dc09-126">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="3dc09-127">Nový dotaz je uvedeny v komentářích v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="3dc09-127">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="3dc09-128">Můžete najít pokyny pro vytvoření zdrojového dokumentu v tomto příkladu v [vytváření zdroj Office Open XML dokumentu (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="3dc09-128">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="3dc09-129">Tento příklad používá třídy v sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="3dc09-129">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="3dc09-130">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3dc09-130">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
const string fileName = "SampleDoc.docx";  
  
const string documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";  
const string wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
XDocument xDoc = null;  
XDocument styleDoc = null;  
  
using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))  
{  
    PackageRelationship docPackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();  
    if (docPackageRelationship != null)  
    {  
        Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative), docPackageRelationship.TargetUri);  
        PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
        //  Load the document XML in the part into an XDocument instance.  
        xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
        //  Find the styles part. There will only be one.  
        PackageRelationship styleRelation = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
        if (styleRelation != null)  
        {  
            Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
            PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
            //  Load the style XML in the part into an XDocument instance.  
            styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
        }  
    }  
}  
  
string defaultStyle =   
    (string)(  
        from style in styleDoc.Root.Elements(w + "style")  
        where (string)style.Attribute(w + "type") == "paragraph"&&  
              (string)style.Attribute(w + "default") == "1"  
              select style  
    ).First().Attribute(w + "styleId");  
  
// Following is the new query that finds all paragraphs in the  
// document and their styles.  
var paragraphs =  
    from para in xDoc  
                 .Root  
                 .Element(w + "body")  
                 .Descendants(w + "p")  
    let styleNode = para  
                    .Elements(w + "pPr")  
                    .Elements(w + "pStyle")  
                    .FirstOrDefault()  
    select new  
    {  
        ParagraphNode = para,  
        StyleName = styleNode != null ?  
            (string)styleNode.Attribute(w + "val") :  
            defaultStyle  
    };  
  
foreach (var p in paragraphs)  
    Console.WriteLine("StyleName:{0}", p.StyleName);  
```  
  
 <span data-ttu-id="3dc09-131">Tento příklad vytvoří následující výstup při použití u dokumentu je popsáno v [vytváření zdroj Office Open XML dokumentu (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="3dc09-131">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
## <a name="next-steps"></a><span data-ttu-id="3dc09-132">Další kroky</span><span class="sxs-lookup"><span data-stu-id="3dc09-132">Next Steps</span></span>  
 <span data-ttu-id="3dc09-133">V dalším tématu [načtení textu odstavců (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), vytvoříte dotaz pro načtení textu odstavců.</span><span class="sxs-lookup"><span data-stu-id="3dc09-133">In the next topic, [Retrieving the Text of the Paragraphs (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), you'll create a query to retrieve the text of paragraphs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dc09-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="3dc09-134">See Also</span></span>

- [<span data-ttu-id="3dc09-135">Kurz: Manipulace s obsahem v dokumentu WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="3dc09-135">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
