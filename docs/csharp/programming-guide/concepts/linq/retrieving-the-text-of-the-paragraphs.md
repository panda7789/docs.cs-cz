---
title: Načtení textu odstavců (C#)
ms.date: 07/20/2015
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
ms.openlocfilehash: 1d23addb4c4c1ea17343585392fbe08fef08568a
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46508369"
---
# <a name="retrieving-the-text-of-the-paragraphs-c"></a><span data-ttu-id="b9dbc-102">Načtení textu odstavců (C#)</span><span class="sxs-lookup"><span data-stu-id="b9dbc-102">Retrieving the Text of the Paragraphs (C#)</span></span>
<span data-ttu-id="b9dbc-103">Tento příklad je založen na předchozím příkladu [načtení odstavců a jejich stylů (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md).</span><span class="sxs-lookup"><span data-stu-id="b9dbc-103">This example builds on the previous example, [Retrieving the Paragraphs and Their Styles (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md).</span></span> <span data-ttu-id="b9dbc-104">Tento nový příklad načte text k jednotlivým odstavcům jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="b9dbc-104">This new example retrieves the text of each paragraph as a string.</span></span>  
  
 <span data-ttu-id="b9dbc-105">K získání textu, v tomto příkladu přidá další dotaz, který Iteruje přes kolekci anonymních typů a projekty novou kolekci s přidáním nového člena anonymního typu `Text`.</span><span class="sxs-lookup"><span data-stu-id="b9dbc-105">To retrieve the text, this example adds an additional query that iterates through the collection of anonymous types and projects a new collection of an anonymous type with the addition of a new member, `Text`.</span></span> <span data-ttu-id="b9dbc-106">Používá <xref:System.Linq.Enumerable.Aggregate%2A> operátor standardního dotazu pro řetězení více řetězců do jednoho řetězce.</span><span class="sxs-lookup"><span data-stu-id="b9dbc-106">It uses the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span>  
  
 <span data-ttu-id="b9dbc-107">Tato technika (to znamená, že první promítání na kolekci anonymního typu a pak pomocí této kolekce projektu do nové kolekce anonymního typu) je běžné a užitečné idiom.</span><span class="sxs-lookup"><span data-stu-id="b9dbc-107">This technique (that is, first projecting to a collection of an anonymous type, then using this collection to project to a new collection of an anonymous type) is a common and useful idiom.</span></span> <span data-ttu-id="b9dbc-108">Tento dotaz by mohl být napsán bez promítání na první anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="b9dbc-108">This query could have been written without projecting to the first anonymous type.</span></span> <span data-ttu-id="b9dbc-109">Však z důvodu opožděné vyhodnocení to uděláte tak nebude používat mnoho další výpočetní výkon.</span><span class="sxs-lookup"><span data-stu-id="b9dbc-109">However, because of lazy evaluation, doing so does not use much additional processing power.</span></span> <span data-ttu-id="b9dbc-110">Idiom vytvoří více krátký povahy objektů na haldě, ale to mít nežádoucí vliv podstatně výkonu.</span><span class="sxs-lookup"><span data-stu-id="b9dbc-110">The idiom creates more short lived objects on the heap, but this does not substantially degrade performance.</span></span>  
  
 <span data-ttu-id="b9dbc-111">Samozřejmě by bylo možné vytvořit jeden dotaz, který obsahuje funkce pro načtení odstavců, styl k jednotlivým odstavcům a každý odstavec.</span><span class="sxs-lookup"><span data-stu-id="b9dbc-111">Of course, it would be possible to write a single query that contains the functionality to retrieve the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="b9dbc-112">Ale často je užitečné rozdělit složitější dotaz do více dotazů, protože výsledný kód je modulární a jednodušší správu.</span><span class="sxs-lookup"><span data-stu-id="b9dbc-112">However, it often is useful to break up a more complicated query into multiple queries because the resulting code is more modular and easier to maintain.</span></span> <span data-ttu-id="b9dbc-113">Kromě toho pokud je potřeba znovu použít části dotazu, je jednodušší refaktorace Pokud dotazy se zapisují tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="b9dbc-113">Furthermore, if you need to reuse a portion of the query, it is easier to refactor if the queries are written in this manner.</span></span>  
  
 <span data-ttu-id="b9dbc-114">Tyto dotazy, které jsou zřetězen dohromady, použijte zpracování modelu, který je podrobně v tématu [kurz: zřetězení dotazů současně (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md).</span><span class="sxs-lookup"><span data-stu-id="b9dbc-114">These queries, which are chained together, use the processing model that is examined in detail in the topic [Tutorial: Chaining Queries Together (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9dbc-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="b9dbc-115">Example</span></span>  
 <span data-ttu-id="b9dbc-116">V tomto příkladu zpracovává dokumentu WordprocessingML, určení uzlu elementu, název stylu a každý odstavec.</span><span class="sxs-lookup"><span data-stu-id="b9dbc-116">This example processes a WordprocessingML document, determining the element node, the style name, and the text of each paragraph.</span></span> <span data-ttu-id="b9dbc-117">Tento příklad je založen na předchozí příklady v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="b9dbc-117">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="b9dbc-118">Nový dotaz je uvedeny v komentářích v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="b9dbc-118">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="b9dbc-119">Pokyny pro vytvoření zdrojového dokumentu pro účely tohoto příkladu naleznete v tématu [vytváření zdroj Office Open XML dokumentu (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="b9dbc-119">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="b9dbc-120">Tento příklad používá třídy z WindowsBase sestavení.</span><span class="sxs-lookup"><span data-stu-id="b9dbc-120">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="b9dbc-121">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b9dbc-121">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="b9dbc-122">Tento příklad vytvoří následující výstup při použití u dokumentu je popsáno v [vytváření zdroj Office Open XML dokumentu (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="b9dbc-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
```  
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
  
## <a name="next-steps"></a><span data-ttu-id="b9dbc-123">Další kroky</span><span class="sxs-lookup"><span data-stu-id="b9dbc-123">Next Steps</span></span>  
 <span data-ttu-id="b9dbc-124">Následující příklad ukazuje způsob použití metody rozšíření, namísto <xref:System.Linq.Enumerable.Aggregate%2A>pro řetězení více řetězců do jednoho řetězce.</span><span class="sxs-lookup"><span data-stu-id="b9dbc-124">The next example shows how to use an extension method, instead of <xref:System.Linq.Enumerable.Aggregate%2A>, to concatenate multiple strings into a single string.</span></span>  
  
-   [<span data-ttu-id="b9dbc-125">Refaktoring pomocí rozšiřující metodu (C#)</span><span class="sxs-lookup"><span data-stu-id="b9dbc-125">Refactoring Using an Extension Method (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="b9dbc-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9dbc-126">See Also</span></span>

- [<span data-ttu-id="b9dbc-127">Kurz: Manipulace s obsahem v dokumentu WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="b9dbc-127">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)  
- [<span data-ttu-id="b9dbc-128">Odložené provedení a opožděné vyhodnocení v LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="b9dbc-128">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
