---
title: Jak napsat dotaz, který najde elementy na základě kontextu (C#)
description: Přečtěte si, jak napsat dotaz, který najde elementy na základě kontextu. Podívejte se na příklady kódu a zobrazte další prostředky.
ms.date: 07/20/2015
ms.assetid: 3ff79ef0-fc8b-42fe-8cc0-10dc32b06b4e
ms.openlocfilehash: 64f09a41c2c1d01b0be8f776461f9be9df9ecb5f
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303189"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-c"></a><span data-ttu-id="9126b-104">Jak napsat dotaz, který najde elementy na základě kontextu (C#)</span><span class="sxs-lookup"><span data-stu-id="9126b-104">How to write a query that finds elements based on context (C#)</span></span>
<span data-ttu-id="9126b-105">Někdy může být nutné napsat dotaz, který vybere prvky na základě jejich kontextu.</span><span class="sxs-lookup"><span data-stu-id="9126b-105">Sometimes you might have to write a query that selects elements based on their context.</span></span> <span data-ttu-id="9126b-106">Je možné, že budete chtít filtrovat na základě předchozích nebo následujících prvků na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="9126b-106">You might want to filter based on preceding or following sibling elements.</span></span> <span data-ttu-id="9126b-107">Je možné, že budete chtít filtrovat na základě podřízených nebo nadřazených prvků.</span><span class="sxs-lookup"><span data-stu-id="9126b-107">You might want to filter based on child or ancestor elements.</span></span>  
  
 <span data-ttu-id="9126b-108">To můžete provést vytvořením dotazu a použitím výsledků dotazu v `where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="9126b-108">You can do this by writing a query and using the results of the query in the `where` clause.</span></span> <span data-ttu-id="9126b-109">Pokud je třeba otestovat proti hodnotě null a potom otestovat hodnotu, je vhodnější provést dotaz v `let` klauzuli a potom použít výsledky v `where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="9126b-109">If you have to first test against null, and then test the value, it is more convenient to do the query in a `let` clause, and then use the results in the `where` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9126b-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="9126b-110">Example</span></span>  
 <span data-ttu-id="9126b-111">Následující příklad vybere všechny `p` prvky, které jsou bezprostředně následovány `ul` elementem.</span><span class="sxs-lookup"><span data-stu-id="9126b-111">The following example selects all `p` elements that are immediately followed by a `ul` element.</span></span>  
  
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
  
 <span data-ttu-id="9126b-112">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="9126b-112">This code produces the following output:</span></span>  
  
```output  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a><span data-ttu-id="9126b-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="9126b-113">Example</span></span>  
 <span data-ttu-id="9126b-114">Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="9126b-114">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="9126b-115">Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9126b-115">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="9126b-116">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="9126b-116">This code produces the following output:</span></span>  
  
```output  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a><span data-ttu-id="9126b-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9126b-117">See also</span></span>

- <xref:System.Xml.Linq.XElement.Parse%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>
