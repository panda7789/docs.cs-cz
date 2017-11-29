---
title: "Postupy: ladění sady výsledků dotazu prázdný (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f8fb77a65c2c5023685251435d3028ffa9b3c2b3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-debug-empty-query-results-sets-c"></a><span data-ttu-id="8a673-102">Postupy: ladění sady výsledků dotazu prázdný (C#)</span><span class="sxs-lookup"><span data-stu-id="8a673-102">How to: Debug Empty Query Results Sets (C#)</span></span>
<span data-ttu-id="8a673-103">Jeden z nejběžnějších problémů při dotazování stromy XML je, že pokud stromu XML má výchozí obor názvů, vývojář někdy zapíše dotazu, jako by soubor XML není v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8a673-103">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="8a673-104">První sadu příklady v tomto tématu ukazuje obvyklým způsobem, že je načteno kód XML v výchozí obor názvů a je dotazován nesprávně.</span><span class="sxs-lookup"><span data-stu-id="8a673-104">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>  
  
 <span data-ttu-id="8a673-105">Druhá sada příklady zobrazit potřebné opravy tak, aby v oboru názvů se můžete dotazovat XML.</span><span class="sxs-lookup"><span data-stu-id="8a673-105">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
 <span data-ttu-id="8a673-106">Další informace najdete v tématu [práci s obory názvů XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="8a673-106">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a673-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="8a673-107">Example</span></span>  
 <span data-ttu-id="8a673-108">Tento příklad ukazuje vytvoření XML v oboru názvů a nastavte dotaz, který vrací prázdný výsledek.</span><span class="sxs-lookup"><span data-stu-id="8a673-108">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
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
  
 <span data-ttu-id="8a673-109">Tento příklad vytvoří následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="8a673-109">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="8a673-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="8a673-110">Example</span></span>  
 <span data-ttu-id="8a673-111">Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který je zakódovaný správně.</span><span class="sxs-lookup"><span data-stu-id="8a673-111">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="8a673-112">Řešení je deklarace a inicializace <xref:System.Xml.Linq.XNamespace> objekt a který můžete použít při zadávání <xref:System.Xml.Linq.XName> objekty.</span><span class="sxs-lookup"><span data-stu-id="8a673-112">The solution is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="8a673-113">V tomto případě argument <xref:System.Xml.Linq.XElement.Elements%2A> je metoda <xref:System.Xml.Linq.XName> objektu.</span><span class="sxs-lookup"><span data-stu-id="8a673-113">In this case, the argument to the <xref:System.Xml.Linq.XElement.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
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
  
 <span data-ttu-id="8a673-114">Tento příklad vytvoří následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="8a673-114">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="8a673-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="8a673-115">See Also</span></span>  
 [<span data-ttu-id="8a673-116">Základní dotazy (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8a673-116">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
