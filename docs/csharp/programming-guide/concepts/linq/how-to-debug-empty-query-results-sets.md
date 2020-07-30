---
title: Jak ladit prázdné sady výsledků dotazu (C#)
description: Naučte se ladit prázdné sady výsledků dotazu. Tyto sady mohou nastat, pokud vývojář napsal dotaz, jako by kód XML nebyl v oboru názvů.
ms.date: 07/20/2015
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
ms.openlocfilehash: ad6d39697e5a59fe23ca700ceeb2a9860d05bb94
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302903"
---
# <a name="how-to-debug-empty-query-results-sets-c"></a><span data-ttu-id="21907-104">Jak ladit prázdné sady výsledků dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="21907-104">How to debug empty query results sets (C#)</span></span>
<span data-ttu-id="21907-105">Jedním z nejběžnějších problémů při dotazování na stromy XML je, že pokud má strom XML výchozí obor názvů, vývojář někdy zapíše dotaz, jako by kód XML nebyl v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="21907-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="21907-106">První sada příkladů v tomto tématu ukazuje typický způsob, jakým je načten XML ve výchozím oboru názvů a je dotaz na něj nesprávně.</span><span class="sxs-lookup"><span data-stu-id="21907-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>  
  
 <span data-ttu-id="21907-107">Druhá sada příkladů ukazuje nezbytné opravy, aby bylo možné dotazovat XML v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="21907-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
 <span data-ttu-id="21907-108">Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="21907-108">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="21907-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="21907-109">Example</span></span>  
 <span data-ttu-id="21907-110">Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který vrací prázdnou sadu výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="21907-110">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
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
  
 <span data-ttu-id="21907-111">Tento příklad vytvoří následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="21907-111">This example produces the following result:</span></span>  
  
```output  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="21907-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="21907-112">Example</span></span>  
 <span data-ttu-id="21907-113">Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který je správně kódován.</span><span class="sxs-lookup"><span data-stu-id="21907-113">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="21907-114">Řešením je deklarovat a inicializovat <xref:System.Xml.Linq.XNamespace> objekt a použít ho při zadávání <xref:System.Xml.Linq.XName> objektů.</span><span class="sxs-lookup"><span data-stu-id="21907-114">The solution is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="21907-115">V tomto případě argument <xref:System.Xml.Linq.XContainer.Elements%2A> metody je <xref:System.Xml.Linq.XName> objekt.</span><span class="sxs-lookup"><span data-stu-id="21907-115">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
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
  
 <span data-ttu-id="21907-116">Tento příklad vytvoří následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="21907-116">This example produces the following result:</span></span>  
  
```output  
Result set follows:  
1  
2  
3  
End of result set  
```  
