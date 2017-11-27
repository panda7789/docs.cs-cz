---
title: "Načítání odstavců a jejich styly (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d7619ede02e9a384ddceec23a232a53de1dad0aa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="retrieving-the-paragraphs-and-their-styles-c"></a><span data-ttu-id="bde89-102">Načítání odstavců a jejich styly (C#)</span><span class="sxs-lookup"><span data-stu-id="bde89-102">Retrieving the Paragraphs and Their Styles (C#)</span></span>
<span data-ttu-id="bde89-103">V tomto příkladu jsme vytvořit dotaz, který načte odstavce uzly z WordprocessingML dokumentu.</span><span class="sxs-lookup"><span data-stu-id="bde89-103">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="bde89-104">Také identifikuje styl jednotlivých odstavců.</span><span class="sxs-lookup"><span data-stu-id="bde89-104">It also identifies the style of each paragraph.</span></span>  
  
 <span data-ttu-id="bde89-105">Tento dotaz založený na dotaz v předchozím příkladu [hledání výchozí styl odstavce (C#)](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), který načte výchozí styl ze seznamu stylů.</span><span class="sxs-lookup"><span data-stu-id="bde89-105">This query builds on the query in the previous example, [Finding the Default Paragraph Style (C#)](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="bde89-106">Tyto informace jsou nezbytné, aby dotaz můžete identifikovat styl odstavců, které nemají styl explicitně nastaven.</span><span class="sxs-lookup"><span data-stu-id="bde89-106">This information is required so that the query can identify the style of paragraphs that do not have a style explicitly set.</span></span> <span data-ttu-id="bde89-107">Styly odstavce, se konfigurují pomocí `w:pPr` element; Pokud odstavec neobsahuje tento prvek, je formátován pomocí výchozí styl.</span><span class="sxs-lookup"><span data-stu-id="bde89-107">Paragraph styles are set through the `w:pPr` element; if a paragraph does not contain this element, it is formatted with the default style.</span></span>  
  
 <span data-ttu-id="bde89-108">Toto téma vysvětluje význam některé jeho součásti dotazu a potom jako součást dokončení práce příklad ukazuje dotaz.</span><span class="sxs-lookup"><span data-stu-id="bde89-108">This topic explains the significance of some pieces of the query, then shows the query as part of a complete, working example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bde89-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="bde89-109">Example</span></span>  
 <span data-ttu-id="bde89-110">Zdroj dotaz pro načtení všech odstavců v dokumentu a jejich styly vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="bde89-110">The source of the query to retrieve all the paragraphs in a document and their styles is as follows:</span></span>  
  
```csharp  
xDoc.Root.Element(w + "body").Descendants(w + "p")  
```  
  
 <span data-ttu-id="bde89-111">Tento výraz je podobná zdroj dotazu v předchozím příkladu [hledání výchozí styl odstavce (C#)](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md).</span><span class="sxs-lookup"><span data-stu-id="bde89-111">This expression is similar to the source of the query in the previous example, [Finding the Default Paragraph Style (C#)](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md).</span></span> <span data-ttu-id="bde89-112">Hlavní rozdíl je, že používá <xref:System.Xml.Linq.XContainer.Descendants%2A> osy místo <xref:System.Xml.Linq.XContainer.Elements%2A> osy.</span><span class="sxs-lookup"><span data-stu-id="bde89-112">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="bde89-113">Dotaz používá <xref:System.Xml.Linq.XContainer.Descendants%2A> osy protože v dokumentech, které mají oddíly, odstavců nebude přímé podřízené objekty daného elementu body; místo toho odstavců bude dvě úrovně dolů v hierarchii.</span><span class="sxs-lookup"><span data-stu-id="bde89-113">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs will not be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="bde89-114">Pomocí <xref:System.Xml.Linq.XContainer.Descendants%2A> osy, bude kód pracovat z zda dokument používá oddíly.</span><span class="sxs-lookup"><span data-stu-id="bde89-114">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work of whether or not the document uses sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bde89-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="bde89-115">Example</span></span>  
 <span data-ttu-id="bde89-116">Dotaz používá `let` klauzule k určení elementu, který obsahuje uzel stylu.</span><span class="sxs-lookup"><span data-stu-id="bde89-116">The query uses a `let` clause to determine the element that contains the style node.</span></span> <span data-ttu-id="bde89-117">Pokud neexistuje žádný element pak `styleNode` je nastaven na `null`:</span><span class="sxs-lookup"><span data-stu-id="bde89-117">If there is no element, then `styleNode` is set to `null`:</span></span>  
  
```csharp  
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()  
```  
  
 <span data-ttu-id="bde89-118">`let` Nejdřív pomocí klauzule <xref:System.Xml.Linq.XContainer.Elements%2A> osy k vyhledání všech elementů s názvem `pPr`, použije <xref:System.Xml.Linq.Extensions.Elements%2A> rozšíření metody k vyhledání všech podřízených elementů s názvem `pStyle`a nakonec používá <xref:System.Linq.Enumerable.FirstOrDefault%2A> standardní dotazu operátor převést kolekci typu singleton.</span><span class="sxs-lookup"><span data-stu-id="bde89-118">The `let` clause first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="bde89-119">Pokud je kolekce prázdná, `styleNode` je nastaven na `null`.</span><span class="sxs-lookup"><span data-stu-id="bde89-119">If the collection is empty, `styleNode` is set to `null`.</span></span> <span data-ttu-id="bde89-120">To je užitečné, stylu a Hledat `pStyle` podřízený uzel.</span><span class="sxs-lookup"><span data-stu-id="bde89-120">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="bde89-121">Všimněte si, že pokud `pPr` podřízený uzel neexistuje, kód nemá ani selhání došlo k výjimce; místo toho `styleNode` je nastaven na `null`, což je toto chování žádoucí tohoto `let` klauzule.</span><span class="sxs-lookup"><span data-stu-id="bde89-121">Note that if the `pPr` child node does not exist, the code does nor fail by throwing an exception; instead, `styleNode` is set to `null`, which is the desired behavior of this `let` clause.</span></span>  
  
 <span data-ttu-id="bde89-122">Dotaz projekty kolekce anonymní typ s dva členy `StyleName` a `ParagraphNode`.</span><span class="sxs-lookup"><span data-stu-id="bde89-122">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bde89-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="bde89-123">Example</span></span>  
 <span data-ttu-id="bde89-124">Tento příklad zpracuje WordprocessingML dokumentu, načítání odstavce uzly z WordprocessingML dokumentu.</span><span class="sxs-lookup"><span data-stu-id="bde89-124">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="bde89-125">Také identifikuje styl jednotlivých odstavců.</span><span class="sxs-lookup"><span data-stu-id="bde89-125">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="bde89-126">Tento příklad vychází v předchozích příkladech v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="bde89-126">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="bde89-127">Nový dotaz se nazývá v komentáře v kódu níže.</span><span class="sxs-lookup"><span data-stu-id="bde89-127">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="bde89-128">Pokyny pro vytvoření zdrojový dokument v tomto příkladu můžete najít [vytváření zdroj Office otevřít dokument XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="bde89-128">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="bde89-129">Tento příklad používá třídy v sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="bde89-129">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="bde89-130">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="bde89-130">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="bde89-131">Tento příklad vytvoří následující výstup v případě použitého pro dokument popsané v [vytváření zdroj Office otevřít dokument XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="bde89-131">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
## <a name="next-steps"></a><span data-ttu-id="bde89-132">Další kroky</span><span class="sxs-lookup"><span data-stu-id="bde89-132">Next Steps</span></span>  
 <span data-ttu-id="bde89-133">V dalším tématu [načítání textu odstavců (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), vytvoříte dotaz pro načtení textu odstavce.</span><span class="sxs-lookup"><span data-stu-id="bde89-133">In the next topic, [Retrieving the Text of the Paragraphs (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), you'll create a query to retrieve the text of paragraphs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bde89-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="bde89-134">See Also</span></span>  
 [<span data-ttu-id="bde89-135">Kurz: Manipulace se obsah v dokumentu WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="bde89-135">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
