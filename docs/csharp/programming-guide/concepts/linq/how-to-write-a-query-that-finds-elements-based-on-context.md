---
title: Jak napsat dotaz, který vyhledá prvky na základě kontextu (C#)
ms.date: 07/20/2015
ms.assetid: 3ff79ef0-fc8b-42fe-8cc0-10dc32b06b4e
ms.openlocfilehash: 3fc131fdeb8dbf8871bfa455bc54eab0eeca7022
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75348369"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-c"></a><span data-ttu-id="345b1-102">Jak napsat dotaz, který vyhledá prvky na základě kontextu (C#)</span><span class="sxs-lookup"><span data-stu-id="345b1-102">How to write a query that finds elements based on context (C#)</span></span>
<span data-ttu-id="345b1-103">Někdy může být nutné napsat dotaz, který vybere prvky na základě jejich kontextu.</span><span class="sxs-lookup"><span data-stu-id="345b1-103">Sometimes you might have to write a query that selects elements based on their context.</span></span> <span data-ttu-id="345b1-104">Můžete chtít filtrovat na základě předchozínebo následující prvky na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="345b1-104">You might want to filter based on preceding or following sibling elements.</span></span> <span data-ttu-id="345b1-105">Můžete chtít filtrovat na základě podřízených nebo nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="345b1-105">You might want to filter based on child or ancestor elements.</span></span>  
  
 <span data-ttu-id="345b1-106">To lze provést zápisem dotazu a pomocí výsledků `where` dotazu v klauzuli.</span><span class="sxs-lookup"><span data-stu-id="345b1-106">You can do this by writing a query and using the results of the query in the `where` clause.</span></span> <span data-ttu-id="345b1-107">Pokud máte nejprve test proti null a potom otestovat hodnotu, je `let` vhodnější provést dotaz v `where` klauzuli a potom použít výsledky v klauzuli.</span><span class="sxs-lookup"><span data-stu-id="345b1-107">If you have to first test against null, and then test the value, it is more convenient to do the query in a `let` clause, and then use the results in the `where` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="345b1-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="345b1-108">Example</span></span>  
 <span data-ttu-id="345b1-109">Následující příklad vybere `p` všechny prvky, které `ul` jsou bezprostředně následuje prvek.</span><span class="sxs-lookup"><span data-stu-id="345b1-109">The following example selects all `p` elements that are immediately followed by a `ul` element.</span></span>  
  
```csharp  
XElement doc = XElement.Parse(@"<Root>  
    <p id=""1""/>  
    <ul>abc</ul>  
    <Child>  
        <p id=""2""/>  
        <notul/>  
        <p id=""3""/>  
        <ul>def</ul>  
        <p id=""4""/>  
    </Child>  
    <Child>  
        <p id=""5""/>  
        <notul/>  
        <p id=""6""/>  
        <ul>abc</ul>  
        <p id=""7""/>  
    </Child>  
</Root>");  
  
IEnumerable<XElement> items =  
    from e in doc.Descendants("p")  
    let z = e.ElementsAfterSelf().FirstOrDefault()  
    where z != null && z.Name.LocalName == "ul"  
    select e;  
  
foreach (XElement e in items)  
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));  
```  
  
 <span data-ttu-id="345b1-110">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="345b1-110">This code produces the following output:</span></span>  
  
```output  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a><span data-ttu-id="345b1-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="345b1-111">Example</span></span>  
 <span data-ttu-id="345b1-112">Následující příklad ukazuje stejný dotaz pro jazyk XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="345b1-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="345b1-113">Další informace naleznete [v tématu Přehled oborů názvů (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="345b1-113">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XElement doc = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>  
    <p id=""1""/>  
    <ul>abc</ul>  
    <Child>  
        <p id=""2""/>  
        <notul/>  
        <p id=""3""/>  
        <ul>def</ul>  
        <p id=""4""/>  
    </Child>  
    <Child>  
        <p id=""5""/>  
        <notul/>  
        <p id=""6""/>  
        <ul>abc</ul>  
        <p id=""7""/>  
    </Child>  
</Root>");  
  
XNamespace ad = "http://www.adatum.com";  
  
IEnumerable<XElement> items =  
    from e in doc.Descendants(ad + "p")  
    let z = e.ElementsAfterSelf().FirstOrDefault()  
    where z != null && z.Name == ad.GetName("ul")  
    select e;  
  
foreach (XElement e in items)  
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));  
```  
  
 <span data-ttu-id="345b1-114">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="345b1-114">This code produces the following output:</span></span>  
  
```output  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a><span data-ttu-id="345b1-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="345b1-115">See also</span></span>

- <xref:System.Xml.Linq.XElement.Parse%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>
