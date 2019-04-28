---
title: 'Postupy: Výpočet mezilehlých hodnot (C#)'
ms.date: 07/20/2015
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: 12c8a87114859ce7b47b8206acb454cdc2838470
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61702396"
---
# <a name="how-to-calculate-intermediate-values-c"></a><span data-ttu-id="e1428-102">Postupy: Výpočet mezilehlých hodnot (C#)</span><span class="sxs-lookup"><span data-stu-id="e1428-102">How to: Calculate Intermediate Values (C#)</span></span>
<span data-ttu-id="e1428-103">Tento příklad ukazuje způsob výpočtu pomocných hodnot použitých v řazení, filtrování a vyberete.</span><span class="sxs-lookup"><span data-stu-id="e1428-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1428-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e1428-104">Example</span></span>  
 <span data-ttu-id="e1428-105">V následujícím příkladu `Let` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="e1428-105">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="e1428-106">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Číselná Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e1428-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="e1428-107">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="e1428-107">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="e1428-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="e1428-108">Example</span></span>  
 <span data-ttu-id="e1428-109">Následující příklad ukazuje stejný dotaz pro soubor XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e1428-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="e1428-110">Další informace najdete v tématu [práce s názvovými prostory XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="e1428-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="e1428-111">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Číselná Data ve Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="e1428-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="e1428-112">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="e1428-112">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="see-also"></a><span data-ttu-id="e1428-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e1428-113">See also</span></span>

- [<span data-ttu-id="e1428-114">Základní dotazy (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e1428-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
