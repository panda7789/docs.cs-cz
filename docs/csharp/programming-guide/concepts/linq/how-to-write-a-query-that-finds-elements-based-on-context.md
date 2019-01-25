---
title: 'Postupy: Napsat dotaz, který vyhledá elementy na základě kontextu (C#)'
ms.date: 07/20/2015
ms.assetid: 3ff79ef0-fc8b-42fe-8cc0-10dc32b06b4e
ms.openlocfilehash: 93bfd77ce6bb7be1d305f20f56da67e8fb9c22f0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667947"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-c"></a><span data-ttu-id="c3dd3-102">Postupy: Napsat dotaz, který vyhledá elementy na základě kontextu (C#)</span><span class="sxs-lookup"><span data-stu-id="c3dd3-102">How to: Write a Query that Finds Elements Based on Context (C#)</span></span>
<span data-ttu-id="c3dd3-103">V některých případech budete muset vytvořit dotaz, který vybere elementy podle jejich kontextu.</span><span class="sxs-lookup"><span data-stu-id="c3dd3-103">Sometimes you might have to write a query that selects elements based on their context.</span></span> <span data-ttu-id="c3dd3-104">Můžete filtrovat na základě před nebo za tímto elementů na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="c3dd3-104">You might want to filter based on preceding or following sibling elements.</span></span> <span data-ttu-id="c3dd3-105">Můžete filtrovat na základě podřízeného nebo nadřazeného elementy.</span><span class="sxs-lookup"><span data-stu-id="c3dd3-105">You might want to filter based on child or ancestor elements.</span></span>  
  
 <span data-ttu-id="c3dd3-106">To lze provést zadáním dotazu a pomocí výsledků dotazu v `where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="c3dd3-106">You can do this by writing a query and using the results of the query in the `where` clause.</span></span> <span data-ttu-id="c3dd3-107">Pokud je nutné nejprve otestovat s hodnotou null a pak testování hodnot, je pohodlnější provést dotaz `let` klauzule a pak použít výsledky v `where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="c3dd3-107">If you have to first test against null, and then test the value, it is more convenient to do the query in a `let` clause, and then use the results in the `where` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3dd3-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="c3dd3-108">Example</span></span>  
 <span data-ttu-id="c3dd3-109">V následujícím příkladu vybere všechny `p` prvky, které jsou okamžitě následovat `ul` elementu.</span><span class="sxs-lookup"><span data-stu-id="c3dd3-109">The following example selects all `p` elements that are immediately followed by a `ul` element.</span></span>  
  
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
  
 <span data-ttu-id="c3dd3-110">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c3dd3-110">This code produces the following output:</span></span>  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a><span data-ttu-id="c3dd3-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="c3dd3-111">Example</span></span>  
 <span data-ttu-id="c3dd3-112">Následující příklad ukazuje stejný dotaz pro soubor XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c3dd3-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="c3dd3-113">Další informace najdete v tématu [práce s názvovými prostory XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="c3dd3-113">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
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
  
 <span data-ttu-id="c3dd3-114">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c3dd3-114">This code produces the following output:</span></span>  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3dd3-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c3dd3-115">See also</span></span>

- <xref:System.Xml.Linq.XElement.Parse%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>
- [<span data-ttu-id="c3dd3-116">Základní dotazy (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c3dd3-116">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
