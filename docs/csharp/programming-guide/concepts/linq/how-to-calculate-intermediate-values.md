---
title: "Postupy: výpočtu pomocných hodnot (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 93aa3683315b88c0ca85abc0eaff3efc8a15452a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-calculate-intermediate-values-c"></a><span data-ttu-id="eea1b-102">Postupy: výpočtu pomocných hodnot (C#)</span><span class="sxs-lookup"><span data-stu-id="eea1b-102">How to: Calculate Intermediate Values (C#)</span></span>
<span data-ttu-id="eea1b-103">Tento příklad ukazuje způsob výpočtu pomocných hodnot, které mohou být používány třídění, filtrování a výběr.</span><span class="sxs-lookup"><span data-stu-id="eea1b-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eea1b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="eea1b-104">Example</span></span>  
 <span data-ttu-id="eea1b-105">Následující příklad používá `Let` klauzule.</span><span class="sxs-lookup"><span data-stu-id="eea1b-105">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="eea1b-106">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: Číselná Data (technologie LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="eea1b-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="eea1b-107">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="eea1b-107">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="eea1b-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="eea1b-108">Example</span></span>  
 <span data-ttu-id="eea1b-109">Následující příklad ukazuje stejný dotaz pro formát XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="eea1b-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="eea1b-110">Další informace najdete v tématu [práci s obory názvů XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="eea1b-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="eea1b-111">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: Číselná Data v Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="eea1b-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="eea1b-112">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="eea1b-112">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="see-also"></a><span data-ttu-id="eea1b-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="eea1b-113">See Also</span></span>  
 [<span data-ttu-id="eea1b-114">Základní dotazy (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="eea1b-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
