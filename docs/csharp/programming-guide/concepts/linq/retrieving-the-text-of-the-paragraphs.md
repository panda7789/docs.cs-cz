---
title: Načtení textu odstavců (C#)
ms.date: 07/20/2015
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
ms.openlocfilehash: 986145fa62722a35d23831a3818b89e63529b85f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253062"
---
# <a name="retrieving-the-text-of-the-paragraphs-c"></a><span data-ttu-id="36f7f-102">Načtení textu odstavců (C#)</span><span class="sxs-lookup"><span data-stu-id="36f7f-102">Retrieving the Text of the Paragraphs (C#)</span></span>
<span data-ttu-id="36f7f-103">Tento příklad sestaví v předchozím příkladu [a načítá odstavce a jejich stylyC#()](./retrieving-the-paragraphs-and-their-styles.md).</span><span class="sxs-lookup"><span data-stu-id="36f7f-103">This example builds on the previous example, [Retrieving the Paragraphs and Their Styles (C#)](./retrieving-the-paragraphs-and-their-styles.md).</span></span> <span data-ttu-id="36f7f-104">Tento nový příklad načte text každého odstavce jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="36f7f-104">This new example retrieves the text of each paragraph as a string.</span></span>  
  
 <span data-ttu-id="36f7f-105">Chcete-li načíst text, tento příklad přidá další dotaz, který projde kolekci anonymních typů a projekty novou kolekci anonymního typu s přidáním nového člena, `Text`.</span><span class="sxs-lookup"><span data-stu-id="36f7f-105">To retrieve the text, this example adds an additional query that iterates through the collection of anonymous types and projects a new collection of an anonymous type with the addition of a new member, `Text`.</span></span> <span data-ttu-id="36f7f-106">Používá <xref:System.Linq.Enumerable.Aggregate%2A> standardní operátor dotazu k zřetězení více řetězců do jednoho řetězce.</span><span class="sxs-lookup"><span data-stu-id="36f7f-106">It uses the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span>  
  
 <span data-ttu-id="36f7f-107">Tato technika (to znamená, že nejprve procházíte do kolekce anonymního typu a pak tuto kolekci použijete pro projekt k nové kolekci anonymního typu) je běžné a užitečné idiom.</span><span class="sxs-lookup"><span data-stu-id="36f7f-107">This technique (that is, first projecting to a collection of an anonymous type, then using this collection to project to a new collection of an anonymous type) is a common and useful idiom.</span></span> <span data-ttu-id="36f7f-108">Tento dotaz může být zapsaný bez projekce prvního anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="36f7f-108">This query could have been written without projecting to the first anonymous type.</span></span> <span data-ttu-id="36f7f-109">Z důvodu opožděného vyhodnocení ale nevyužívá mnohem další výpočetní výkon.</span><span class="sxs-lookup"><span data-stu-id="36f7f-109">However, because of lazy evaluation, doing so does not use much additional processing power.</span></span> <span data-ttu-id="36f7f-110">Idiom vytváří v haldě krátkodobé objekty pro zpracování, ale v podstatě nesnižuje výkon.</span><span class="sxs-lookup"><span data-stu-id="36f7f-110">The idiom creates more short lived objects on the heap, but this does not substantially degrade performance.</span></span>  
  
 <span data-ttu-id="36f7f-111">Samozřejmě by bylo možné napsat jeden dotaz, který obsahuje funkce pro načtení odstavců, styl každého odstavce a text každého odstavce.</span><span class="sxs-lookup"><span data-stu-id="36f7f-111">Of course, it would be possible to write a single query that contains the functionality to retrieve the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="36f7f-112">Často je však užitečné rozdělit složitější dotaz do několika dotazů, protože výsledný kód je více modulární a snazší pro údržbu.</span><span class="sxs-lookup"><span data-stu-id="36f7f-112">However, it often is useful to break up a more complicated query into multiple queries because the resulting code is more modular and easier to maintain.</span></span> <span data-ttu-id="36f7f-113">Kromě toho, pokud potřebujete znovu použít část dotazu, je snazší Refaktorovat, pokud jsou dotazy zapisovány tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="36f7f-113">Furthermore, if you need to reuse a portion of the query, it is easier to refactor if the queries are written in this manner.</span></span>  
  
 <span data-ttu-id="36f7f-114">Tyto dotazy, které jsou zřetězeny společně, používají model zpracování, který je podrobně prověřen v tématu [kurz: Zřetězení dotazů společně (C#)](./tutorial-chaining-queries-together.md).</span><span class="sxs-lookup"><span data-stu-id="36f7f-114">These queries, which are chained together, use the processing model that is examined in detail in the topic [Tutorial: Chaining Queries Together (C#)](./tutorial-chaining-queries-together.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="36f7f-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="36f7f-115">Example</span></span>  
 <span data-ttu-id="36f7f-116">Tento příklad zpracovává dokument WordprocessingML, určuje uzel elementu, název stylu a text každého odstavce.</span><span class="sxs-lookup"><span data-stu-id="36f7f-116">This example processes a WordprocessingML document, determining the element node, the style name, and the text of each paragraph.</span></span> <span data-ttu-id="36f7f-117">Tento příklad sestaví na předchozích příkladech v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="36f7f-117">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="36f7f-118">Nový dotaz se zavolá v komentářích v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="36f7f-118">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="36f7f-119">Pokyny k vytvoření zdrojového dokumentu pro tento příklad najdete v tématu [vytvoření zdrojového dokumentu XML (C#) pro zdrojový Office](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="36f7f-119">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="36f7f-120">Tento příklad používá třídy ze sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="36f7f-120">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="36f7f-121">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="36f7f-121">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
const string fileName = "SampleDoc.docx";  
  
const string documentRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string stylesRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";  
const string wordmlNamespace =  
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
XDocument xDoc = null;  
XDocument styleDoc = null;  
  
using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))  
{  
    PackageRelationship docPackageRelationship =  
      wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();  
    if (docPackageRelationship != null)  
    {  
        Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative),  
          docPackageRelationship.TargetUri);  
        PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
        //  Load the document XML in the part into an XDocument instance.  
        xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
        //  Find the styles part. There will only be one.  
        PackageRelationship styleRelation =  
          documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
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
  
// Find all paragraphs in the document.  
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
  
// Following is the new query that retrieves the text of  
// each paragraph.  
var paraWithText =  
    from para in paragraphs  
    select new  
    {  
        ParagraphNode = para.ParagraphNode,  
        StyleName = para.StyleName,  
        Text = para  
               .ParagraphNode  
               .Elements(w + "r")  
               .Elements(w + "t")  
               .Aggregate(  
                   new StringBuilder(),  
                   (s, i) => s.Append((string)i),  
                   s => s.ToString()  
               )  
    };  
  
foreach (var p in paraWithText)  
    Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
```  
  
 <span data-ttu-id="36f7f-122">Tento příklad vytvoří následující výstup při použití v dokumentu popsaném v [tématu vytvoření zdrojového dokumentu XML pro OfficeC#()](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="36f7f-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
```output  
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<  
StyleName:Normal ><  
StyleName:Normal >The following example prints to the console.<  
StyleName:Normal ><  
StyleName:Code >using System;<  
StyleName:Code ><  
StyleName:Code >class Program {<  
StyleName:Code >    public static void (string[] args) {<  
StyleName:Code >        Console.WriteLine("Hello World");<  
StyleName:Code >    }<  
StyleName:Code >}<  
StyleName:Normal ><  
StyleName:Normal >This example produces the following output:<  
StyleName:Normal ><  
StyleName:Code >Hello World<  
```  
  
## <a name="next-steps"></a><span data-ttu-id="36f7f-123">Další kroky</span><span class="sxs-lookup"><span data-stu-id="36f7f-123">Next Steps</span></span>  
 <span data-ttu-id="36f7f-124">Další příklad ukazuje <xref:System.Linq.Enumerable.Aggregate%2A>, jak použít rozšiřující metodu namísto, k zřetězení více řetězců do jednoho řetězce.</span><span class="sxs-lookup"><span data-stu-id="36f7f-124">The next example shows how to use an extension method, instead of <xref:System.Linq.Enumerable.Aggregate%2A>, to concatenate multiple strings into a single string.</span></span>  
  
- [<span data-ttu-id="36f7f-125">Refaktoring pomocí metody rozšíření (C#)</span><span class="sxs-lookup"><span data-stu-id="36f7f-125">Refactoring Using an Extension Method (C#)</span></span>](./refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="36f7f-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="36f7f-126">See also</span></span>

- [<span data-ttu-id="36f7f-127">Kurz: Manipulace s obsahem v dokumentu WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="36f7f-127">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [<span data-ttu-id="36f7f-128">Odložené provádění a opožděné vyhodnocení v LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="36f7f-128">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
