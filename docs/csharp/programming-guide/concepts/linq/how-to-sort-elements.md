---
title: 'Postupy: Sort – elementyC#()'
ms.date: 07/20/2015
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: 074428413fa57d8f0e5ae94970c2aeeeb9e4cc7c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592452"
---
# <a name="how-to-sort-elements-c"></a><span data-ttu-id="206f5-102">Postupy: Sort – elementyC#()</span><span class="sxs-lookup"><span data-stu-id="206f5-102">How to: Sort Elements (C#)</span></span>
<span data-ttu-id="206f5-103">Tento příklad ukazuje, jak napsat dotaz, který seřadí jeho výsledky.</span><span class="sxs-lookup"><span data-stu-id="206f5-103">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="206f5-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="206f5-104">Example</span></span>  
 <span data-ttu-id="206f5-105">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Číselná data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="206f5-105">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
IEnumerable<decimal> prices =  
    from el in root.Elements("Data")  
    let price = (decimal)el.Element("Price")  
    orderby price  
    select price;  
foreach (decimal el in prices)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="206f5-106">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="206f5-106">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="206f5-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="206f5-107">Example</span></span>  
 <span data-ttu-id="206f5-108">Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="206f5-108">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="206f5-109">Další informace najdete v tématu [obory názvů Overview (LINQ to XMLC#) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="206f5-109">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="206f5-110">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Číselná data v oboru názvů](./sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="206f5-110">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("DataInNamespace.xml");  
XNamespace aw = "http://www.adatum.com";  
IEnumerable<decimal> prices =  
    from el in root.Elements(aw + "Data")  
    let price = (decimal)el.Element(aw + "Price")  
    orderby price  
    select price;  
foreach (decimal el in prices)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="206f5-111">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="206f5-111">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="206f5-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="206f5-112">See also</span></span>

- [<span data-ttu-id="206f5-113">Řazení dat (C#)</span><span class="sxs-lookup"><span data-stu-id="206f5-113">Sorting Data (C#)</span></span>](./sorting-data.md)
