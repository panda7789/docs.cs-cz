---
title: Načítání odstavců a jejich stylů (C#)
ms.date: 07/20/2015
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
ms.openlocfilehash: ec59ef0ac36f8691ca93a4c21c5379118ee0491f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253063"
---
# <a name="retrieving-the-paragraphs-and-their-styles-c"></a><span data-ttu-id="d7426-102">Načítání odstavců a jejich stylů (C#)</span><span class="sxs-lookup"><span data-stu-id="d7426-102">Retrieving the Paragraphs and Their Styles (C#)</span></span>
<span data-ttu-id="d7426-103">V tomto příkladu zapíšeme dotaz, který načte uzly odstavců z dokumentu WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="d7426-103">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="d7426-104">Určuje také styl každého odstavce.</span><span class="sxs-lookup"><span data-stu-id="d7426-104">It also identifies the style of each paragraph.</span></span>  
  
 <span data-ttu-id="d7426-105">Tento dotaz sestaví na dotazu v předchozím příkladu a hledá [výchozí styl odstavce (C#)](./finding-the-default-paragraph-style.md), který načte výchozí styl ze seznamu stylů.</span><span class="sxs-lookup"><span data-stu-id="d7426-105">This query builds on the query in the previous example, [Finding the Default Paragraph Style (C#)](./finding-the-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="d7426-106">Tyto informace jsou požadovány, aby dotaz mohl identifikovat styl odstavců, které nemají explicitně nastaven styl.</span><span class="sxs-lookup"><span data-stu-id="d7426-106">This information is required so that the query can identify the style of paragraphs that do not have a style explicitly set.</span></span> <span data-ttu-id="d7426-107">Odstavcové styly se nastavují `w:pPr` prostřednictvím elementu; Pokud odstavec tento prvek neobsahuje, naformátuje se s výchozím stylem.</span><span class="sxs-lookup"><span data-stu-id="d7426-107">Paragraph styles are set through the `w:pPr` element; if a paragraph does not contain this element, it is formatted with the default style.</span></span>  
  
 <span data-ttu-id="d7426-108">Toto téma vysvětluje význam některých částí dotazu a pak zobrazuje dotaz jako součást kompletního a funkčního příkladu.</span><span class="sxs-lookup"><span data-stu-id="d7426-108">This topic explains the significance of some pieces of the query, then shows the query as part of a complete, working example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7426-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="d7426-109">Example</span></span>  
 <span data-ttu-id="d7426-110">Zdroj dotazu pro načtení všech odstavců v dokumentu a jejich stylů je následující:</span><span class="sxs-lookup"><span data-stu-id="d7426-110">The source of the query to retrieve all the paragraphs in a document and their styles is as follows:</span></span>  
  
```csharp  
xDoc.Root.Element(w + "body").Descendants(w + "p")  
```  
  
 <span data-ttu-id="d7426-111">Tento výraz je podobný zdroji dotazu v předchozím příkladu, kde [hledání výchozího stylu odstavceC#()](./finding-the-default-paragraph-style.md).</span><span class="sxs-lookup"><span data-stu-id="d7426-111">This expression is similar to the source of the query in the previous example, [Finding the Default Paragraph Style (C#)](./finding-the-default-paragraph-style.md).</span></span> <span data-ttu-id="d7426-112">Hlavní rozdíl spočívá v tom, že místo <xref:System.Xml.Linq.XContainer.Descendants%2A> <xref:System.Xml.Linq.XContainer.Elements%2A> osy používá osu.</span><span class="sxs-lookup"><span data-stu-id="d7426-112">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="d7426-113">Dotaz používá <xref:System.Xml.Linq.XContainer.Descendants%2A> osu, protože v dokumentech, které mají oddíly, nebudou odstavce přímo podřízeny elementu těla. místo toho budou v hierarchii tyto odstavce dvě.</span><span class="sxs-lookup"><span data-stu-id="d7426-113">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs will not be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="d7426-114">Pomocí <xref:System.Xml.Linq.XContainer.Descendants%2A> osy bude kód pracovat na tom, zda dokument používá oddíly.</span><span class="sxs-lookup"><span data-stu-id="d7426-114">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work of whether or not the document uses sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7426-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="d7426-115">Example</span></span>  
 <span data-ttu-id="d7426-116">Dotaz používá `let` klauzuli k určení prvku, který obsahuje uzel Style.</span><span class="sxs-lookup"><span data-stu-id="d7426-116">The query uses a `let` clause to determine the element that contains the style node.</span></span> <span data-ttu-id="d7426-117">Pokud není žádný element, pak `styleNode` je nastaven na: `null`</span><span class="sxs-lookup"><span data-stu-id="d7426-117">If there is no element, then `styleNode` is set to `null`:</span></span>  
  
```csharp  
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()  
```  
  
 <span data-ttu-id="d7426-118">`pPr` <xref:System.Xml.Linq.Extensions.Elements%2A> `pStyle` <xref:System.Linq.Enumerable.FirstOrDefault%2A> Klauzule nejprve <xref:System.Xml.Linq.XContainer.Elements%2A> používá osu k vyhledání všech prvků s názvem a poté používá metodu rozšíření k vyhledání všech podřízených elementů s názvem a nakonec používá standardní dotaz. `let` operátor pro převod kolekce na typ singleton.</span><span class="sxs-lookup"><span data-stu-id="d7426-118">The `let` clause first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="d7426-119">Je-li kolekce prázdná, `styleNode` je nastavena na `null`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d7426-119">If the collection is empty, `styleNode` is set to `null`.</span></span> <span data-ttu-id="d7426-120">Toto je užitečná idiom pro vyhledání `pStyle` podřízeného uzlu.</span><span class="sxs-lookup"><span data-stu-id="d7426-120">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="d7426-121">Všimněte si, že `pPr` Pokud neexistuje podřízený uzel, kód selže ani selže vyvoláním výjimky; `styleNode` namísto toho je nastavena na `null`, což je požadované chování této `let` klauzule.</span><span class="sxs-lookup"><span data-stu-id="d7426-121">Note that if the `pPr` child node does not exist, the code does nor fail by throwing an exception; instead, `styleNode` is set to `null`, which is the desired behavior of this `let` clause.</span></span>  
  
 <span data-ttu-id="d7426-122">Dotaz projektuje kolekci anonymního typu se dvěma členy `StyleName` a. `ParagraphNode`</span><span class="sxs-lookup"><span data-stu-id="d7426-122">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7426-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="d7426-123">Example</span></span>  
 <span data-ttu-id="d7426-124">Tento příklad zpracovává dokument WordprocessingML a načítá uzly odstavců z dokumentu WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="d7426-124">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="d7426-125">Určuje také styl každého odstavce.</span><span class="sxs-lookup"><span data-stu-id="d7426-125">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="d7426-126">Tento příklad sestaví na předchozích příkladech v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="d7426-126">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="d7426-127">Nový dotaz se zavolá v komentářích v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="d7426-127">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="d7426-128">Pokyny pro vytvoření zdrojového dokumentu pro tento příklad najdete v [tématu vytvoření zdrojového dokumentuC#XML pro Office Open](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="d7426-128">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="d7426-129">Tento příklad používá třídy nalezené v sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="d7426-129">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="d7426-130">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d7426-130">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="d7426-131">Tento příklad vytvoří následující výstup při použití v dokumentu popsaném v [tématu vytvoření zdrojového dokumentu XML pro OfficeC#()](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="d7426-131">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
## <a name="next-steps"></a><span data-ttu-id="d7426-132">Další kroky</span><span class="sxs-lookup"><span data-stu-id="d7426-132">Next Steps</span></span>  
 <span data-ttu-id="d7426-133">V dalším tématu [načtení textu odstavcůC#()](./retrieving-the-text-of-the-paragraphs.md)vytvoříte dotaz pro načtení textu odstavců.</span><span class="sxs-lookup"><span data-stu-id="d7426-133">In the next topic, [Retrieving the Text of the Paragraphs (C#)](./retrieving-the-text-of-the-paragraphs.md), you'll create a query to retrieve the text of paragraphs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7426-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d7426-134">See also</span></span>

- [<span data-ttu-id="d7426-135">Kurz: Manipulace s obsahem v dokumentu WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="d7426-135">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
