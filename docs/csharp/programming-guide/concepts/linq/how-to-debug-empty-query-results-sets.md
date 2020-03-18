---
title: Jak ladit prázdné sady výsledků dotazu (C#)
ms.date: 07/20/2015
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
ms.openlocfilehash: 2716f7c525ac6bee8d2fb374e4ecc4c975d852a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141292"
---
# <a name="how-to-debug-empty-query-results-sets-c"></a><span data-ttu-id="100ea-102">Jak ladit prázdné sady výsledků dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="100ea-102">How to debug empty query results sets (C#)</span></span>
<span data-ttu-id="100ea-103">Jedním z nejčastějších problémů při dotazování na stromy XML je, že pokud má strom XML výchozí obor názvů, vývojář někdy zapíše dotaz, jako by xml nebyl v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="100ea-103">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="100ea-104">První sada příkladů v tomto tématu ukazuje typický způsob, jakým je načten xml ve výchozím oboru názvů a je dotazován nesprávně.</span><span class="sxs-lookup"><span data-stu-id="100ea-104">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>  
  
 <span data-ttu-id="100ea-105">Druhá sada příkladů zobrazuje potřebné opravy, takže můžete dotazovat XML v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="100ea-105">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
 <span data-ttu-id="100ea-106">Další informace naleznete [v tématu Přehled oborů názvů (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="100ea-106">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="100ea-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="100ea-107">Example</span></span>  
 <span data-ttu-id="100ea-108">Tento příklad ukazuje vytvoření xml v oboru názvů a dotaz, který vrací prázdnou sadu výsledků.</span><span class="sxs-lookup"><span data-stu-id="100ea-108">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
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
  
 <span data-ttu-id="100ea-109">Tento příklad přináší následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="100ea-109">This example produces the following result:</span></span>  
  
```output  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="100ea-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="100ea-110">Example</span></span>  
 <span data-ttu-id="100ea-111">Tento příklad ukazuje vytvoření xml v oboru názvů a dotaz, který je kódován správně.</span><span class="sxs-lookup"><span data-stu-id="100ea-111">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="100ea-112">Řešením je deklarovat a <xref:System.Xml.Linq.XNamespace> inicializovat objekt a <xref:System.Xml.Linq.XName> použít jej při zadávání objektů.</span><span class="sxs-lookup"><span data-stu-id="100ea-112">The solution is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="100ea-113">V tomto případě argument <xref:System.Xml.Linq.XContainer.Elements%2A> metody je <xref:System.Xml.Linq.XName> objekt.</span><span class="sxs-lookup"><span data-stu-id="100ea-113">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
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
  
 <span data-ttu-id="100ea-114">Tento příklad přináší následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="100ea-114">This example produces the following result:</span></span>  
  
```output  
Result set follows:  
1  
2  
3  
End of result set  
```  
