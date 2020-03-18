---
title: Načítání odstavců a jejich stylů (C#)
ms.date: 07/20/2015
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
ms.openlocfilehash: 47127b6f1d6bfaa0d8d93333882a0d0b59f1bae6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168294"
---
# <a name="retrieving-the-paragraphs-and-their-styles-c"></a><span data-ttu-id="30545-102">Načítání odstavců a jejich stylů (C#)</span><span class="sxs-lookup"><span data-stu-id="30545-102">Retrieving the Paragraphs and Their Styles (C#)</span></span>
<span data-ttu-id="30545-103">V tomto příkladu napíšeme dotaz, který načte uzly odstavce z dokumentu Wordprocessing ML.</span><span class="sxs-lookup"><span data-stu-id="30545-103">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="30545-104">Také identifikuje styl každého odstavce.</span><span class="sxs-lookup"><span data-stu-id="30545-104">It also identifies the style of each paragraph.</span></span>  
  
 <span data-ttu-id="30545-105">Tento dotaz vychází z dotazu v předchozím příkladu [Hledání výchozího odstavcového stylu (C#),](./finding-the-default-paragraph-style.md)který načte výchozí styl ze seznamu stylů.</span><span class="sxs-lookup"><span data-stu-id="30545-105">This query builds on the query in the previous example, [Finding the Default Paragraph Style (C#)](./finding-the-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="30545-106">Tyto informace jsou vyžadovány tak, aby dotaz mohl identifikovat styl odstavců, které nemají explicitně nastavený styl.</span><span class="sxs-lookup"><span data-stu-id="30545-106">This information is required so that the query can identify the style of paragraphs that do not have a style explicitly set.</span></span> <span data-ttu-id="30545-107">Odstavcové styly `w:pPr` jsou nastaveny prostřednictvím prvku; Pokud odstavec tento prvek neobsahuje, je formátován s výchozím stylem.</span><span class="sxs-lookup"><span data-stu-id="30545-107">Paragraph styles are set through the `w:pPr` element; if a paragraph does not contain this element, it is formatted with the default style.</span></span>  
  
 <span data-ttu-id="30545-108">Toto téma vysvětluje význam některých částí dotazu a potom zobrazí dotaz jako součást úplného, pracovního příkladu.</span><span class="sxs-lookup"><span data-stu-id="30545-108">This topic explains the significance of some pieces of the query, then shows the query as part of a complete, working example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30545-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="30545-109">Example</span></span>  
 <span data-ttu-id="30545-110">Zdroj dotazu pro načtení všech odstavců v dokumentu a jejich styly je následující:</span><span class="sxs-lookup"><span data-stu-id="30545-110">The source of the query to retrieve all the paragraphs in a document and their styles is as follows:</span></span>  
  
```csharp  
xDoc.Root.Element(w + "body").Descendants(w + "p")  
```  
  
 <span data-ttu-id="30545-111">Tento výraz je podobný zdroji dotazu v předchozím příkladu [Hledání výchozího odstavcového stylu (C#).](./finding-the-default-paragraph-style.md)</span><span class="sxs-lookup"><span data-stu-id="30545-111">This expression is similar to the source of the query in the previous example, [Finding the Default Paragraph Style (C#)](./finding-the-default-paragraph-style.md).</span></span> <span data-ttu-id="30545-112">Hlavní rozdíl spočá, že používá osu <xref:System.Xml.Linq.XContainer.Descendants%2A> namísto osy. <xref:System.Xml.Linq.XContainer.Elements%2A></span><span class="sxs-lookup"><span data-stu-id="30545-112">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="30545-113">Dotaz používá <xref:System.Xml.Linq.XContainer.Descendants%2A> osu, protože v dokumentech, které mají oddíly, odstavce nebudou přímými podřízenými prvky těla; spíše odstavce budou v hierarchii o dvě úrovně níže.</span><span class="sxs-lookup"><span data-stu-id="30545-113">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs will not be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="30545-114">Pomocí <xref:System.Xml.Linq.XContainer.Descendants%2A> osy bude kód fungovat, zda dokument používá oddíly.</span><span class="sxs-lookup"><span data-stu-id="30545-114">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work of whether or not the document uses sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30545-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="30545-115">Example</span></span>  
 <span data-ttu-id="30545-116">Dotaz používá `let` klauzuli k určení prvku, který obsahuje uzel stylu.</span><span class="sxs-lookup"><span data-stu-id="30545-116">The query uses a `let` clause to determine the element that contains the style node.</span></span> <span data-ttu-id="30545-117">Pokud není žádný prvek, `styleNode` pak `null`je nastavena na :</span><span class="sxs-lookup"><span data-stu-id="30545-117">If there is no element, then `styleNode` is set to `null`:</span></span>  
  
```csharp  
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()  
```  
  
 <span data-ttu-id="30545-118">`let` Klauzule nejprve <xref:System.Xml.Linq.XContainer.Elements%2A> používá osu `pPr`najít všechny <xref:System.Xml.Linq.Extensions.Elements%2A> prvky s názvem `pStyle`, pak používá <xref:System.Linq.Enumerable.FirstOrDefault%2A> metodu rozšíření najít všechny podřízené prvky s názvem a nakonec používá operátor standardní dotaz převést kolekci na singleton.</span><span class="sxs-lookup"><span data-stu-id="30545-118">The `let` clause first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="30545-119">Pokud je kolekce `styleNode` prázdná, `null`je nastavena na .</span><span class="sxs-lookup"><span data-stu-id="30545-119">If the collection is empty, `styleNode` is set to `null`.</span></span> <span data-ttu-id="30545-120">To to je užitečné idiom `pStyle` hledat uzel potomka.</span><span class="sxs-lookup"><span data-stu-id="30545-120">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="30545-121">Všimněte si, že pokud `pPr` podřízený uzel neexistuje, kód neselže ani nepodaří vyvoláním výjimky; místo `styleNode` , je `null`nastavena na , `let` což je požadované chování této klauzule.</span><span class="sxs-lookup"><span data-stu-id="30545-121">Note that if the `pPr` child node does not exist, the code does nor fail by throwing an exception; instead, `styleNode` is set to `null`, which is the desired behavior of this `let` clause.</span></span>  
  
 <span data-ttu-id="30545-122">Dotaz projekty kolekce anonymního typu se `StyleName` `ParagraphNode`dvěma členy a .</span><span class="sxs-lookup"><span data-stu-id="30545-122">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30545-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="30545-123">Example</span></span>  
 <span data-ttu-id="30545-124">Tento příklad zpracuje dokument WordprocessingML, načtení odstavcových uzlů z dokumentu WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="30545-124">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="30545-125">Také identifikuje styl každého odstavce.</span><span class="sxs-lookup"><span data-stu-id="30545-125">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="30545-126">Tento příklad vychází z předchozích příkladů v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="30545-126">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="30545-127">Nový dotaz je volán v komentářích v níže uvedeném kódu.</span><span class="sxs-lookup"><span data-stu-id="30545-127">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="30545-128">Pokyny pro vytvoření zdrojového dokumentu pro tento příklad naleznete v [části Vytvoření dokumentu Open XML (C#) zdrojové sady Office](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="30545-128">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="30545-129">Tento příklad používá třídy nalezené v sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="30545-129">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="30545-130">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="30545-130">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="30545-131">Tento příklad vytvoří následující výstup při použití na dokument popsaný v [části Vytvoření dokumentu Open XML (C#) zdrojové kanceláře](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="30545-131">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
## <a name="next-steps"></a><span data-ttu-id="30545-132">Další kroky</span><span class="sxs-lookup"><span data-stu-id="30545-132">Next Steps</span></span>  
 <span data-ttu-id="30545-133">V dalším tématu [Načítání textu odstavců (C#)](./retrieving-the-text-of-the-paragraphs.md)vytvoříte dotaz pro načtení textu odstavců.</span><span class="sxs-lookup"><span data-stu-id="30545-133">In the next topic, [Retrieving the Text of the Paragraphs (C#)](./retrieving-the-text-of-the-paragraphs.md), you'll create a query to retrieve the text of paragraphs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30545-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="30545-134">See also</span></span>

- [<span data-ttu-id="30545-135">Kurz: Manipulace s obsahem v dokumentu WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="30545-135">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
