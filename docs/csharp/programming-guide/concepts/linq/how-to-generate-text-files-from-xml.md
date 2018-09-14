---
title: 'Postupy: generování textových souborů z XML (C#)'
ms.date: 07/20/2015
ms.assetid: 9ad283f7-7cac-42ff-bf32-92aa866e6883
ms.openlocfilehash: 1e0c57b1fa16bb1b92cabaf4afa7ff7bf40824bd
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45509403"
---
# <a name="how-to-generate-text-files-from-xml-c"></a><span data-ttu-id="e37c6-102">Postupy: generování textových souborů z XML (C#)</span><span class="sxs-lookup"><span data-stu-id="e37c6-102">How to: Generate Text Files from XML (C#)</span></span>
<span data-ttu-id="e37c6-103">Tento příklad ukazuje, jak vygenerovat soubor hodnot oddělených čárkami (CSV) ze souboru XML.</span><span class="sxs-lookup"><span data-stu-id="e37c6-103">This example shows how to generate a comma-separated values (CSV) file from an XML file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e37c6-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e37c6-104">Example</span></span>  
 <span data-ttu-id="e37c6-105">Verze jazyka C# v tomto příkladu používá syntaxe využívající metody a `Aggregate` operátor vygenerovat soubor CSV z dokumentu XML v jednom výrazu.</span><span class="sxs-lookup"><span data-stu-id="e37c6-105">The C# version of this example uses method syntax and the `Aggregate` operator to generate a CSV file from an XML document in a single expression.</span></span> <span data-ttu-id="e37c6-106">Další informace najdete v tématu [syntaxi dotazů a syntaxe využívající metody v jazyce LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).</span><span class="sxs-lookup"><span data-stu-id="e37c6-106">For more information, see [Query Syntax and Method Syntax in LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
 <span data-ttu-id="e37c6-107">Tento příklad používá následujícího dokumentu XML: [ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="e37c6-107">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XElement custOrd = XElement.Load("CustomersOrders.xml");  
string csv =  
    (from el in custOrd.Element("Customers").Elements("Customer")  
    select  
        String.Format("{0},{1},{2},{3},{4},{5},{6},{7},{8},{9}{10}",  
            (string)el.Attribute("CustomerID"),  
            (string)el.Element("CompanyName"),  
            (string)el.Element("ContactName"),  
            (string)el.Element("ContactTitle"),  
            (string)el.Element("Phone"),  
            (string)el.Element("FullAddress").Element("Address"),  
            (string)el.Element("FullAddress").Element("City"),  
            (string)el.Element("FullAddress").Element("Region"),  
            (string)el.Element("FullAddress").Element("PostalCode"),  
            (string)el.Element("FullAddress").Element("Country"),  
            Environment.NewLine  
        )  
    )  
    .Aggregate(  
        new StringBuilder(),  
        (sb, s) => sb.Append(s),  
        sb => sb.ToString()  
    );  
Console.WriteLine(csv);  
```  
  
 <span data-ttu-id="e37c6-108">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="e37c6-108">This code produces the following output:</span></span>  
  
```  
GREAL,Great Lakes Food Market,Howard Snyder,Marketing Manager,(503) 555-7555,2732 Baker Blvd.,Eugene,OR,97403,USA  
HUNGC,Hungry Coyote Import Store,Yoshi Latimer,Sales Representative,(503) 555-6874,City Center Plaza 516 Main St.,Elgin,OR,97827,USA  
LAZYK,Lazy K Kountry Store,John Steel,Marketing Manager,(509) 555-7969,12 Orchestra Terrace,Walla Walla,WA,99362,USA  
LETSS,Let's Stop N Shop,Jaime Yorres,Owner,(415) 555-5938,87 Polk St. Suite 5,San Francisco,CA,94117,USA  
```  
  
## <a name="see-also"></a><span data-ttu-id="e37c6-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="e37c6-109">See Also</span></span>

- [<span data-ttu-id="e37c6-110">Projekce a transformace (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e37c6-110">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
