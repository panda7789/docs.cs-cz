---
title: Načtení textu odstavců (C#)
ms.date: 07/20/2015
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
ms.openlocfilehash: cedca9df84ee687a9e304cde0015b46d07956364
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423331"
---
# <a name="retrieving-the-text-of-the-paragraphs-c"></a><span data-ttu-id="ed858-102">Načtení textu odstavců (C#)</span><span class="sxs-lookup"><span data-stu-id="ed858-102">Retrieving the Text of the Paragraphs (C#)</span></span>
<span data-ttu-id="ed858-103">Tento příklad sestaví v předchozím příkladu [a načítá odstavce a jejich stylyC#()](./retrieving-the-paragraphs-and-their-styles.md).</span><span class="sxs-lookup"><span data-stu-id="ed858-103">This example builds on the previous example, [Retrieving the Paragraphs and Their Styles (C#)](./retrieving-the-paragraphs-and-their-styles.md).</span></span> <span data-ttu-id="ed858-104">Tento nový příklad načte text každého odstavce jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="ed858-104">This new example retrieves the text of each paragraph as a string.</span></span>  
  
 <span data-ttu-id="ed858-105">Chcete-li načíst text, tento příklad přidá další dotaz, který prochází kolekcí anonymních typů a projekty nové kolekce anonymního typu s přidáním nového člena, `Text`.</span><span class="sxs-lookup"><span data-stu-id="ed858-105">To retrieve the text, this example adds an additional query that iterates through the collection of anonymous types and projects a new collection of an anonymous type with the addition of a new member, `Text`.</span></span> <span data-ttu-id="ed858-106">Používá operátor dotazu <xref:System.Linq.Enumerable.Aggregate%2A> Standard k zřetězení více řetězců do jednoho řetězce.</span><span class="sxs-lookup"><span data-stu-id="ed858-106">It uses the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span>  
  
 <span data-ttu-id="ed858-107">Tato technika (to znamená, že nejprve procházíte do kolekce anonymního typu a pak tuto kolekci použijete pro projekt k nové kolekci anonymního typu) je běžné a užitečné idiom.</span><span class="sxs-lookup"><span data-stu-id="ed858-107">This technique (that is, first projecting to a collection of an anonymous type, then using this collection to project to a new collection of an anonymous type) is a common and useful idiom.</span></span> <span data-ttu-id="ed858-108">Tento dotaz může být zapsaný bez projekce prvního anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="ed858-108">This query could have been written without projecting to the first anonymous type.</span></span> <span data-ttu-id="ed858-109">Z důvodu opožděného vyhodnocení ale nevyužívá mnohem další výpočetní výkon.</span><span class="sxs-lookup"><span data-stu-id="ed858-109">However, because of lazy evaluation, doing so does not use much additional processing power.</span></span> <span data-ttu-id="ed858-110">Idiom vytváří v haldě krátkodobé objekty pro zpracování, ale v podstatě nesnižuje výkon.</span><span class="sxs-lookup"><span data-stu-id="ed858-110">The idiom creates more short lived objects on the heap, but this does not substantially degrade performance.</span></span>  
  
 <span data-ttu-id="ed858-111">Samozřejmě by bylo možné napsat jeden dotaz, který obsahuje funkce pro načtení odstavců, styl každého odstavce a text každého odstavce.</span><span class="sxs-lookup"><span data-stu-id="ed858-111">Of course, it would be possible to write a single query that contains the functionality to retrieve the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="ed858-112">Často je však užitečné rozdělit složitější dotaz do několika dotazů, protože výsledný kód je více modulární a snazší pro údržbu.</span><span class="sxs-lookup"><span data-stu-id="ed858-112">However, it often is useful to break up a more complicated query into multiple queries because the resulting code is more modular and easier to maintain.</span></span> <span data-ttu-id="ed858-113">Kromě toho, pokud potřebujete znovu použít část dotazu, je snazší Refaktorovat, pokud jsou dotazy zapisovány tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="ed858-113">Furthermore, if you need to reuse a portion of the query, it is easier to refactor if the queries are written in this manner.</span></span>  
  
 <span data-ttu-id="ed858-114">Tyto dotazy, které jsou zřetězeny společně, používají model zpracování, který je podrobně prověřen v tématu [kurz: zřetězení dotazů společněC#()](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ed858-114">These queries, which are chained together, use the processing model that is examined in detail in the topic [Tutorial: Chaining Queries Together (C#)](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed858-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="ed858-115">Example</span></span>  
 <span data-ttu-id="ed858-116">Tento příklad zpracovává dokument WordprocessingML, určuje uzel elementu, název stylu a text každého odstavce.</span><span class="sxs-lookup"><span data-stu-id="ed858-116">This example processes a WordprocessingML document, determining the element node, the style name, and the text of each paragraph.</span></span> <span data-ttu-id="ed858-117">Tento příklad sestaví na předchozích příkladech v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="ed858-117">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="ed858-118">Nový dotaz se zavolá v komentářích v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="ed858-118">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="ed858-119">Pokyny k vytvoření zdrojového dokumentu pro tento příklad najdete v tématu [vytvoření zdrojového dokumentu XML (C#) pro zdrojový Office](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="ed858-119">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="ed858-120">Tento příklad používá třídy ze sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="ed858-120">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="ed858-121">Používá typy v oboru názvů <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ed858-121">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="ed858-122">Tento příklad vytvoří následující výstup při použití v dokumentu popsaném v [tématu vytvoření zdrojového dokumentu XML pro OfficeC#()](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="ed858-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
## <a name="next-steps"></a><span data-ttu-id="ed858-123">Další kroky</span><span class="sxs-lookup"><span data-stu-id="ed858-123">Next Steps</span></span>  
 <span data-ttu-id="ed858-124">Další příklad ukazuje, jak použít rozšiřující metodu namísto <xref:System.Linq.Enumerable.Aggregate%2A>, k zřetězení více řetězců do jednoho řetězce.</span><span class="sxs-lookup"><span data-stu-id="ed858-124">The next example shows how to use an extension method, instead of <xref:System.Linq.Enumerable.Aggregate%2A>, to concatenate multiple strings into a single string.</span></span>  
  
- [<span data-ttu-id="ed858-125">Refaktoring pomocí metody rozšíření (C#)</span><span class="sxs-lookup"><span data-stu-id="ed858-125">Refactoring Using an Extension Method (C#)</span></span>](./refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="ed858-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ed858-126">See also</span></span>

- [<span data-ttu-id="ed858-127">Kurz: manipulace s obsahem v dokumentu WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="ed858-127">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](shape-of-wordprocessingml-documents.md)
- [<span data-ttu-id="ed858-128">Odložené provádění a opožděné vyhodnocení v LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="ed858-128">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
