---
title: Jak vypočítat mezilehlé hodnoty (C#)
description: Tento LINQ to XML příklad v jazyce C# ukazuje, jak vypočítat mezilehlé hodnoty, které lze použít při řazení, filtrování a výběr.
ms.date: 07/20/2015
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: fc648f20550de13735a1f6da6b2f811fd0d39004
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103620"
---
# <a name="how-to-calculate-intermediate-values-c"></a><span data-ttu-id="1fb81-103">Jak vypočítat mezilehlé hodnoty (C#)</span><span class="sxs-lookup"><span data-stu-id="1fb81-103">How to calculate intermediate values (C#)</span></span>
<span data-ttu-id="1fb81-104">Tento příklad ukazuje, jak vypočítat mezilehlé hodnoty, které lze použít při řazení, filtrování a výběr.</span><span class="sxs-lookup"><span data-stu-id="1fb81-104">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fb81-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="1fb81-105">Example</span></span>  
 <span data-ttu-id="1fb81-106">V následujícím příkladu je použita `Let` klauzule.</span><span class="sxs-lookup"><span data-stu-id="1fb81-106">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="1fb81-107">Tento příklad používá následující dokument XML: [ukázkový soubor XML: numerická data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1fb81-107">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
IEnumerable<decimal> extensions =  
    from el in root.Elements("Data")  
    let extension = (decimal)el.Element("Quantity") * (decimal)el.Element("Price")  
    where extension >= 25  
    orderby extension  
    select extension;  
foreach (decimal ex in extensions)  
    Console.WriteLine(ex);  
```  
  
 <span data-ttu-id="1fb81-108">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="1fb81-108">This code produces the following output:</span></span>  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="1fb81-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="1fb81-109">Example</span></span>  
 <span data-ttu-id="1fb81-110">Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1fb81-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="1fb81-111">Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1fb81-111">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="1fb81-112">Tento příklad používá následující dokument XML: [ukázkový soubor XML: numerická data v oboru názvů](./sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="1fb81-112">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("DataInNamespace.xml");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<decimal> extensions =  
    from el in root.Elements(ad + "Data")  
    let extension = (decimal)el.Element(ad + "Quantity") * (decimal)el.Element(ad + "Price")  
    where extension >= 25  
    orderby extension  
    select extension;  
foreach (decimal ex in extensions)  
    Console.WriteLine(ex);  
```  
  
 <span data-ttu-id="1fb81-113">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="1fb81-113">This code produces the following output:</span></span>  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
