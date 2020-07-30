---
title: Načítání odstavců a jejich stylů (C#)
description: Naučte se napsat dotaz, který načte odstavce a pak určí styl každého odstavce.
ms.date: 07/20/2015
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
ms.openlocfilehash: 94d01a13485f70bc9d9cef55b5f390c3b30d7f14
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303397"
---
# <a name="retrieving-the-paragraphs-and-their-styles-c"></a><span data-ttu-id="4e582-103">Načítání odstavců a jejich stylů (C#)</span><span class="sxs-lookup"><span data-stu-id="4e582-103">Retrieving the Paragraphs and Their Styles (C#)</span></span>
<span data-ttu-id="4e582-104">V tomto příkladu zapíšeme dotaz, který načte uzly odstavců z dokumentu WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="4e582-104">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="4e582-105">Určuje také styl každého odstavce.</span><span class="sxs-lookup"><span data-stu-id="4e582-105">It also identifies the style of each paragraph.</span></span>  
  
 <span data-ttu-id="4e582-106">Tento dotaz sestaví na dotazu v předchozím příkladu a hledá [výchozí styl odstavce (C#)](./finding-the-default-paragraph-style.md), který načte výchozí styl ze seznamu stylů.</span><span class="sxs-lookup"><span data-stu-id="4e582-106">This query builds on the query in the previous example, [Finding the Default Paragraph Style (C#)](./finding-the-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="4e582-107">Tyto informace jsou požadovány, aby dotaz mohl identifikovat styl odstavců, které nemají explicitně nastaven styl.</span><span class="sxs-lookup"><span data-stu-id="4e582-107">This information is required so that the query can identify the style of paragraphs that do not have a style explicitly set.</span></span> <span data-ttu-id="4e582-108">Odstavcové styly se nastavují prostřednictvím `w:pPr` elementu; Pokud odstavec tento prvek neobsahuje, naformátuje se s výchozím stylem.</span><span class="sxs-lookup"><span data-stu-id="4e582-108">Paragraph styles are set through the `w:pPr` element; if a paragraph does not contain this element, it is formatted with the default style.</span></span>  
  
 <span data-ttu-id="4e582-109">Toto téma vysvětluje význam některých částí dotazu a pak zobrazuje dotaz jako součást kompletního a funkčního příkladu.</span><span class="sxs-lookup"><span data-stu-id="4e582-109">This topic explains the significance of some pieces of the query, then shows the query as part of a complete, working example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e582-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="4e582-110">Example</span></span>  
 <span data-ttu-id="4e582-111">Zdroj dotazu pro načtení všech odstavců v dokumentu a jejich stylů je následující:</span><span class="sxs-lookup"><span data-stu-id="4e582-111">The source of the query to retrieve all the paragraphs in a document and their styles is as follows:</span></span>  
  
```csharp  
xDoc.Root.Element(w + "body").Descendants(w + "p")  
```  
  
 <span data-ttu-id="4e582-112">Tento výraz je podobný zdroji dotazu v předchozím příkladu, který [najde výchozí styl odstavce (C#)](./finding-the-default-paragraph-style.md).</span><span class="sxs-lookup"><span data-stu-id="4e582-112">This expression is similar to the source of the query in the previous example, [Finding the Default Paragraph Style (C#)](./finding-the-default-paragraph-style.md).</span></span> <span data-ttu-id="4e582-113">Hlavní rozdíl spočívá v tom, že <xref:System.Xml.Linq.XContainer.Descendants%2A> místo osy používá osu <xref:System.Xml.Linq.XContainer.Elements%2A> .</span><span class="sxs-lookup"><span data-stu-id="4e582-113">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="4e582-114">Dotaz používá osu, <xref:System.Xml.Linq.XContainer.Descendants%2A> protože v dokumentech, které mají oddíly, nebudou odstavce přímo podřízeny elementu těla. místo toho budou v hierarchii tyto odstavce dvě.</span><span class="sxs-lookup"><span data-stu-id="4e582-114">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs will not be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="4e582-115">Pomocí <xref:System.Xml.Linq.XContainer.Descendants%2A> osy bude kód pracovat na tom, zda dokument používá oddíly.</span><span class="sxs-lookup"><span data-stu-id="4e582-115">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work of whether or not the document uses sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e582-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="4e582-116">Example</span></span>  
 <span data-ttu-id="4e582-117">Dotaz používá `let` klauzuli k určení prvku, který obsahuje uzel Style.</span><span class="sxs-lookup"><span data-stu-id="4e582-117">The query uses a `let` clause to determine the element that contains the style node.</span></span> <span data-ttu-id="4e582-118">Pokud není žádný element, pak `styleNode` je nastaven na `null` :</span><span class="sxs-lookup"><span data-stu-id="4e582-118">If there is no element, then `styleNode` is set to `null`:</span></span>  
  
```csharp  
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()  
```  
  
 <span data-ttu-id="4e582-119">`let`Klauzule nejprve používá <xref:System.Xml.Linq.XContainer.Elements%2A> osu k vyhledání všech prvků s názvem `pPr` a poté používá <xref:System.Xml.Linq.Extensions.Elements%2A> metodu rozšíření k vyhledání všech podřízených elementů s názvem `pStyle` a nakonec používá <xref:System.Linq.Enumerable.FirstOrDefault%2A> standardní operátor dotazu k převedení kolekce na typ singleton.</span><span class="sxs-lookup"><span data-stu-id="4e582-119">The `let` clause first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="4e582-120">Je-li kolekce prázdná, `styleNode` je nastavena na hodnotu `null` .</span><span class="sxs-lookup"><span data-stu-id="4e582-120">If the collection is empty, `styleNode` is set to `null`.</span></span> <span data-ttu-id="4e582-121">Toto je užitečná idiom pro vyhledání `pStyle` podřízeného uzlu.</span><span class="sxs-lookup"><span data-stu-id="4e582-121">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="4e582-122">Všimněte si, že pokud `pPr` neexistuje podřízený uzel, kód selže ani selže vyvoláním výjimky; namísto toho `styleNode` je nastavena na `null` , což je požadované chování této `let` klauzule.</span><span class="sxs-lookup"><span data-stu-id="4e582-122">Note that if the `pPr` child node does not exist, the code does nor fail by throwing an exception; instead, `styleNode` is set to `null`, which is the desired behavior of this `let` clause.</span></span>  
  
 <span data-ttu-id="4e582-123">Dotaz projektuje kolekci anonymního typu se dvěma členy `StyleName` a `ParagraphNode` .</span><span class="sxs-lookup"><span data-stu-id="4e582-123">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e582-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="4e582-124">Example</span></span>  
 <span data-ttu-id="4e582-125">Tento příklad zpracovává dokument WordprocessingML a načítá uzly odstavců z dokumentu WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="4e582-125">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="4e582-126">Určuje také styl každého odstavce.</span><span class="sxs-lookup"><span data-stu-id="4e582-126">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="4e582-127">Tento příklad sestaví na předchozích příkladech v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="4e582-127">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="4e582-128">Nový dotaz se zavolá v komentářích v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="4e582-128">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="4e582-129">Pokyny pro vytvoření zdrojového dokumentu pro tento příklad najdete v [tématu vytvoření zdrojového dokumentu XML pro Office (C#)](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="4e582-129">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="4e582-130">Tento příklad používá třídy nalezené v sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="4e582-130">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="4e582-131">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4e582-131">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="4e582-132">Tento příklad vytvoří následující výstup při použití v dokumentu popsaném v [tématu vytvoření zdrojového dokumentu XML pro Office (C#)](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="4e582-132">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
```output  
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
  
## <a name="next-steps"></a><span data-ttu-id="4e582-133">Další kroky</span><span class="sxs-lookup"><span data-stu-id="4e582-133">Next Steps</span></span>  
 <span data-ttu-id="4e582-134">V dalším tématu [načtení textu odstavců (C#)](./retrieving-the-text-of-the-paragraphs.md)vytvoříte dotaz pro načtení textu odstavců.</span><span class="sxs-lookup"><span data-stu-id="4e582-134">In the next topic, [Retrieving the Text of the Paragraphs (C#)](./retrieving-the-text-of-the-paragraphs.md), you'll create a query to retrieve the text of paragraphs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e582-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4e582-135">See also</span></span>

- [<span data-ttu-id="4e582-136">Kurz: manipulace s obsahem v dokumentu WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="4e582-136">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
