---
title: "Postupy: řazení elementů (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2a9fba878a5f760996566a566cee94a2ca16dcee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-sort-elements-c"></a><span data-ttu-id="20b4b-102">Postupy: řazení elementů (C#)</span><span class="sxs-lookup"><span data-stu-id="20b4b-102">How to: Sort Elements (C#)</span></span>
<span data-ttu-id="20b4b-103">Tento příklad ukazuje, jak napsat dotaz, který seřadí své výsledky.</span><span class="sxs-lookup"><span data-stu-id="20b4b-103">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20b4b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="20b4b-104">Example</span></span>  
 <span data-ttu-id="20b4b-105">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: Číselná Data (technologie LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="20b4b-105">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="20b4b-106">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="20b4b-106">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="20b4b-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="20b4b-107">Example</span></span>  
 <span data-ttu-id="20b4b-108">Následující příklad ukazuje stejný dotaz pro formát XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="20b4b-108">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="20b4b-109">Další informace najdete v tématu [práci s obory názvů XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="20b4b-109">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="20b4b-110">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: Číselná Data v Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="20b4b-110">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="20b4b-111">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="20b4b-111">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="20b4b-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="20b4b-112">See Also</span></span>  
 [<span data-ttu-id="20b4b-113">Řazení dat (C#)</span><span class="sxs-lookup"><span data-stu-id="20b4b-113">Sorting Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/sorting-data.md)  
 [<span data-ttu-id="20b4b-114">Základní dotazy (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="20b4b-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
