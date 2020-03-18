---
title: Jak seřadit prvky (C#)
ms.date: 07/20/2015
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: 7fad9fcb43905072c88a5704c56672917bfc377c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347369"
---
# <a name="how-to-sort-elements-c"></a><span data-ttu-id="55ac2-102">Jak seřadit prvky (C#)</span><span class="sxs-lookup"><span data-stu-id="55ac2-102">How to sort elements (C#)</span></span>
<span data-ttu-id="55ac2-103">Tento příklad ukazuje, jak napsat dotaz, který seřadí jeho výsledky.</span><span class="sxs-lookup"><span data-stu-id="55ac2-103">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55ac2-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="55ac2-104">Example</span></span>  
 <span data-ttu-id="55ac2-105">Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Numerická data (LINQ to XML).](./sample-xml-file-numerical-data-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="55ac2-105">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="55ac2-106">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="55ac2-106">This code produces the following output:</span></span>  
  
```output  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="55ac2-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="55ac2-107">Example</span></span>  
 <span data-ttu-id="55ac2-108">Následující příklad ukazuje stejný dotaz pro jazyk XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="55ac2-108">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="55ac2-109">Další informace naleznete [v tématu Přehled oborů názvů (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="55ac2-109">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="55ac2-110">Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Numerická data v oboru názvů](./sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="55ac2-110">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="55ac2-111">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="55ac2-111">This code produces the following output:</span></span>  
  
```output  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="55ac2-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="55ac2-112">See also</span></span>

- [<span data-ttu-id="55ac2-113">Řazení dat (C#)</span><span class="sxs-lookup"><span data-stu-id="55ac2-113">Sorting Data (C#)</span></span>](./sorting-data.md)
