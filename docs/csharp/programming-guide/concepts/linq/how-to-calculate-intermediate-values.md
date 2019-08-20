---
title: 'Postupy: Vypočítat mezilehlé hodnoty (C#)'
ms.date: 07/20/2015
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: 7b2dfc4e26fc7648cbd93b1e590079e4b105ad43
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594132"
---
# <a name="how-to-calculate-intermediate-values-c"></a><span data-ttu-id="3b38f-102">Postupy: Vypočítat mezilehlé hodnoty (C#)</span><span class="sxs-lookup"><span data-stu-id="3b38f-102">How to: Calculate Intermediate Values (C#)</span></span>
<span data-ttu-id="3b38f-103">Tento příklad ukazuje, jak vypočítat mezilehlé hodnoty, které lze použít při řazení, filtrování a výběr.</span><span class="sxs-lookup"><span data-stu-id="3b38f-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b38f-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="3b38f-104">Example</span></span>  
 <span data-ttu-id="3b38f-105">V následujícím příkladu je použita `Let` klauzule.</span><span class="sxs-lookup"><span data-stu-id="3b38f-105">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="3b38f-106">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Číselná data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3b38f-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="3b38f-107">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3b38f-107">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="3b38f-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="3b38f-108">Example</span></span>  
 <span data-ttu-id="3b38f-109">Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3b38f-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="3b38f-110">Další informace najdete v tématu [obory názvů Overview (LINQ to XMLC#) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3b38f-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="3b38f-111">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Číselná data v oboru názvů](./sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="3b38f-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="3b38f-112">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3b38f-112">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
