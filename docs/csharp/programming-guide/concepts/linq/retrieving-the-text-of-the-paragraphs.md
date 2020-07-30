---
title: Načtení textu odstavců (C#)
description: Naučte se používat dotazy LINQ k získání textu každého odstavce v dokumentu WordprocessingML jako řetězce v jazyce C#. Tento příklad používá zřetězené dotazy.
ms.date: 07/20/2015
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
ms.openlocfilehash: 58a07ab848307c886927815e4e49e90806f61346
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302591"
---
# <a name="retrieving-the-text-of-the-paragraphs-c"></a><span data-ttu-id="3e076-104">Načtení textu odstavců (C#)</span><span class="sxs-lookup"><span data-stu-id="3e076-104">Retrieving the Text of the Paragraphs (C#)</span></span>
<span data-ttu-id="3e076-105">Tento příklad sestaví v předchozím příkladu [a načítá odstavce a jejich styly (C#)](./retrieving-the-paragraphs-and-their-styles.md).</span><span class="sxs-lookup"><span data-stu-id="3e076-105">This example builds on the previous example, [Retrieving the Paragraphs and Their Styles (C#)](./retrieving-the-paragraphs-and-their-styles.md).</span></span> <span data-ttu-id="3e076-106">Tento nový příklad načte text každého odstavce jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="3e076-106">This new example retrieves the text of each paragraph as a string.</span></span>  
  
 <span data-ttu-id="3e076-107">Chcete-li načíst text, tento příklad přidá další dotaz, který projde kolekci anonymních typů a projekty novou kolekci anonymního typu s přidáním nového člena, `Text` .</span><span class="sxs-lookup"><span data-stu-id="3e076-107">To retrieve the text, this example adds an additional query that iterates through the collection of anonymous types and projects a new collection of an anonymous type with the addition of a new member, `Text`.</span></span> <span data-ttu-id="3e076-108">Používá <xref:System.Linq.Enumerable.Aggregate%2A> standardní operátor dotazu k zřetězení více řetězců do jednoho řetězce.</span><span class="sxs-lookup"><span data-stu-id="3e076-108">It uses the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span>  
  
 <span data-ttu-id="3e076-109">Tato technika (to znamená, že nejprve procházíte do kolekce anonymního typu a pak tuto kolekci použijete pro projekt k nové kolekci anonymního typu) je běžné a užitečné idiom.</span><span class="sxs-lookup"><span data-stu-id="3e076-109">This technique (that is, first projecting to a collection of an anonymous type, then using this collection to project to a new collection of an anonymous type) is a common and useful idiom.</span></span> <span data-ttu-id="3e076-110">Tento dotaz může být zapsaný bez projekce prvního anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="3e076-110">This query could have been written without projecting to the first anonymous type.</span></span> <span data-ttu-id="3e076-111">Z důvodu opožděného vyhodnocení ale nevyužívá mnohem další výpočetní výkon.</span><span class="sxs-lookup"><span data-stu-id="3e076-111">However, because of lazy evaluation, doing so does not use much additional processing power.</span></span> <span data-ttu-id="3e076-112">Idiom vytváří v haldě krátkodobé objekty pro zpracování, ale v podstatě nesnižuje výkon.</span><span class="sxs-lookup"><span data-stu-id="3e076-112">The idiom creates more short lived objects on the heap, but this does not substantially degrade performance.</span></span>  
  
 <span data-ttu-id="3e076-113">Samozřejmě by bylo možné napsat jeden dotaz, který obsahuje funkce pro načtení odstavců, styl každého odstavce a text každého odstavce.</span><span class="sxs-lookup"><span data-stu-id="3e076-113">Of course, it would be possible to write a single query that contains the functionality to retrieve the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="3e076-114">Často je však užitečné rozdělit složitější dotaz do několika dotazů, protože výsledný kód je více modulární a snazší pro údržbu.</span><span class="sxs-lookup"><span data-stu-id="3e076-114">However, it often is useful to break up a more complicated query into multiple queries because the resulting code is more modular and easier to maintain.</span></span> <span data-ttu-id="3e076-115">Kromě toho, pokud potřebujete znovu použít část dotazu, je snazší Refaktorovat, pokud jsou dotazy zapisovány tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="3e076-115">Furthermore, if you need to reuse a portion of the query, it is easier to refactor if the queries are written in this manner.</span></span>  
  
 <span data-ttu-id="3e076-116">Tyto dotazy, které jsou zřetězeny společně, používají model zpracování, který je podrobně prověřen v tématu [kurz: zřetězení dotazů dohromady (C#)](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3e076-116">These queries, which are chained together, use the processing model that is examined in detail in the topic [Tutorial: Chaining Queries Together (C#)](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e076-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="3e076-117">Example</span></span>  
 <span data-ttu-id="3e076-118">Tento příklad zpracovává dokument WordprocessingML, určuje uzel elementu, název stylu a text každého odstavce.</span><span class="sxs-lookup"><span data-stu-id="3e076-118">This example processes a WordprocessingML document, determining the element node, the style name, and the text of each paragraph.</span></span> <span data-ttu-id="3e076-119">Tento příklad sestaví na předchozích příkladech v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="3e076-119">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="3e076-120">Nový dotaz se zavolá v komentářích v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="3e076-120">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="3e076-121">Pokyny pro vytvoření zdrojového dokumentu pro tento příklad najdete v tématu [vytvoření zdrojového dokumentu XML pro Office (C#)](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="3e076-121">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="3e076-122">Tento příklad používá třídy ze sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="3e076-122">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="3e076-123">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3e076-123">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="3e076-124">Tento příklad vytvoří následující výstup při použití v dokumentu popsaném v [tématu vytvoření zdrojového dokumentu XML pro Office (C#)](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="3e076-124">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
## <a name="next-steps"></a><span data-ttu-id="3e076-125">Další kroky</span><span class="sxs-lookup"><span data-stu-id="3e076-125">Next Steps</span></span>  
 <span data-ttu-id="3e076-126">Další příklad ukazuje, jak použít rozšiřující metodu namísto <xref:System.Linq.Enumerable.Aggregate%2A> , k zřetězení více řetězců do jednoho řetězce.</span><span class="sxs-lookup"><span data-stu-id="3e076-126">The next example shows how to use an extension method, instead of <xref:System.Linq.Enumerable.Aggregate%2A>, to concatenate multiple strings into a single string.</span></span>  
  
- [<span data-ttu-id="3e076-127">Refaktoring pomocí metody rozšíření (C#)</span><span class="sxs-lookup"><span data-stu-id="3e076-127">Refactoring Using an Extension Method (C#)</span></span>](./refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="3e076-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3e076-128">See also</span></span>

- [<span data-ttu-id="3e076-129">Kurz: manipulace s obsahem v dokumentu WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="3e076-129">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](shape-of-wordprocessingml-documents.md)
- [<span data-ttu-id="3e076-130">Odložené provádění a opožděné vyhodnocení v LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="3e076-130">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
