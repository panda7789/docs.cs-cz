---
title: 'Postupy: ladění prázdných sad výsledků dotazu (C#)'
ms.date: 07/20/2015
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
ms.openlocfilehash: 4760b1e5274634954bd5fe4b3880fd4415af2510
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43779838"
---
# <a name="how-to-debug-empty-query-results-sets-c"></a><span data-ttu-id="b996a-102">Postupy: ladění prázdných sad výsledků dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="b996a-102">How to: Debug Empty Query Results Sets (C#)</span></span>
<span data-ttu-id="b996a-103">Jedním z nejběžnějších problémů při dotazování na stromy XML je, že pokud stromu XML má výchozí obor názvů, vývojář někdy zapíše dotaz jakoby nebyly v oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="b996a-103">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="b996a-104">První sada příklady v tomto tématu ukazuje typické tak, že je načteno XML ve výchozím oboru názvů a dotazuje se nesprávně.</span><span class="sxs-lookup"><span data-stu-id="b996a-104">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>  
  
 <span data-ttu-id="b996a-105">Druhá sada příklady ukazují potřebné opravy tak, aby můžete dát dotaz na XML v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b996a-105">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
 <span data-ttu-id="b996a-106">Další informace najdete v tématu [práce s názvovými prostory XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="b996a-106">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b996a-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="b996a-107">Example</span></span>  
 <span data-ttu-id="b996a-108">Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který vrací prázdný výsledek sadu.</span><span class="sxs-lookup"><span data-stu-id="b996a-108">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements("Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
 <span data-ttu-id="b996a-109">Tento příklad vytvoří následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="b996a-109">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="b996a-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="b996a-110">Example</span></span>  
 <span data-ttu-id="b996a-111">Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který je zakódovaný správně.</span><span class="sxs-lookup"><span data-stu-id="b996a-111">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="b996a-112">Řešením je deklarovat a inicializovat <xref:System.Xml.Linq.XNamespace> objektu a použít je při zadávání <xref:System.Xml.Linq.XName> objekty.</span><span class="sxs-lookup"><span data-stu-id="b996a-112">The solution is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="b996a-113">V tomto případě, že argument <xref:System.Xml.Linq.XElement.Elements%2A> metoda je <xref:System.Xml.Linq.XName> objektu.</span><span class="sxs-lookup"><span data-stu-id="b996a-113">In this case, the argument to the <xref:System.Xml.Linq.XElement.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
 <span data-ttu-id="b996a-114">Tento příklad vytvoří následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="b996a-114">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="b996a-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="b996a-115">See Also</span></span>

- [<span data-ttu-id="b996a-116">Základní dotazy (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b996a-116">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
